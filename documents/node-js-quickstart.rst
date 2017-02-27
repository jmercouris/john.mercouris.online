Node js Quickstart
##################
:date: 2014-05-16 03:10
:author: jmercouris
:category: Software
:tags: featured
:slug: node-js-quickstart
:status: published

This tutorial will cover installing node js, using node js, and writing
your first program. This tutorial is not intended to teach node js
programming.

The Final Product & Premise
~~~~~~~~~~~~~~~~~~~~~~~~~~~

I had the idea recently of music and rhymes. What if we could take a
song, and substitute key words of the song with other words that rhyme
which would change the meaning of the song entirely. For example,
changing the sentence "I can't believe this dish", to "I can't believe
this fish" has changed the entire meaning of the sentence.

 

    Since songs often rely on rhyme and symbolism, locating nouns and
    changing them within a sentence would probably lead to funny song
    outcomes.

--------------

 

Tutorial Requirements
~~~~~~~~~~~~~~~~~~~~~

\*Nix system (Linux, Solaris, OSX etc)

Installation
~~~~~~~~~~~~

-  Download an official version of node js from the following
   url:\ http://nodejs.org/dist/
-  Unzip node JS
-  Go into your unzipped node js directory and enter the command

   ::

       ./configure

   followed by

   ::

       sudo make install

::

    You may require the installation of build tools (compilers) 
    Ubuntu: apt-get install build-essential
    OSX: Install XCode via the app store, then in a terminal run xcode-select --install

 Installation Test!
~~~~~~~~~~~~~~~~~~~

Did your installation work?

::

    node
    >console.log("hello test")
    lolundefined

 Ready to Code
~~~~~~~~~~~~~~

You are now officially ready to begin your node.js journey. Before we
begin creating our magical rhyming program we will need to get some
programs that other people have made that do the rhyming for us. To do
this we will use a cool package manager called npm.

Install NPM
~~~~~~~~~~~

No need! NPM comes with node js, but if somehow you managed to get it
without then simply:

::

    curl http://npmjs.org/install.sh | sh

You might also want to make sure that if you have installed NPM via node
js you have the last version, to do so run:

::

    sudo npm install npm -g

Using NPM
~~~~~~~~~

Using NPM is super easy; simple npm install \ *packagename*.
Where \ *packagename* is the name of the package you want to install.

Let's Actually Begin Coding:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Now that we have npm. Let's go ahead and begin by installing our only
and most useful package that we will be using. In this case it is called
simply \ *rhyme. *\ This can be achieved with:

::

    npm install rhyme

Now that we have our base requirements for the project. Let's go ahead
and do some coding. I'm not going to attempt to teach you node.js, there
are plenty of good resources for that, this is meant to be as a primer
for setting up your environment and running through a build.

Next make a new file on disk. Call it rhyme.js, or whatever you wish.
Copy and paste the following contents into the program;

::

    var rhyme = require('rhyme');

    var fs = require('fs'),
     readline = require('readline');

    var rd = readline.createInterface({
     input: fs.createReadStream('source.txt'),
     output: process.stdout,
     terminal: false
    });

    rd.on('line', function(line) {
     var splitLine = line.split(' ');

     rhyme(function (r) {
     splitLine[0] = r.rhyme(splitLine[0])[10];
     console.log(splitLine);
     }); 
    });

As soon as you're done, run

::

    node myprogram.js

The program will then read a song line by line (from a file, in this
case source.txt) and rhyme the words with other words. Because the
rhyming uses a lookup server, use only small files with four lines or
less. Good luck!

Get the Code:
~~~~~~~~~~~~~

https://bitbucket.org/jmercouris/node-rhyme/overview

Credit:
~~~~~~~

http://nodeguide.com/beginner.html

https://www.npmjs.org

https://github.com/substack/node-rhyme

 
