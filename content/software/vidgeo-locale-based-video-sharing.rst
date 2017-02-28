Vidgeo: Locale based video sharing
##################################
:date: 2014-11-13 22:59
:author: jmercouris
:category: Software
:tags: featured
:slug: vidgeo-locale-based-video-sharing
:status: published

Vidgeo is a program that my friend Eyoel and I created in order to share
videos within a geographical context. The program works in a very simple
way:

-  Record a video
-  Video get's placed on a map pinned to where the video is recorded
-  The video is available for distribution or searching by other users

The value of a geographic search method is far beyond the obvious.  It
can help users find information that is relevant to their needs. Let's
consider a few common use cases:

1. I am at a museum and want to watch an interesting presentation about
the sculpture I am looking at.

1. A. By using the app I can quickly find presentations about the
sculptures around me.

2. I am at a comedy club and I want to see the coolest performance ever
there.

2.A. I could open the Vidgeo app and look for the highest rated videos
at the location of the comedy club.

3. I want to look for travel information, or get an idea of what a beach
in Miami is like.

3.A. I can simply use the vidgeo app to look at the beach in Miami that
I am interested in. The video can give me a good feel for the atmosphere
and appearance.


Anyways, enough talk, let's get to some screenshots and explanations.


This is the first view you see when you open the program and login for
the first time:


|iOS Simulator Screen shot Mar 26, 2014, 5.07.44 PM|


This is your map view, from here you can browse, view, or record videos.
Every Green/Red dot represents a video with either positive or negative
reviews, the intensity of the green or the red indicates how positive or
negative the reviews are.


-  The bottom left button allows you to quickly jump to your point of
   reference.
-  The bottom middle red button allows you to record a vidgeo.
-  The bottom arrow immediately to the right of the red button allows
   you to refresh the available videos.
-  The far bottom right filter allows you to filter videos based on
   keywords, whether your friends posted them, popularity, etc.


-  Then, starting from the top we can see several auxiliary buttons. The
   top left gear button represents the settings icon.
-  The globe to the right of the gear icon represents how many views you
   have available to view videos outside your local (the goal being
   promoting local videos).
-  Finally, the top right home icon represents your user content page.
   My videos, friends videos, etc.


|iOS Simulator Screen shot Mar 26, 2014, 5.08.23 PM|


This is the user home page that they would get to by clicking the
"home" icon on the map browse page. From here they can view their own
videos, manage them, make them private, delete etc. They can also browse
through their favorite videos.


|iOS Simulator Screen shot Mar 26, 2014, 5.10.47 PM|


The above is an example of a video playback view. From here the user can
perform a number of useful actions. They can go back to browsing, flag
inappropriate content, share, or vote on their favorite videos.


|iOS Simulator Screen shot Mar 26, 2014, 5.11.08 PM|


This is the dialog that appears when a user tries to share a video. They
can share the location, post to Facebook, or send to other friends who
have Vidgeo.


What appears to be a relatively simple application has revealed immense
complexities in user design decisions and programming problems. For
example, how do we implement privacy features, do we limit the videos a
User can watch? What ended up being a simple app was the product of
intense feature scrutiny and extremely careful planning. Study of user
habits, analysis of user needs and constantly cycling through the design
phase. Finally, we were left with a most distilled and essential design.


.. |iOS Simulator Screen shot Mar 26, 2014, 5.07.44 PM| image:: {filename}/images/iOS-Simulator-Screen-shot-Mar-26-2014-5.07.44-PM.png
   :class: pure-img
.. |iOS Simulator Screen shot Mar 26, 2014, 5.08.23 PM| image:: {filename}/images/iOS-Simulator-Screen-shot-Mar-26-2014-5.08.23-PM.png
   :class: pure-img
.. |iOS Simulator Screen shot Mar 26, 2014, 5.10.47 PM| image:: {filename}/images/iOS-Simulator-Screen-shot-Mar-26-2014-5.10.47-PM.png
   :class: pure-img
.. |iOS Simulator Screen shot Mar 26, 2014, 5.11.08 PM| image:: {filename}/images/iOS-Simulator-Screen-shot-Mar-26-2014-5.11.08-PM.png
   :class: pure-img
