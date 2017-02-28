The Clock
#########
:date: 2015-03-23 05:00
:author: jmercouris
:category: Design, Hardware, Software
:slug: the-clock
:status: published

The Idea
========

*The Clock* is a project aimed at making our world feel more connected.
Different time zones are often represented by different clocks set
amongst a wall. This separates us from other locations and creates a
divide: this is our time, that is their time.

    What if we had a clock that could travel through time and space to
    connect us with another locale?

The Inspiration
===============

The inspiration from the international clock arose from my frequent
trips to Europe. I am a dual citizen Greek-American and I have never
liked changing my watch when switching time zones. It felt as if I was
severing a connection to my homeland whether it was leaving Greece or
leaving the US. Especially lately that I have begun my Master's program
in Germany, I do not like to switch my watch from American time. It
helps me feel as if I have kept a piece of my identity with me.

The Prototype
=============

The first prototype involved several simple components:

-  An Arduino
-  An EasyVR
-  A Clock

The Development Journey
=======================

The development of this project was not at all straightforward. It began
simply with the purchase of a clock from inventables.com.

|IMG_2692|

I wanted to figure out what makes it tick; literally. So I began
disassembly and found out that actually the mechanism was relatively
straightforward.

|IMG_2905|

| I then began to take it apart and figure out how I was going to
  control the actuation of the motor. I found that I could separate the
  motor from the rest of the enclosure.
| |IMG_2925|

After separating the motor, a quick run with the multimeter confirmed
that the quartz circuit underneath the motor was simply alternating the
polarity. This would cause the motor to jump from it's initial position,
to a half rotation forward. If you repeat this process multiple times,
you get a full rotation, and thus accurate time keeping in an
elegant stepper motor that uses the clock as its gearing.

Having discovered this, actuating the motor was a simple case of
connecting leads to the motor and running them out of the clock
enclosure, from there they could be manually controlled by an arduino.

|IMG_2926|

 

|IMG_2924|

Here is quick video of the first attempts to get the motor to move.
Unfortunately I had not supplied enough power to the motor and it was
unable to make a full rotation.

http://youtu.be/thIQ7zJQvxU

After changing the duty cycle on the PWM pins on the Arduino I was able
to successfully get the motor to rotate in emulation of the original
quartz circuit.

http://youtu.be/WudKeSwK7W8

Finally after successfully rotating the motor, I've reassembled the
clock with my modifications in place and am demonstrating normal
movement. The only modification is that I am doing a full cycle instead
of half steps like the original quartz circuit.

http://youtu.be/kBwP5rOW_es

After having reassembled the clock, I began pushing the limits of the
little motor seeing how far I could take it. The result is, impressively
fast.

http://youtu.be/N8E02IusGhE

After reassembling the clock I found that the performance was
significantly lackluster in comparison with its disassembled
performance. The difference can most likely be attributed to friction in
the closed assembly.

http://youtu.be/2E1FBxHV_SA

I've achieved a good speed with the clock and have managed to make it
operate almost as quickly as it did disassembled. There were strange
mechanics in place with the gearing and it appeared that specific
frequencies were prone to jamming the mechanism. I found that the ideal
delay was 20 milliseconds between pinging the motor and then changing
the polarity. For unknown reasons 17 milliseconds was detrimental as was
a value of 30 milliseconds. I am sure there is mathematical significance
to 20, but I cannot explain it.

http://youtu.be/f8grYupFAJE

The next steps involved adding some sort of control interface. I
initially envisioned that someone could easily go up to the clock and
press a switch to change time zones. At which point the clock would
change the time and would show the new time in a display of some sort.
Unfortunately this kind of change for a clock is difficult and
uninspiring. It also adds a mental blockade and an identification of the
country which is against the aim of the project.

Voice Recognition: Normally Difficult, Easy with EasyVR
-------------------------------------------------------

Instead I opted for voice recognition. Voice recognition on a device
with as little processing power as the arduino is a difficult task. I
thought of many derivates such as offloading the processing to a
computer and communicating via bluetooth, or offloading processing to an
Android device, and again, communicating through bluetooth.

Finally after extensive research and deciding that the voice recognition
had to be integrated into the clock; I found EasyVR. EasyVR is a great
device available from  http://www.veear.eu/products/easyvr/. I cannot
recommend this product enough. After a few simple training sets with the
Arduino plugged into my computer, I was able to implement voice
recognition in an hour. The longest part of the implementation involved
configuring virtual box with Windows XP and guest additions (VR
Commander (the training and configuration program) only operates in
Windows).

|IMG_2690|

The Final Product
=================

A final demonstration of the project in its current state with
integrated VR. The clock operates as normally until prompted, at which
point it will "switch" to a new time zone. A helpful nudge is necessary
to deal with the jamming of the gears. I attempted to solve this by
implementing a logarithmic acceleration algorithm in the code, but found
that as the clock progressed through certain frequencies, it was unable
to cope and would jam.

http://youtu.be/pm65W3PI7yQ

