Emacs Latex-Preview-Pane on OSX
###############################
:date: 2016-07-11 10:00
:author: jmercouris
:category: Software
:slug: emacs-latex-preview-pane-on-osx
:status: published

Working with Emacs and Latex
============================

Latex-preview-pane is a handy Emacs package that allows you to preview
the work you are doing in Latex in a buffer (usually to the right) of
your Latex document. It looks like this:


.. figure:: {filename}/images/Screen-Shot-2016-07-11-at-11.49.31.png
    :class: pure-img

    Latex raw text on the left, pdf output on the right.


To use this functionality you need ghostscript, what ghostscript does
for you is converts your Latex file to something renderable by Emac's
built in doc-view-mode.


::

    sudo port install ghostscript

or

::

    brew install ghostscript

Then, from within Emacs, simply M-x, package-install, latex-preview-pane.
Then when you're ready to go, run M-x, latex-preview-pane-mode in
whichever buffer you'd like a preview of.

Possible Issues
---------------

If you find that your Latex file renders initially in the preview pane,
but does not render on refresh, this signifies an issue with your Latex
file, you should fix any compilation errors or warnings and try again.
If you still persist on refresh, try latex-preview-pane-mode with the
simplest Latex file you can to verify your system's operation.

Additional Recommendations
--------------------------

I also highly suggest that you install the AUCTeX package for Emacs.
This does all sorts of useful things for Emacs, like syntax
highlighting, and it even comes with it's own built-in preview mode that
will show you how a function or an operation will render, right in the
buffer (without opening a separate pane).


Thanks for reading!
