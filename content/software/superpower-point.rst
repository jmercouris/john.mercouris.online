Superpower Point
################
:date: 2015-07-15 14:22
:author: jmercouris
:category: Software
:slug: superpower-point
:status: published

What does it do?
================

Superpower Point is an idea that was developed on a team I participated
in for a course titled Multimodal Interaction. The idea is that through
using natural gestures (no handheld devices) you should be able to go
through a presentation.

..
   http://jmercouris.com/wp-content/uploads/2015/07/Superpowerpoint.mp4"


Technology Demonstration:
=========================

.. youtube:: vKPNY0GjnIs

Prerequisites to run the code:
==============================

You need the following Libraries installed (unzipped and copied folders)
into Processing's libraries folder (usually
Documents/Processing/libraries).

For example, here's what my Processing libraries folder looks like (you
do not need blobscanner, or old):

|Screen Shot 2015-07-15 at 17.19.23|

Simple Open NI:
---------------

Easy Installation:
~~~~~~~~~~~~~~~~~~

https://code.google.com/p/simple-openni/wiki/Installation

Manual Installation:
~~~~~~~~~~~~~~~~~~~~

https://code.google.com/p/simple-openni/downloads/list

Simply download, unzip, and place the folder into your Processing
library folder.

Websocket P5
------------

https://github.com/muthesius/WebSocketP5

Same installation method as Simple Open NI

Processing: Kinect Detection
============================

For the detection, the program uses SimpleOpenNI with an Xbox Kinect.
This can be used to detect the position of any number of skeletal joints
for example:

::

    SimpleOpenNI.SKEL_TORSO
    SimpleOpenNI.SKEL_LEFT_HIP
    SimpleOpenNI.SKEL_LEFT_KNEE

Then, using these points in the skeleton, you can do simple detection.
For our program, what we did was check to see if the left or right arm
was above the torso, and 300 or more px away from the torso in the x
direction. This action would look like someone raising their right or
left hand to signal the presentation to go forwards or backwards.

The early detection code looked like this (largely based off the
examples which can be found at:
*parentDirectory*/Processing/libraries/SimpleOpenNI/examples):

