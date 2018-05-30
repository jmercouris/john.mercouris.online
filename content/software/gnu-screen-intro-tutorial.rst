GNU Screen! Intro & Tutorial
############################
:date: 2014-06-24 02:58
:author: jmercouris
:category: Software
:tags: Bash, featured, GNU, GNU Screen, Linux, Terminal, Unix
:slug: gnu-screen-intro-tutorial
:status: published

GNU Screen is a program that allows you to have virtual terminal spaces
or desktops. Imagine that GNU Screen is a terminal version of OSX
Spaces.

The blurb on the GNU Screen home page is accurate, but difficult to
understand:

    Screen is a full-screen window manager that multiplexes a physical
    terminal between several processes, typically interactive shells.
    Each virtual terminal provides the functions of the DEC VT100
    terminal and, in addition, several control functions from the ANSI
    X3.64 (ISO 6429) and ISO 2022 standards (e.g., insert/delete line
    and support for multiple character sets). There is a scrollback
    history buffer for each virtual terminal and a copy-and-paste
    mechanism that allows the user to move text regions between windows.

Let's demystify what GNU Screen is, and how you would use it by running
through a potential use case (there are many, many more)

#. You need to run several programs simultaneously
#. These programs cannot be sent to the background
#. You have to switch between these programs to interact with them
   within one terminal session (e.g. ssh session)

So what would you do? You can use GNU Screen! More likely than not, GNU
Screen ships with your \*Nix Machine. To test if it is already installed
simply type:

.. code-block:: bash

    screen

If you are presented with a message as such:

|Screen Shot 2014-06-23 at 9.33.22 PM|

then, you have GNU Screen installed, congratulations, if not you can
find it at:

.. code-block:: bash

    http://ftp.gnu.org/gnu/screen/

Or, on Ubuntu you can install it with:

.. code-block:: bash

    sudo apt-get install screen

Now, here's how you use it! Think of Screens as virtual desktops or OSX
spaces.

The first command we'll learn is how to make a new \ *named* screen.

.. code-block:: bash

    screen -S screenname

Will produce a new screen with a particular *screenname*, let's go ahead
and do it. Immediately we'll be presented with a new blank terminal. Or
in this case, a new virtual terminal \ *screen*.

|Screen Shot 2014-06-23 at 9.37.12 PM|

If we run:

.. code-block:: bash

    screen -ls

We'll be presented with a list of running \ *screens,* which should
include our new running screen, in my case \ *testScreenEmacs*.

|Screen Shot 2014-06-23 at 9.38.06 PM|

Now, if we want to "detach" from our screen session, that is, change our
virtual display, akin to changing "spaces" on OSX, we will type the
following key combination:

.. code-block:: bash

    ctrl + a

we'll then release all keys on the keyboard and press:

.. code-block:: bash

    d

This will "detach" our running session, let's go ahead and do that.
 After detaching, entering the command:

.. code-block:: bash

    screen -ls

will show us the new state of our terminal:

|Screen Shot 2014-06-23 at 9.40.17 PM|

We are now detached from our previous session, and are attached to the
standard terminal. To go back into our virtual \ *screen*, we type:

.. code-block:: bash

    screen -r testScreenEmacs

Finally, let us kill our test screen environment. The recommended way to
do so is to enter the \ *screen* using

.. code-block:: bash

    screen -r screenname

then entering the following key combination:

.. code-block:: bash

    ctrl + a

we'll then release all keys on the keyboard and type:

.. code-block:: bash

    :quit

followed by the return key (enter).

 

In short, GNU Screen is a powerful tool for maintaining multiple
"virtual" screens. Here's an aggregate quick reference:

.. code-block:: bash

      screen -ls   list screen sessions
      screen -S name create screen called name
      screen -r name connects to the screen name

Here is a reference of commands to use within Gnu Screen itself: Much
like the Emacs commands :code:`C-n` and :code:`C-p`, Gnu Screen
followers similar mnemonics.

.. code-block:: bash

     Ctrl+A N -> go to the next screen
     Ctrl+A P -> go to the previous screen
     Ctrl+A C -> Create new screen
     Ctrl+A D -> Detach screen

You can always find more on the help screen :code:`C-a ?`. Best of
luck!

.. |Screen Shot 2014-06-23 at 9.33.22 PM| image:: {filename}/images/Screen-Shot-2014-06-23-at-9.33.22-PM.png
   :class: pure-img
.. |Screen Shot 2014-06-23 at 9.37.12 PM| image:: {filename}/images/Screen-Shot-2014-06-23-at-9.37.12-PM.png
   :class: pure-img
.. |Screen Shot 2014-06-23 at 9.38.06 PM| image:: {filename}/images/Screen-Shot-2014-06-23-at-9.38.06-PM.png
   :class: pure-img
.. |Screen Shot 2014-06-23 at 9.40.17 PM| image:: {filename}/images/Screen-Shot-2014-06-23-at-9.40.17-PM.png
   :class: pure-img
