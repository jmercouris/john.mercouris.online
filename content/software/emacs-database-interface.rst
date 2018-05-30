Emacs Database Interface (EDBI)
###############################
:date: 2018-05-27 22:17
:author: jmercouris
:category: Software
:slug: emacs-database-interface
:status: published
:description: How to install and use EDBI, the abstract Emacs database
              interface.

What is it?
========================================================================

Emacs database interface (EDBI) is a useful tool for connecting to any
number of databases with an abstract interface. Much like the abstract
version control system in Emacs
(https://www.gnu.org/software/emacs/manual/html_node/emacs/Version-Control.html),
EDBI can help simplify and make consistent multiple databases.


Why should I care?
========================================================================
EDBI is useful for reducing the mental load of managing and connecting
with several different types of databases.

How do I install it?
========================================================================
If you haven't already, install Melpa within Emacs. You can find out
more here: http://melpa.milkbox.net/#/getting-started.

After installing Melpa, simply :code:`M-x package-install RET edbi
RET`.  In order to use EDBI, you'll need to install some Perl packages
from CPAN. CPAN is the "Comprehensive Perl Archive Network" and
provides a way to install Perl modules.

EDBI depends on a Perl interface that abstracts databases in order to
abstract them within Emacs. You can read more about the abstraction
here: https://metacpan.org/pod/DBI#connect. In reading about it,
you'll also find information about how to structure your database
information in the EDBI prompt.

To begin with, the modules you'll want to probably install are the
following:

.. code-block:: bash

      RPC::EPC::Service
      DBI
      DBD::SQLite
      DBD::Pg
      DBD::mysql

You can install each module like this :code:`cpan install DBD::SQLite`
which would install SQLite support for EDBI.

A Practical Example: SQLITE
========================================================================
To use EDBI, you can simply :code:`M-x edbi:open-db-viewer RET` which
will bring you to the following window:

|open-db-window|

You could enter your information here, but it might be simpler to install
the package for SQLite that makes EDBI a little bit simpler to use.

To do this, once again, :code:`M-x package-install edbi-sqlite RET`. After
you'll be able to execute :code:`M-x edbi-sqlite RET` and be prompted
to open a SQLite database 

|sqlite-open|

After opening the database you'll be presented with a screen like this:

|edbi-database-view|

This screen contains all of the tables within your database. To begin
exploring the commands available to you, you can type :code:`?`. Doing
so will bring up the following prompt:

|edbi-help|

Following one of the presented options, typing :code:`RET` will allow
you to drill down and look at the data in one of your tables. An example
can be seen below:

|edbi-query|

As you can see, it is just a query. You can edit the query, and
resubmit it using :code:`C-c C-c`. This will allow you to inspect,
modify, and traverse the data in more complex ways.

Thank you for reading, I hope you enjoyed!

.. |open-db-window| image:: {filename}/images/edbi-dialog-open.png
   :class: pure-img

.. |sqlite-open| image:: {filename}/images/sqlite-open.png
   :class: pure-img

.. |edbi-database-view| image:: {filename}/images/edbi-database-view.png
   :class: pure-img

.. |edbi-help| image:: {filename}/images/edbi-help.png
   :class: pure-img

.. |edbi-query| image:: {filename}/images/edbi-query.png
   :class: pure-img