::

    import SimpleOpenNI.*;

    SimpleOpenNI context;
    color[] userClr = new color[] { 
     color(255, 0, 0), 
     color(0, 255, 0), 
     color(0, 0, 255), 
     color(255, 255, 0), 
     color(255, 0, 255), 
     color(0, 255, 255)
    };

    PVector vectorPoint = new PVector();

    //-----------------------------------------------------------------
    // Setup
    //-----------------------------------------------------------------
    void setup()
    {
     // Attempt to Instantiate SimpleOpenNI
     context = new SimpleOpenNI(this);
     if (context.isInit() == false)
     {
     println("Can't init SimpleOpenNI"); 
     exit();
     return;
     }
     
     // Initialization
     size(640, 480);
     context.enableDepth();
     context.enableUser();
     context.setMirror(true);

     background(200, 0, 0);
     stroke(0, 0, 255);
     strokeWeight(3);
     smooth();
    }

    //----------------------------------------------------------------------
    // Draw
    //----------------------------------------------------------------------
    void draw()
    {
     // update the cam
     context.update();

     // draw depthImageMap
     //image(context.depthImage(),0,0);
     image(context.userImage(), 0, 0);

     // draw the skeleton if it's available
     int[] userList = context.getUsers();
     for (int i=0; i<userList.length; i++)
     {
     if (context.isTrackingSkeleton(userList[i]))
     {
     stroke(userClr[ (userList[i] - 1) % userClr.length ] );
     
     // Assign the Pvector named vectorPoint to the data of user[i]'s right hand
     context.getJointPositionSkeleton(userList[i], SimpleOpenNI.SKEL_RIGHT_HAND, vectorPoint);
     
     context.getJointPositionSkeleton(userList[i], SimpleOpenNI.SKEL_LEFT_HAND, vectorPoint);
     
     println("Check it: " + vectorPoint.x);

     drawSkeleton(userList[i]);
     } 
     }
    }

    // draw the skeleton with the selected joints
    void drawSkeleton(int userId)
    {
     // to get the 3d joint data
     /*
     PVector jointPos = new PVector();
     context.getJointPositionSkeleton(userId,SimpleOpenNI.SKEL_NECK,jointPos);
     println(jointPos);
     */

     context.drawLimb(userId, SimpleOpenNI.SKEL_HEAD, SimpleOpenNI.SKEL_NECK);

     context.drawLimb(userId, SimpleOpenNI.SKEL_NECK, SimpleOpenNI.SKEL_LEFT_SHOULDER);
     context.drawLimb(userId, SimpleOpenNI.SKEL_LEFT_SHOULDER, SimpleOpenNI.SKEL_LEFT_ELBOW);
     context.drawLimb(userId, SimpleOpenNI.SKEL_LEFT_ELBOW, SimpleOpenNI.SKEL_LEFT_HAND);

     context.drawLimb(userId, SimpleOpenNI.SKEL_NECK, SimpleOpenNI.SKEL_RIGHT_SHOULDER);
     context.drawLimb(userId, SimpleOpenNI.SKEL_RIGHT_SHOULDER, SimpleOpenNI.SKEL_RIGHT_ELBOW);
     context.drawLimb(userId, SimpleOpenNI.SKEL_RIGHT_ELBOW, SimpleOpenNI.SKEL_RIGHT_HAND);

     context.drawLimb(userId, SimpleOpenNI.SKEL_LEFT_SHOULDER, SimpleOpenNI.SKEL_TORSO);
     context.drawLimb(userId, SimpleOpenNI.SKEL_RIGHT_SHOULDER, SimpleOpenNI.SKEL_TORSO);

     context.drawLimb(userId, SimpleOpenNI.SKEL_TORSO, SimpleOpenNI.SKEL_LEFT_HIP);
     context.drawLimb(userId, SimpleOpenNI.SKEL_LEFT_HIP, SimpleOpenNI.SKEL_LEFT_KNEE);
     context.drawLimb(userId, SimpleOpenNI.SKEL_LEFT_KNEE, SimpleOpenNI.SKEL_LEFT_FOOT);

     context.drawLimb(userId, SimpleOpenNI.SKEL_TORSO, SimpleOpenNI.SKEL_RIGHT_HIP);
     context.drawLimb(userId, SimpleOpenNI.SKEL_RIGHT_HIP, SimpleOpenNI.SKEL_RIGHT_KNEE);
     context.drawLimb(userId, SimpleOpenNI.SKEL_RIGHT_KNEE, SimpleOpenNI.SKEL_RIGHT_FOOT);
    }
    //-----------------------------------------------------------------
    // SimpleOpenNI events
    //-----------------------------------------------------------------
    void onNewUser(SimpleOpenNI curContext, int userId)
    {
     println("onNewUser - userId: " + userId);
     println("\tstart tracking skeleton");

     curContext.startTrackingSkeleton(userId);
    }

    void onLostUser(SimpleOpenNI curContext, int userId)
    {
     println("onLostUser - userId: " + userId);
    }

    void onVisibleUser(SimpleOpenNI curContext, int userId)
    {
     //println("onVisibleUser - userId: " + userId);
    }

What the above code will do (when an Xbox Kinect is detected and plugged
into a USB) is draw an outline around any detected users. It will also
draw a skeleton simulating the user's skeleton. Also importantly there
are some SimpleOpenNI events that are implemented, for example, when the
program detects a new user using the method

::

    void onNewUser(...)

There should be a log in the Processing log indicating this event. This
can be useful if you want to inform users of detection/loss of
detection.

Processing: Speech Recognition
==============================

The speech recognition was done using a very helpful library which can
be found at: http://stt.getflourish.com. Using this library I was able
to get speech recognition up very quickly.

I needed to do two things, firstly setup an apache web server on my
computer, then find the web page served. The web page that I would be
serving through Chrome looks like the following:

