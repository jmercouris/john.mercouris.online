Tomaterminal: Command Line Pomodoro Timer Tool
##############################################
:date: 2015-09-29 05:59
:author: jmercouris
:category: Software
:slug: tomaterminal-command-line-pomodoro-timer-tool
:status: published

The Source Code
===============

git@bitbucket.org:jmercouris/tomaterminal.git

The Pomodoro Method:
====================

    The technique uses a timer to break down work into intervals
    traditionally 25 minutes in length, separated by short breaks. These
    intervals are known as "pomodoros", the plural in English of
    the Italian word \ *pomodoro* meaning "tomato".

    Cirillo, Francesco. \ `"The Pomodoro Technique (The
    Pomodoro)" <http://baomee.info/pdf/technique/1.pdf>`__

The Need:
=========

I looked on the internet, and I could not find a simple terminal based
Pomodoro application. Most applications were either way too bloated, or
way too minimal. I did find a simple one line application that was a
terminal timer, I wanted functionality beyond that though. I did not
want to have to launch a separate application with a full GUI and
dependencies- though- I wanted something I could add to my path and
easily execute when I needed to get some work done.

The Result
==========

The end result is an absolutely super easy to use program.

./tomaterminal -- that's it!

|Screen Shot 2015-09-29 at 01.14.42|

The really cool thing is that, you don't have to pay attention to the
timer at all. Focus on your work, and when your break begins, the
program will alert your terminal with a visual or audible bell
(depending on your terminal settings and operating system).

|Screen Shot 2015-09-29 at 00.49.44|

In addition, as the program runs it will show you elapsed task/break
cycles in a row. Below is an example of how the program would change
over time:

|Screen Shot 2015-09-29 at 00.49.28|

|Screen Shot 2015-09-29 at 00.49.32|

|Screen Shot 2015-09-29 at 00.49.33|

The Details
===========

Firstly change the permissions of the program on your own machine:

::

    chmod +x tomaterminal.py

after you have changed the permissions, you should simply be able to
execute the program as normally:

::

    ./tomaterminal

When you execute the program, you can pass a couple of command line
options that alter the behavior. For example, if you wish to have a 10
minute work interval, and a 7 minute break interval you'd start the
program like this:

::

    ./tomaterminal -t 10 -b 7

Thanks for reading!
===================

I hope you enjoyed this short read, and hopefully this tool will be
useful to you. Best of luck!

The Source Code
===============

git@bitbucket.org:jmercouris/tomaterminal.git

The Full Source
===============

::

    #!/usr/bin/python
    import time
    import sys
    import argparse

    # Help String
    description_string = "Tomaterminal is a terminal program based on the Pomodoro (Italian for Tomato) method of working. In the Pomodoro method, you take a timer ((frequently tomato shaped) historically used in kitchens) and you set a 25 minute timer for work. After 25 mintues are completed, you set a 5 minute timer for break. Tomaterminal emulates this exact behavior, alerting you after 25 minutes have elapsed, then after your 5 minute break has elapsed."

    parser = argparse.ArgumentParser(description=description_string)
    parser.add_argument('-t','--task_time', type=int, help='Task Interval (minutes)',required=False)
    parser.add_argument('-b','--break_time', type=int, help='Break Interval (minutes)',required=False)
    args = parser.parse_args()

    # Time Definitions
    seconds_minute = 60
    minutes_hour = 60
    hours_day = 24

    # Task Definitions
    task_time = 25
    break_time = 5

    # Override task/break time if command line arguments passed
    if args.task_time is not None:
     task_time = args.task_time
    if args.break_time is not None:
     break_time = args.break_time

    # UI Definitions
    progress_bar_length = 40

    def alert():
     print ('\a')

    def progress(count, total, suffix=''):
     filled_len = int(round(progress_bar_length * count / float(total)))
     percents = round(100.0 * count / float(total), 1)
     bar = '=' * filled_len + '-' * (progress_bar_length - filled_len)
     sys.stdout.write('[%s] %s%s %s\r' % (bar, percents, '%', suffix))
     sys.stdout.flush()

    # Initial Entry into Program; Clear Screen
    print(chr(27) + "[2J")
    while True:
     # Task Loop
     progress(0,task_time,'Task Time Elapsed: 0:00')
     for i in range(0, task_time):
     time.sleep(seconds_minute)
     progress(i,task_time,'Task Time Elapsed: %s:00' % i)
     alert()
     # Break Loop
     progress(0,task_time,'Break Time Elapsed: 0:00')
     for i in range(0, break_time):
     time.sleep(seconds_minute)
     progress(i,break_time,'Break Time Elapsed: %s:00' % i)
     alert()

.. |Screen Shot 2015-09-29 at 01.14.42| image:: {filename}/images/Screen-Shot-2015-09-29-at-01.14.42.png
   :class: pure-img
.. |Screen Shot 2015-09-29 at 00.49.44| image:: {filename}/images/Screen-Shot-2015-09-29-at-00.49.44.png
   :class: pure-img
.. |Screen Shot 2015-09-29 at 00.49.28| image:: {filename}/images/Screen-Shot-2015-09-29-at-00.49.28.png
   :class: pure-img
.. |Screen Shot 2015-09-29 at 00.49.32| image:: {filename}/images/Screen-Shot-2015-09-29-at-00.49.32.png
   :class: pure-img
.. |Screen Shot 2015-09-29 at 00.49.33| image:: {filename}/images/Screen-Shot-2015-09-29-at-00.49.33.png
   :class: pure-img
