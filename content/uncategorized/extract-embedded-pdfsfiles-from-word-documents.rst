Extract Embedded PDFs/Files from Word Documents
###############################################
:date: 2014-10-22 16:24
:author: jmercouris
:category: Uncategorized
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

Install \ **The Unarchiver**

http://wakaba.c3.cx/s/apps/unarchiver

Extract the archive by opening the file with \ **The Unarchiver**

|Screen Shot 2014-10-22 at 18.27.20|

Select \ **The Unarchiver** from the list

|Screen Shot 2014-10-22 at 18.27.39|

After extracting the file, you should have a folder with the same name
as your doc, this folder contains the contents of your document.

|Screen Shot 2014-10-22 at 18.27.53|

If you enter this folder you'll see a number of sub-folders, the one we
are interested is called ObjectPool, this contains all embedded objects.

|Screen Shot 2014-10-22 at 18.28.10|

Within ObjectPool, each embedded object is represented by a folder.

|Screen Shot 2014-10-22 at 18.28.12|

Within each embedded object's folder, we can find the actual object in
question, in this example a PDF. The object will be named CONTENTS.

|Screen Shot 2014-10-22 at 18.28.14|

Simply copy and rename CONTENTS to whatever file extension/file you are
expecting, in this case we know we are looking for a PDF in our doc. So
we will rename CONTENTS to CONTENTS.pdf.

|Screen Shot 2014-10-22 at 18.28.23|

We should now be able to view our pdf! That's it! The above process
applies to any type of embedded object within a word document.

As a note of caution, if when you unzip the doc you do not see the list
of files, and instead see:

|Screen Shot 2014-10-22 at 18.36.03|

then your unzip tool has failed to unzip the padded files at the
beginning of the zip file which are not contained in the zip index. This
cannot be fixed by the standard command line zip tool. Try another tool.

Best of luck!

.. |Screen Shot 2014-10-22 at 18.27.20| image:: {filename}/images/Screen-Shot-2014-10-22-at-18.27.20.png
   :class: pure-img
   :target: {filename}/images/Screen-Shot-2014-10-22-at-18.27.20.png
.. |Screen Shot 2014-10-22 at 18.27.39| image:: {filename}/images/Screen-Shot-2014-10-22-at-18.27.39.png
   :class: pure-img
   :target: {filename}/images/Screen-Shot-2014-10-22-at-18.27.39.png
.. |Screen Shot 2014-10-22 at 18.27.53| image:: {filename}/images/Screen-Shot-2014-10-22-at-18.27.53.png
   :class: pure-img
   :target: {filename}/images/Screen-Shot-2014-10-22-at-18.27.53.png
.. |Screen Shot 2014-10-22 at 18.28.10| image:: {filename}/images/Screen-Shot-2014-10-22-at-18.28.10.png
   :class: pure-img
   :target: {filename}/images/Screen-Shot-2014-10-22-at-18.28.10.png
.. |Screen Shot 2014-10-22 at 18.28.12| image:: {filename}/images/Screen-Shot-2014-10-22-at-18.28.12.png
   :class: pure-img
   :target: {filename}/images/Screen-Shot-2014-10-22-at-18.28.12.png
.. |Screen Shot 2014-10-22 at 18.28.14| image:: {filename}/images/Screen-Shot-2014-10-22-at-18.28.14.png
   :class: pure-img
   :target: {filename}/images/Screen-Shot-2014-10-22-at-18.28.14.png
.. |Screen Shot 2014-10-22 at 18.28.23| image:: {filename}/images/Screen-Shot-2014-10-22-at-18.28.23.png
   :class: pure-img
   :target: {filename}/images/Screen-Shot-2014-10-22-at-18.28.23.png
.. |Screen Shot 2014-10-22 at 18.36.03| image:: {filename}/images/Screen-Shot-2014-10-22-at-18.36.03.png
   :class: pure-img
   :target: {filename}/images/Screen-Shot-2014-10-22-at-18.36.03.png