::

    <!DOCTYPE HTML>
    <html>
    <head>
    <script type="text/javascript">

    // We need to check if the browser supports WebSockets

    if ("WebSocket" in window) {

    // Before we can connect to the WebSocket, we need to start it in Processing.
    // Example using WebSocketP5
    // http://github.com/muthesius/WebSocketP5

    var ws = new WebSocket("ws://localhost:8080/p5websocket");
    } else {

    // The browser doesn't support WebSocket

    alert("WebSocket NOT supported by your Browser!");
    }

    // Now we can start the speech recognition
    // Supported only in Chrome
    // Once started, you need to allow Chrome to use the microphone

    var recognition = new webkitSpeechRecognition();

    // Be default, Chrome will only return a single result.
    // By enabling "continuous", Chrome will keep the microphone active.

    recognition.continuous = true;

    recognition.onresult = function(event) {

    // Get the current result from the results object
    var transcript = event.results[event.results.length-1][0].transcript;

    // Send the result string via WebSocket to the running Processing Sketch
    ws.send(transcript);
    }

    // Start the recognition
    recognition.start();

    </script>
    </head>
    <body>
    </body>
    </html>

After setting up the web server, I added the following code to
Processing:

::

    /*
     Simple WebSocketServer example that can receive voice transcripts from Chrome
     */
     
    import muthesius.net.*;
    import org.webbitserver.*;
     
    WebSocketP5 socket;
     
    void setup() {
     socket = new WebSocketP5(this,8080);
    }
     
    void draw() {}
     
    void stop(){
     socket.stop();
    }
     
    void websocketOnMessage(WebSocketConnection con, String msg){
     println(msg);
     if (msg.contains("hello")) println("Yay!");
    }
     
    void websocketOnOpen(WebSocketConnection con){
     println("A client joined");
    }
     
    void websocketOnClosed(WebSocketConnection con){
     println("A client left");
    }

