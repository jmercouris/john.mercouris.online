SSH Server Access: No External Dependencies
###########################################
:date: 2016-11-19 14:16
:author: jmercouris
:category: Software
:slug: ssh-server-access-no-external-dependencies
:status: published
:description: Access your home server without depending on DynDNS and
              others.

The Problem
===========

You have a Server, or a computer at home that you want to access,
whether via SSH or otherwise. You type in the IP Address of your house's
network, the port you want to access, and everything works great for a
couple of weeks. But what's that you say? You reset your modem? There
was a power outage in your area? Any number of things can lead to a
change in your IP which was 'static' for months at a time!

The Solution
============

There are a number of ways to deal with this. We could simply sign up
for a service at DynDNS (http://dyn.com/dns/). The issue with this is
that it usually costs money beyond some basic features, is limited in
some artificial way, and introduces an external dependency into your
system.

Instead, we'll build our own simple version of DynDNS. This could
manifest itself in a number of ways, but because I have a webserver that
I already host my blog on, I figured I could utilize it to keep track of
my computer's ip.

High Level Architecture
=======================

Here's how the system works:

#. Script on home server pings webserver daily.
#. PHP script on webserver saves/updates IP address from home server.
#. To get IP, your own machine asks webserver for home server IP.

WebServer Side Component
========================

.. code-block:: php

    $ipfile = "server.txt"; // File for encrypted IP Persistence
    $key = 'super_secret_key'; // Key for IP encryption

    if($_GET['accessor'] == 'secret_password') {
     $string = $_SERVER['REMOTE_ADDR'];

     // Encrypt the IP Address  
     $encrypted = base64_encode(mcrypt_encrypt(MCRYPT_RIJNDAEL_256,
       md5($key), $string, MCRYPT_MODE_CBC, md5(md5($key))));

     // Persist The Encrypted Key to Disk
     $fh = @fopen($ipfile, 'w');
     fwrite($fh, $encrypted);
     fclose($fh);
    }
    // Check to see that the request for the IP has the correct Password
    else if ($_GET['request'] == 'secret_password') {
     // Open the File and Decrypt the IP Address
     $string = file_get_contents($ipfile, true);
     $decrypted = rtrim(mcrypt_decrypt(MCRYPT_RIJNDAEL_256, md5($key),
       base64_decode($string), MCRYPT_MODE_CBC, md5(md5($key))), "\0");

     // Return the IP Address
     echo $decrypted;
    }
    else {
     header("HTTP/1.0 404 Not Found");
    }

The Home Server Perspective
---------------------------

This script works in a very simple way, if we call the script by GET'ing
the URL www.website.com/webscript.php?accessor=secret\_password, the
script will take our IP Address, encrypt it with our $key and then save
it to a file at location $ipfile. This is how our home server will
update its' IP with the webserver, by calling this script in this way.

The User Perspective
--------------------

When it is time to ask our webserver for the IP, we GET the same script,
but with different parameters, this time like this:
www.website.com/webscript.php?request=secret\_password. The script will
then compare the string we pass in the for the password with what is
saved in the script on the webserver, if they match, it will decrypt the
$ipfile and echo the IP address back to us.

Home Server Component
=====================

As alluded to above, the Home Server needs to call the webserver script
occassionally to make sure it has the latest IP address. To do this
we'll set up a cronjob at whatever frequency we wish. I have my cronjob
set to update the IP of my Home Server about once a day. The script here
is far simpler:

.. code-block:: bash

    #!/bin/bash
    curl http://www.website.com/server.php?accessor=secret_password

What this script simply does is execute a 'GET' onto the webserver
script with the 'secret\_password' so that the webserver can record the
home server's IP address.

User Computer Component
=======================

On the side of the user, we want to fetch the IP address whenever we are
not able to connect to our machine, because likely this means that our
IP address has changed. To do this, we have a bash script that we place
in our path:

.. code-block:: bash

    #!/bin/bash
    ssh_name=`curl -s http://www.website.com.com/server.php?request=secret_password`

    echo "Host server" > ~/.ssh/config
    echo " HostName ${ssh_name}" >> ~/.ssh/config
    echo " Port 22" >> ~/.ssh/config

To use this script, we'd simply call 'script' from our command line
(assuming the script is in our path). Then, we could simply type in 'ssh
server' and all of our details would be automatically filled out!

Future Improvements
===================

In the future such a system could use git with private/public key
encryption. The kind of system presented works great if you have a
webserver, but even hosting a webserver costs money. If you want an
agnostic future proof system, consider one that uses git, mercurial, or
any other type of version control system.

Imagine that you could have a cron script on your home server that uses
your public key to encrypt its' ip address and then commits it to a
repository online (public, private github, etc).

Then, on your own machine, to retrieve the IP address of your home
server, you write a script that clones/pulls the latest changes from the
repository, decrypts the message using your private key, and then
updates your ssh config file as before.