Future Improvements
===================

As suggested in the video, there are plenty of potential future
improvements. The most obvious one is greatly increasing the speed of
the time zone switching by integrating a servo into the clock adjustment
mechanism that currently exists on the clock. Modulating the motor to
change the time is possible, but lacks the speed and reliability
(frequent jamming) when spinning at several hundred times its intended
operational parameters.

Another great improvement would be integrating wifi into the clock so
that it may be exact by utilizing atomic clock data. The original clock
had a quartz circuit inside, which is accurate, but over time and
day-light savings it may be inaccurate.

Conclusions
===========

I hope you enjoyed my project! The concept is that *The Clock* will help
us become a more unified community. It isn't their time, and our time.
It is our world's time.

The Code
========

Available from Git:

https://bitbucket.org/jmercouris/international-clock/overview

There are two files,

-  motorDriver which contains sample motor driving code.
-  generated which contains code generated by VR Commander (EasyVR
   Configuration and setup tool) that has had motorDriver code
   integrated.

I've also copied and pasted the files below for convenient reference.

::

    motorDriver.ino

::

    //2-Way motor control

    int motorPin1 = 5; // One motor wire connected to digital pin 5
    int motorPin2 = 6; // One motor wire connected to digital pin 6
    int dutyCycle = 200;
    int delayTime = 100;

    // The setup() method runs once, when the sketch starts

    void setup() { 
     // initialize the digital pins as an output:
     pinMode(motorPin1, OUTPUT); 
     pinMode(motorPin2, OUTPUT); 
     //rotate(1);
     //accelerate();
    }

    // the loop() method runs over and over again,
    // as long as the Arduino has power
    void loop() 
    {
     clock_tick();
    }

    // Input time in Hours +/-
    void rotate(int time)
    {
     // Convert Hours into Seconds (Cycles)
     time = time * 1800;
     int distance = abs(time);
     while(distance > 0)
     {
     distance--;
     analogWrite(motorPin1, dutyCycle); //rotates motor
     digitalWrite(motorPin2, LOW); // set the Pin motorPin2 LOW
     delay(delayTime);
     analogWrite(motorPin2, dutyCycle); //rotates motor
     digitalWrite(motorPin1, LOW); // set the Pin motorPin2 LOW
     delay(delayTime); 
     }
    }

    void clock_tick()
    { 
     analogWrite(motorPin1, dutyCycle); //rotates motor
     digitalWrite(motorPin2, LOW); // set the Pin motorPin2 LOW
     delay(1000);
     analogWrite(motorPin2, dutyCycle); //rotates motor
     digitalWrite(motorPin1, LOW); // set the Pin motorPin2 LOW
     delay(1000); 
    }

    // Peripheral does not behave as expected
    // Jams gears while accelerating
    void accelerate()
    {
     while(delayTime > 20)
     {
     int tickCount = 0;
     if (tickCount % 10 == 0)
     {
     tickCount = 0;
     delayTime --;
     } 
     else
     {
     tickCount ++;
     }
     
     analogWrite(motorPin1, dutyCycle); //rotates motor
     digitalWrite(motorPin2, LOW); // set the Pin motorPin2 LOW
     delay(delayTime);
     analogWrite(motorPin2, dutyCycle); //rotates motor
     digitalWrite(motorPin1, LOW); // set the Pin motorPin2 LOW
     delay(delayTime);
     }
    }

::

    generated.ino