Then, by FIRST starting the Processing program, THEN opening Chrome and
navigating to my page, I was able to get basic speech recognition. I
simply had to talk to my computer (in a quiet environment) and I was
able to get speech recognition to output my messages into the Processing
log. It is EXTREMELY important that your web page is running on a web
server, it CANNOT be simply opened as a file by Chrome (i.e.
file:///chrome..)

Processing: Keystroke Simulation
================================

To perform mock keyboard presses to move the presentation forward or
back, I used java robot. Java robot is an automation toolkit to help you
automate GUIs and their testing, demoing, etc. I found a helper class
online and I modified it to rate limit how quickly a key can be pressed,
and I simplified the code:

::

    import java.awt.Robot;
    import java.awt.AWTException;
     
    public class KeystrokeSimulator {
     
    private Robot robot;
     
     KeystrokeSimulator(){
     try{
     robot = new Robot(); 
     }
     catch(AWTException e){
     println(e);
     }
     }
     
     void simulate(char c) throws AWTException {
     for (int i=0; i<10; i++) {
     robot.delay(1000);
     robot.keyPress(c);
     }
     }
    }

Everything Together
===================

When you add all the code together you get the following:

::

    //-----------------------------------------------------------------
    // Imports
    //-----------------------------------------------------------------
    import java.awt.AWTException;
    import java.awt.Robot;
    import java.awt.event.KeyEvent;
    import java.util.Date;
    import SimpleOpenNI.*;
    import muthesius.net.*;
    import org.webbitserver.*;
    import java.awt.Toolkit;
    import ddf.minim.*;

    //-----------------------------------------------------------------
    // Variable Definitions
    //-----------------------------------------------------------------
    KeystrokeSimulator keySimulator; // Helper to simulate key events
    Date lastActionDate = new Date(); // Time last action occured
    Date currentDate; // Current date used for calculating time elapsed
    float actionRepeatTime = 1500; // Amount of time before new action
    SimpleOpenNI context; // Reference to openNI Library
    PVector vectorPoint = new PVector(); // Reusable vector for tracking
    PVector vectorCore = new PVector(); // Reusable vector for tracking
    WebSocketP5 socket; // Web socket for communicating with chrome
    Minim minim; // Minim Library Instance
    AudioPlayer song; // Audio player for feedback


    // Colors of incremental users
    color[] userClr = new color[] { 
     color(255, 0, 0), 
     color(0, 255, 0), 
     color(0, 0, 255), 
     color(255, 255, 0), 
     color(255, 0, 255), 
     color(0, 255, 255)
    };

    //-----------------------------------------------------------------
    // Setup
    //-----------------------------------------------------------------
    void setup()
    {
     println("Initializing");
     keySimulator = new KeystrokeSimulator();

     // Attempt to Instantiate SimpleOpenNI
     context = new SimpleOpenNI(this);
     if (context.isInit() == false)
     {
     println("Can't init SimpleOpenNI"); 
     exit();
     return;
     }

     // Initialization
     size(640, 480);
     context.enableDepth();
     context.enableUser();
     context.setMirror(true);

     // Setup Voice Control
     socket = new WebSocketP5(this, 8080);

     // Setup Audio Playback
     minim = new Minim(this);

     // Set Drawing information
     background(200, 0, 0);
     stroke(0, 0, 255);
     strokeWeight(3);
     smooth();
    }

    //-----------------------------------------------------------------
    // Draw Method
    //-----------------------------------------------------------------
    void draw()
    {
     // Update the Camera
     context.update();
     image(context.userImage(), 0, 0);

     // Reduce Frame Checking Rate
     if (frameCount % 30 == 0) {
     int[] userList = context.getUsers();
     for (int i=0; i<userList.length; i++)
     {
     // Detect Gesture Left or right
     if (context.isTrackingSkeleton(userList[i]))
     {
     stroke(userClr[ (userList[i] - 1) % userClr.length ] );
     context.getJointPositionSkeleton(userList[i], SimpleOpenNI.SKEL_LEFT_HAND, vectorPoint);
     context.getJointPositionSkeleton(userList[i], SimpleOpenNI.SKEL_TORSO, vectorCore);
     if (abs(vectorPoint.x - vectorCore.x) > 300 && vectorPoint.y > vectorCore.y)
     {
     slideNext();
     } 
     context.getJointPositionSkeleton(userList[i], SimpleOpenNI.SKEL_RIGHT_HAND, vectorPoint);
     if (abs(vectorPoint.x - vectorCore.x) > 300 && vectorPoint.y > vectorCore.y)
     {
     slidePrevious();
     }
     }
     }
     }
    }

    //-----------------------------------------------------------------
    // Web Socket Receieved Message
    //-----------------------------------------------------------------
    void websocketOnMessage(WebSocketConnection con, String msg) {
     println(msg);

     if (msg.contains("next"))
     {
     slideNext();
     }
     if (msg.contains("previous"))
     {
     slidePrevious();
     }
    }

    //-----------------------------------------------------------------
    // Stop
    //-----------------------------------------------------------------
    void stop() {
     socket.stop();
    }

    //-----------------------------------------------------------------
    // Powerpoint Functions
    //-----------------------------------------------------------------
    void slidePrevious() 
    {
     println("Previous Slide");
     try {
     keySimulator.simulateEvent(KeyEvent.VK_P);
     }
     catch(AWTException e) {
     println(e);
     }
    }

    void slideNext()
    {
     println("Next Slide");
     try {
     keySimulator.simulateEvent(KeyEvent.VK_N);
     }
     catch(AWTException e) {
     println(e);
     }
    }

    //-----------------------------------------------------------------
    // Helping Classes & Functions
    //-----------------------------------------------------------------
    // draw the skeleton with the selected joints
    void drawSkeleton(int userId)
    {
     // to get the 3d joint data
     /*
     PVector jointPos = new PVector();
     context.getJointPositionSkeleton(userId,SimpleOpenNI.SKEL_NECK,jointPos);
     println(jointPos);
     */

     context.drawLimb(userId, SimpleOpenNI.SKEL_HEAD, SimpleOpenNI.SKEL_NECK);

     context.drawLimb(userId, SimpleOpenNI.SKEL_NECK, SimpleOpenNI.SKEL_LEFT_SHOULDER);
     context.drawLimb(userId, SimpleOpenNI.SKEL_LEFT_SHOULDER, SimpleOpenNI.SKEL_LEFT_ELBOW);
     context.drawLimb(userId, SimpleOpenNI.SKEL_LEFT_ELBOW, SimpleOpenNI.SKEL_LEFT_HAND);

     context.drawLimb(userId, SimpleOpenNI.SKEL_NECK, SimpleOpenNI.SKEL_RIGHT_SHOULDER);
     context.drawLimb(userId, SimpleOpenNI.SKEL_RIGHT_SHOULDER, SimpleOpenNI.SKEL_RIGHT_ELBOW);
     context.drawLimb(userId, SimpleOpenNI.SKEL_RIGHT_ELBOW, SimpleOpenNI.SKEL_RIGHT_HAND);

     context.drawLimb(userId, SimpleOpenNI.SKEL_LEFT_SHOULDER, SimpleOpenNI.SKEL_TORSO);
     context.drawLimb(userId, SimpleOpenNI.SKEL_RIGHT_SHOULDER, SimpleOpenNI.SKEL_TORSO);

     context.drawLimb(userId, SimpleOpenNI.SKEL_TORSO, SimpleOpenNI.SKEL_LEFT_HIP);
     context.drawLimb(userId, SimpleOpenNI.SKEL_LEFT_HIP, SimpleOpenNI.SKEL_LEFT_KNEE);
     context.drawLimb(userId, SimpleOpenNI.SKEL_LEFT_KNEE, SimpleOpenNI.SKEL_LEFT_FOOT);

     context.drawLimb(userId, SimpleOpenNI.SKEL_TORSO, SimpleOpenNI.SKEL_RIGHT_HIP);
     context.drawLimb(userId, SimpleOpenNI.SKEL_RIGHT_HIP, SimpleOpenNI.SKEL_RIGHT_KNEE);
     context.drawLimb(userId, SimpleOpenNI.SKEL_RIGHT_KNEE, SimpleOpenNI.SKEL_RIGHT_FOOT);
    }
    //-----------------------------------------------------------------
    // SimpleOpenNI events
    //-----------------------------------------------------------------
    void onNewUser(SimpleOpenNI curContext, int userId)
    {
     println("onNewUser - userId: " + userId);
     println("\tstart tracking skeleton");

     curContext.startTrackingSkeleton(userId);

     // Alert user tracking began
     song = minim.loadFile("connected.mp3");
     song.play();
    }

    void onLostUser(SimpleOpenNI curContext, int userId)
    {
     println("onLostUser - userId: " + userId);

     // Alert user tracking lost
     song = minim.loadFile("disconnected.mp3");
     song.play();
    }

    void onVisibleUser(SimpleOpenNI curContext, int userId)
    {
     //println("onVisibleUser - userId: " + userId);
    }

    //-----------------------------------------------------------------
    // Web Socket events
    //-----------------------------------------------------------------
    void websocketOnOpen(WebSocketConnection con) {
     println("A client joined");
    }

    void websocketOnClosed(WebSocketConnection con) {
     println("A client left");
    }

    //-----------------------------------------------------------------
    // Keystroke Simulator Class
    //-----------------------------------------------------------------
    public class KeystrokeSimulator {
     private Robot robot;

     KeystrokeSimulator() {
     try {
     robot = new Robot();
     }
     catch(AWTException e) {
     println(e);
     }
     }

     void simulateEvent(int inputKey) throws AWTException {
     currentDate = new Date();
     if (currentDate.getTime() - lastActionDate.getTime() > actionRepeatTime)
     {
     // Alert user command received
     song = minim.loadFile("command.mp3");
     song.play();
     robot.keyPress(inputKey);
     robot.keyRelease(inputKey);
     lastActionDate = new Date();
     }
     }
    }

I also added a few helpful features to the program, such as sounds so
that the user can recognize when their gesture has been detected, or if
they are being recognized as a user. All of the source code and project
can be found on Github (see URL below)

Where's the source code?
========================

https://github.com/jmercouris/PowerPointer

Can I have it for Windows? Linux? OS X?
=======================================

The program can be downloaded for any of those platforms and compiled
using Processing, please note you MAY have to get the Microsoft Kinect
drivers, check out what you need for your own system. Also important to
note is that the program currently uses the

::

    KeyEvent.VK_P

and

::

    KeyEvent.VK_P

this means that your presentation software should allow you to go
forward or back by pressing "p" or "n" on your keyboard (previous/next).
If your software does not allow you to do this, you could download the
source code and change the KeyEvent to the appropriate code for your
presentation software.

Then, when you are ready, in Processing, simply click "File --> Export
Application".

Conclusions
===========

The Kinect is still a long way off from providing a reliable way to
control a presentation. It works relatively well, but you must remain in
front of the sensor. As the technology progresses, this could very well
become a viable way of presenting. Anyways, I hope you enjoyed, and
thanks for reading!

.. |Screen Shot 2015-07-15 at 17.19.23| image:: {filename}/images/Screen-Shot-2015-07-15-at-17.19.23.png
   :class: pure-img

