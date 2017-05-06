Emacs Centered-Point
####################
:date: 2016-04-11 22:01
:author: jmercouris
:category: Software
:slug: emacs-centered-point
:status: published

What is it?
===========

Emacs centered-point mode is a mode that centers the point within an
Emacs buffer. This gives you good visual context when you are scrolling
to avoid jarring bumps as you work on a piece of code.

Where can I get it?
===================

The code is available on github
at: https://github.com/jmercouris/emacs-centered-point

What about emacs-centered-cursor mode?
======================================

I've been using the emacs-centered-cursor mode for a long time, and
while I am really satisfied with it, it bothered me how much CPU time it
seemed to take. In response I developed a plugin that was substantially
shorter and used only one line of Elisp code.

What does the code look like?
=============================

.. code-block:: elisp

    (define-minor-mode centered-point-mode
      "Alaways center the cursor in the middle of the screen."
      :lighter "..."
      (cond (centered-point-mode (add-hook 'post-command-hook 'line-change))
        (t (remove-hook 'post-command-hook 'line-change)))
      )

    (defun line-change ()
      (recenter)
      )

What was the journey like?
==========================

Along the way I had a lot of great resources that helped me. I strongly
recommend the following resources to anyone looking to extend their
editor:

-  Official Elisp
   Tutorial: https://www.gnu.org/software/emacs/manual/html\_node/eintr/
-  Quick Elisp Intro
   Tutorial: http://ergoemacs.org/emacs/elisp\_basics.html
-  Common Elisp
   functions: http://ergoemacs.org/emacs/elisp\_common\_functions.html
-  How to write an Emacs
   minor-mode: http://nullprogram.com/blog/2013/02/06/

The path that I recommend is going through the quick Xah Elisp tutorial,
then going through the Emacs minor-mode tutorial, then referencing the
Elisp resources until you can finally shape what you need. Looking at my
code should even be enough of a simple example to build off and get
started. Good luck! Thanks for reading, I hope you enjoyed it!
