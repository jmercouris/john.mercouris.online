Emacs Column Width
########################################################################
:date: 2017-05-06 15:54
:author: jmercouris
:category: Software
:slug: emacs-column-width
:status: published

What is the problem?
========================================================================
Emacs does not come with a built in function to set the column width
for a given window. Normally, one might think, this is not really a
huge problem, when you split windows with emacs, they'll split equally
and then you can resize any child windows as necessary.

What is the Solution?
========================================================================
How can we do this quicker and automate it? How can we set the width
of a window to a number of columns instantaneously?

.. code-block:: elisp

    (defun set-window-width (n)
      "Set the selected window's width to N columns wide."
      (if (> n (window-width))
	  (enlarge-window-horizontally (- n (window-width)))
	  (shrink-window-horizontally (- (window-width) n))))
	
This function allows us to set the width of a window to an absolute
value. As a side effect, all other windows may become larger or
smaller. To demonstrate, let's consider the following scenario:

.. image:: {filename}/images/emacs_window_state_0.png
   :alt: Equal width windows
   :class: pure-img

If we try to make window A equal to N columns, where N is a number
greater than the current columns wide that window A is, then window A
will grow bigger, and window B will grow smaller.

.. image:: {filename}/images/emacs_window_state_1.png
   :alt: Window A grew to 80 columns in width, shrinking window B.
   :class: pure-img

The opposite is also true, if we were to now set window A to equal
40 columns in width, it would shrink, and window B would grow.

If you frequently find yourself opening up buffers that work best
at certain widths (circe, man, etc), then you can make handy
functions that automatically scale a window to a specific width.

.. code-block:: elisp

    (defun set-80-columns ()
      "Set the selected window to 80 columns."
      (interactive)
      (set-window-width 80))

For example, the above function automatically sets the width of a
window to 80 columns.

I hope you enjoyed reading this post, and that it was useful to you!