::

    #if defined(ARDUINO) && ARDUINO >= 100
     #include "Arduino.h"
     #include "Platform.h"
     #include "SoftwareSerial.h"
    #ifndef CDC_ENABLED
     // Shield Jumper on SW
     SoftwareSerial port(12,13);
    #else
     // Shield Jumper on HW (for Leonardo)
     #define port Serial1
    #endif
    #else // Arduino 0022 - use modified NewSoftSerial
     #include "WProgram.h"
     #include "NewSoftSerial.h"
     NewSoftSerial port(12,13);
    #endif

    #include "EasyVR.h"
    EasyVR easyvr(port);
    //Groups and Commands
    enum Groups
    {
     GROUP_0 = 0,
     GROUP_1 = 1,
    };

    enum Group0 
    {
     G0_OK_CLOCK = 0,
    };

    enum Group1 
    {
     G1_CHICAGO = 0,
     G1_BERLIN = 1,
     G1_LONDON = 2,
     G1_NEW_YORK = 3,
     G1_TOKYO = 4,
     G1_SAN_FRANCISCO = 5,
    };

    EasyVRBridge bridge;
    int8_t group, idx;
    // Signifies clock is changing time zones
    boolean zone_changing = false;
    // Motor Control Pins
    int motorPin1 = 5; // One motor wire connected to digital pin 5
    int motorPin2 = 6; // One motor wire connected to digital pin 6
    int dutyCycle = 200;
    int delayTime = 20;


    void setup()
    {
    #ifndef CDC_ENABLED
     // bridge mode?
     if (bridge.check())
     {
     cli();
     bridge.loop(0, 1, 12, 13);
     }

     // run normally
     Serial.begin(9600);
     Serial.println("Bridge not started!");
    #else
     // bridge mode?
     if (bridge.check())
     {
     port.begin(9600);
     bridge.loop(port);
     }
     Serial.println("Bridge connection aborted!");
    #endif
     port.begin(9600);

     while (!easyvr.detect())
     {
     Serial.println("EasyVR not detected!");
     delay(1000);
     }

     easyvr.setPinOutput(EasyVR::IO1, LOW);
     Serial.println("EasyVR detected!");
     easyvr.setTimeout(5);
     easyvr.setLanguage(0);
     group = EasyVR::TRIGGER; //<-- start group (customize)
     // Set Motor Pins for clock
     pinMode(motorPin1, OUTPUT); 
     pinMode(motorPin2, OUTPUT); 

    }

    void action();

    void loop()
    {
     easyvr.setPinOutput(EasyVR::IO1, HIGH); // LED on (listening)
     Serial.print("Say a command in Group ");
     Serial.println(group);
     easyvr.recognizeCommand(group);

     do
     {
     if (!zone_changing)
     {
     clock_tick();
     }
     // can do some processing while waiting for a spoken command
     }

     while (!easyvr.hasFinished());
     easyvr.setPinOutput(EasyVR::IO1, LOW); // LED off
     idx = easyvr.getWord();

     if (idx >= 0)
     {

     // built-in trigger (ROBOT)

     // group = GROUP_X; <-- jump to another group X

     return;
     }

     idx = easyvr.getCommand();
     if (idx >= 0)
     {

     // print debug message
     uint8_t train = 0;
     char name[32];
     Serial.print("Command: ");
     Serial.print(idx);
     if (easyvr.dumpCommand(group, idx, name, train))
     {
     Serial.print(" = ");
     Serial.println(name);
     }

     else
     Serial.println();
     easyvr.playSound(0, EasyVR::VOL_FULL);
     // perform some action
     action();
     }
     else // errors or timeout
     {
     if (easyvr.isTimeout())
     Serial.println("Timed out, try again...");
     int16_t err = easyvr.getError();
     if (err >= 0)
     {
     Serial.print("Error ");
     Serial.println(err, HEX);
     }
     }
    }


    void action()
    {
     switch (group)
     {
     case GROUP_0:
     switch (idx)
     {
     case G0_OK_CLOCK:
     // write your action code here
     group = GROUP_1;
     // group = GROUP_X; <-- or jump to another group X for composite commands
     break;
     }
     break;
     case GROUP_1:
     switch (idx)
     {
     case G1_CHICAGO:
     // write your action code here
     rotate(.5);
     group = GROUP_0;
     break;
     case G1_BERLIN:
     // write your action code here
     group = GROUP_0;
     break;
     case G1_LONDON:
     // write your action code here
     group = GROUP_0;
     break;
     case G1_NEW_YORK:
     // write your action code here
     group = GROUP_0;
     break;
     case G1_TOKYO:
     // write your action code here
     group = GROUP_0;
     break;
     case G1_SAN_FRANCISCO:
     // write your action code here
     group = GROUP_0;
     break;
     }
     break;
     }
    }

    // Input time in Hours +/-
    void rotate(double time)
    {
     // Signify that we are changing time zones to avoid regular clock motion
     zone_changing = true;
     // Convert Hours into Seconds (Cycles)
     time = time * 1800;
     double distance = abs(time);
     while(distance > 0)
     {
     distance--;
     analogWrite(motorPin1, dutyCycle); //rotates motor
     digitalWrite(motorPin2, LOW); // set the Pin motorPin2 LOW
     delay(delayTime);
     analogWrite(motorPin2, dutyCycle); //rotates motor
     digitalWrite(motorPin1, LOW); // set the Pin motorPin2 LOW
     delay(delayTime); 
     }
     // Resume regular clock motion now that we are no longer switching time zones
     zone_changing = false;
    }

    // Clock Tick Moves
    void clock_tick()
    { 
     analogWrite(motorPin1, dutyCycle); //rotates motor
     digitalWrite(motorPin2, LOW); // set the Pin motorPin2 LOW
     delay(1000);
     analogWrite(motorPin2, dutyCycle); //rotates motor
     digitalWrite(motorPin1, LOW); // set the Pin motorPin2 LOW
     delay(1000); 
    }


.. |IMG_2692| image:: {filename}/images/IMG_2692.jpg
   :class: pure-img
.. |IMG_2905| image:: {filename}/images/IMG_29051.jpg
   :class: pure-img
.. |IMG_2925| image:: {filename}/images/IMG_2925.jpg
   :class: pure-img
.. |IMG_2926| image:: {filename}/images/IMG_2926.jpg
   :class: pure-img
.. |IMG_2924| image:: {filename}/images/IMG_2924.jpg
   :class: pure-img
.. |IMG_2690| image:: {filename}/images/IMG_2690.jpg
   :class: pure-img
