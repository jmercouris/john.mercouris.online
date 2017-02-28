Extract Embedded PDFs/Files from Word Documents
###############################################
:date: 2014-10-22 16:24
:author: jmercouris
:category: Software
:tags: embedded pdf, extract pdf, microsoft office
:slug: extract-embedded-pdfsfiles-from-word-documents
:status: published

In Microsoft Word for Windows, you have the capability to embed
PDF-files / other files. On every other platform, including OS X (which
even has Microsoft Office), it is not possible to extract or view these
embedded files (Libre Office/Open Office do not work).

In order to get to these files I came up with a workaround that works on
OS X (and possibly on Linux with a good decompression utility).

Get a good archive tool. I recommend \ **The Unarchiver** for OS X,
and \ **7zip** for any other platform.

.. raw:: html

   <div>

Install \ **The Unarchiver**

.. raw:: html

   </div>

.. raw:: html

   <div>

http://wakaba.c3.cx/s/apps/unarchiver

.. raw:: html

   </div>

.. raw:: html

   <div>

.. raw:: html

   </div>

.. raw:: html

   <div>

Extract the archive by opening the file with \ **The Unarchiver**

.. raw:: html

   </div>

.. raw:: html

   <div>

.. raw:: html

   </div>

.. raw:: html

   <div>

|Screen Shot 2014-10-22 at 18.27.20|

.. raw:: html

   </div>

.. raw:: html

   <div>

Select \ **The Unarchiver** from the list

.. raw:: html

   </div>

.. raw:: html

   <div>

|Screen Shot 2014-10-22 at 18.27.39|

.. raw:: html

   </div>

.. raw:: html

   <div>

.. raw:: html

   </div>

.. raw:: html

   <div>

After extracting the file, you should have a folder with the same name
as your doc, this folder contains the contents of your document.

.. raw:: html

   </div>

.. raw:: html

   <div>

|Screen Shot 2014-10-22 at 18.27.53|

.. raw:: html

   </div>

.. raw:: html

   <div>

If you enter this folder you'll see a number of sub-folders, the one we
are interested is called ObjectPool, this contains all embedded objects.

.. raw:: html

   </div>

.. raw:: html

   <div>

|Screen Shot 2014-10-22 at 18.28.10|

.. raw:: html

   </div>

.. raw:: html

   <div>

Within ObjectPool, each embedded object is represented by a folder.

.. raw:: html

   </div>

.. raw:: html

   <div>

|Screen Shot 2014-10-22 at 18.28.12|

.. raw:: html

   </div>

.. raw:: html

   <div>

Within each embedded object's folder, we can find the actual object in
question, in this example a PDF. The object will be named CONTENTS.

.. raw:: html

   </div>

.. raw:: html

   <div>

|Screen Shot 2014-10-22 at 18.28.14|

.. raw:: html

   </div>

.. raw:: html

   <div>

Simply copy and rename CONTENTS to whatever file extension/file you are
expecting, in this case we know we are looking for a PDF in our doc. So
we will rename CONTENTS to CONTENTS.pdf.

.. raw:: html

   </div>

.. raw:: html

   <div>

|Screen Shot 2014-10-22 at 18.28.23|

.. raw:: html

   </div>

.. raw:: html

   <div>

We should now be able to view our pdf! That's it! The above process
applies to any type of embedded object within a word document.

.. raw:: html

   </div>

.. raw:: html

   <div>

.. raw:: html

   </div>

.. raw:: html

   <div>

As a note of caution, if when you unzip the doc you do not see the list
of files, and instead see:

.. raw:: html

   </div>

.. raw:: html

   <div>

|Screen Shot 2014-10-22 at 18.36.03|

.. raw:: html

   </div>

.. raw:: html

   <div>

then your unzip tool has failed to unzip the padded files at the
beginning of the zip file which are not contained in the zip index. This
cannot be fixed by the standard command line zip tool. Try another tool.

.. raw:: html

   </div>

.. raw:: html

   <div>

.. raw:: html

   </div>

.. raw:: html

   <div>

Best of luck!

.. raw:: html

   </div>

.. raw:: html

   <div>

.. raw:: html

   </div>

.. raw:: html

   <div>

.. raw:: html

   </div>

.. |Screen Shot 2014-10-22 at 18.27.20| image:: http://jmercouris.com/wp-content/uploads/2014/10/Screen-Shot-2014-10-22-at-18.27.20-1024x866.png
   :class: alignnone size-large wp-image-130
   :width: 474px
   :height: 400px
   :target: http://jmercouris.com/wp-content/uploads/2014/10/Screen-Shot-2014-10-22-at-18.27.20.png
.. |Screen Shot 2014-10-22 at 18.27.39| image:: http://jmercouris.com/wp-content/uploads/2014/10/Screen-Shot-2014-10-22-at-18.27.39-1024x716.png
   :class: alignnone size-large wp-image-138
   :width: 474px
   :height: 331px
   :target: http://jmercouris.com/wp-content/uploads/2014/10/Screen-Shot-2014-10-22-at-18.27.39.png
.. |Screen Shot 2014-10-22 at 18.27.53| image:: http://jmercouris.com/wp-content/uploads/2014/10/Screen-Shot-2014-10-22-at-18.27.53-965x1024.png
   :class: alignnone size-large wp-image-131
   :width: 474px
   :height: 502px
   :target: http://jmercouris.com/wp-content/uploads/2014/10/Screen-Shot-2014-10-22-at-18.27.53.png
.. |Screen Shot 2014-10-22 at 18.28.10| image:: http://jmercouris.com/wp-content/uploads/2014/10/Screen-Shot-2014-10-22-at-18.28.10-965x1024.png
   :class: alignnone size-large wp-image-132
   :width: 474px
   :height: 502px
   :target: http://jmercouris.com/wp-content/uploads/2014/10/Screen-Shot-2014-10-22-at-18.28.10.png
.. |Screen Shot 2014-10-22 at 18.28.12| image:: http://jmercouris.com/wp-content/uploads/2014/10/Screen-Shot-2014-10-22-at-18.28.12-965x1024.png
   :class: alignnone size-large wp-image-133
   :width: 474px
   :height: 502px
   :target: http://jmercouris.com/wp-content/uploads/2014/10/Screen-Shot-2014-10-22-at-18.28.12.png
.. |Screen Shot 2014-10-22 at 18.28.14| image:: http://jmercouris.com/wp-content/uploads/2014/10/Screen-Shot-2014-10-22-at-18.28.14-965x1024.png
   :class: alignnone size-large wp-image-134
   :width: 474px
   :height: 502px
   :target: http://jmercouris.com/wp-content/uploads/2014/10/Screen-Shot-2014-10-22-at-18.28.14.png
.. |Screen Shot 2014-10-22 at 18.28.23| image:: http://jmercouris.com/wp-content/uploads/2014/10/Screen-Shot-2014-10-22-at-18.28.23-965x1024.png
   :class: alignnone size-large wp-image-135
   :width: 474px
   :height: 502px
   :target: http://jmercouris.com/wp-content/uploads/2014/10/Screen-Shot-2014-10-22-at-18.28.23.png
.. |Screen Shot 2014-10-22 at 18.36.03| image:: http://jmercouris.com/wp-content/uploads/2014/10/Screen-Shot-2014-10-22-at-18.36.03-1024x981.png
   :class: alignnone size-large wp-image-136
   :width: 474px
   :height: 454px
   :target: http://jmercouris.com/wp-content/uploads/2014/10/Screen-Shot-2014-10-22-at-18.36.03.png
