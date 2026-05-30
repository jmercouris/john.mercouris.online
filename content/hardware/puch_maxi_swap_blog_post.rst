Puch Maxi 1P52FMI Engine Swap: A Complete Build Log
===================================================

:Date: 2023-08-24
:Author: John Mercouris
:Category: Hardware
:Description: Modifying a classic moped with a modern engine.
:Tags: moped, puch maxi, engine swap, 1P52FMI, honda, engineering, CAD, fabrication
:status: draft

This is a compilation of my forum posts documenting the complete build
process of swapping a 1P52FMI (Honda-style) engine into a Puch Maxi
frame. This project took approximately 8 months from initial concept
to rideable bike.

----


2022-12-19
----------


Hello everyone, I recently rebuilt a Puch Maxi (affectionately named
Pistachio). After completing the project, of course I had to
completely redo it. I wanted to more effortlessly keep up with
traffic, and I missed having multiple gears. I could have designed a
gearbox for the e50, but it seemed beyond my engineering
capabilities. I figured it would be better to adapt an existing engine
and transmission combination to fit the Puch Maxi frame. Of course,
the obvious choice was the 1P52FMI, this meant that I would be able to
fit a Honda engine without any further modification, thus, I removed
the engine and began taking measurements. Offering up the engine, it
appears it *will* fit in the allotted space. I also know that my Puch
Maxi frame is a little wonky- even the OEM e50 engine interferes with
the front-fender (I have broken several spark plug mounts). I ended up
creating a complete scale CAD model of the frame, and engine to play
with mounting positions in a 3D space. From this CAD prototype, I
ended up playing with several positions and angles. I would move the
X, Y, and the angle of the engine until I could get something that fit
properly. Even with CAD, I ended up producing around eight prototype
engine mounts to find something that fit just *right*. Every movement
of the engine was a compromise. My task was complicated by my
appreciation for these frames- no cutting was allowed! Everything
needed to be an addition! Finally, I settled on an angle and mount
design that was manufacturable.

----



.. image:: images/puch-maxi-swap/image_268247.jpg
   :alt: Build progress
   :class: pure-img


.. image:: images/puch-maxi-swap/image_268248.jpg
   :alt: Build progress
   :class: pure-img


.. image:: images/puch-maxi-swap/image_268249.jpg
   :alt: Build progress
   :class: pure-img


.. image:: images/puch-maxi-swap/image_268250.jpg
   :alt: Build progress
   :class: pure-img


.. image:: images/puch-maxi-swap/image_268251.jpg
   :alt: Build progress
   :class: pure-img



2022-12-19
----------


The final position of the engine was satisfactory. It was impossible
for the engine to hit the front fender, and it allowed for sufficient
ground clearance. The engine could not be moved any closer to the
frame, there is approximately one millimeter of clearance from the
back of the engine to the frame. After validating the position with a
rough 3D FDM mount and some blocks, I decided to settle on a complete
design. I printed a more solid 3D mount that will mount on the other
side to validate both engine mounts. Again, for the sake of
manufacturability, I designed both the left and the right mounts to be
the same. Of course the engine is *not* the same on both sides. Widths
and tolerances are different. However, I did manage to make it work
:-) I also designed (not visible) a frame brace. Everything is
designed to be made of 3MM powder coated stainless steel. Due to the
extra power/torque/weight of this engine/transmission combination,
I've done a significant amount of analysis to design something that
can withstand the stresses of the new system.

----



.. image:: images/puch-maxi-swap/image_268252.jpg
   :alt: Build progress
   :class: pure-img


.. image:: images/puch-maxi-swap/image_268253.jpg
   :alt: Build progress
   :class: pure-img


.. image:: images/puch-maxi-swap/image_268254.jpg
   :alt: Build progress
   :class: pure-img


.. image:: images/puch-maxi-swap/image_268255.jpg
   :alt: Build progress
   :class: pure-img


.. image:: images/puch-maxi-swap/image_268256.jpg
   :alt: Build progress
   :class: pure-img



2022-12-19
----------


Finally, I managed to make the stock exhaust fit in the space. You can
see the carburetor and intake mounted, no problem with space, the wire
shield even fits! You can also see the position of the shifter on this
side. Due to the lower ground clearance of this engine, I also
designed a mount for foot pegs directly below the engine. As you can
see, this mount is again designed for manufacturability. It is
designed to be bent within a hydraulic brake (and the same width 3MM
stainless steel). This should be far beyond robust. Here is what it
looks like from the side:

----



.. image:: images/puch-maxi-swap/image_268257.jpg
   :alt: Build progress
   :class: pure-img


.. image:: images/puch-maxi-swap/image_268541.jpg
   :alt: Build progress
   :class: pure-img


.. image:: images/puch-maxi-swap/image_268660.jpg
   :alt: Build progress
   :class: pure-img


.. image:: images/puch-maxi-swap/image_268661.jpg
   :alt: Build progress
   :class: pure-img


.. image:: images/puch-maxi-swap/image_269062.jpg
   :alt: Build progress
   :class: pure-img



2022-12-19
----------


For those wondering, here is how the engine looks from the top: It is
actually quite balanced. The weight is as low as it can possibly be,
and it is quite comfortable. Most of the sticking out of the "engine"
on the right is actually the transmission. The jug and crank are
centered on the center-line of the Maxi frame. Finally, here is where
I am at today: My next steps: 1. Mount the foot pegs and validate my
mount design. 2. Create an idler for the chain to allow it to cleanly
run between the rear sprocket and the engine. 3. Order my parts from
the CNC manufacturer who will take care of the hydraulic bending,
cutting, and powder coating. After that, my job requires no more
custom fabrication, it will just involve running cables to the new
carburetor, a new fuel line, and a clutch cable. I have designed
everything to make it reproducible/computer designed. If anyone is
interested in a kit for their own project, I believe I can have all of
the parts manufactured for around 250$. This kit would require no
fabrication, and be entirely bolt in, and not modify the Maxi frame at
all. If there is any interest, I would be happy to organize a
production run :-)

----



.. image:: images/puch-maxi-swap/image_269063.jpg
   :alt: Build progress
   :class: pure-img


.. image:: images/puch-maxi-swap/image_269064.jpg
   :alt: Build progress
   :class: pure-img


.. image:: images/puch-maxi-swap/image_270344.jpg
   :alt: Build progress
   :class: pure-img


.. image:: images/puch-maxi-swap/image_270611.jpg
   :alt: Build progress
   :class: pure-img


.. image:: images/puch-maxi-swap/image_270612.jpg
   :alt: Build progress
   :class: pure-img



2022-12-27
----------


I did consider a plastic chain guide because I had seen them within
the context of timing chains on automobiles. I reasoned that because
they are lubricated they last, and that they would not last outside of
a well oiled environment. I now see that they *do exist* in a non
lubricated context! Perhaps then it is enough to create a part that
will be milled out of teflon that attaches to the pedal hub. That
could create a relatively smooth flow for the chain. Additionally, I
had designed the idler sprocket bracket to be made of (up to) 7mm of
stainless steel, which is certainly more than enough strength. I know
that bearings can be made strong enough for this application, they are
used in the automotive space already. Conclusion: 1. I'll design a
teflon chain guide version 2. I'll run simulations against a 7mm thick
stainless steel idler against multiple magnitudes of the maximum
engine power 3. I'll calculate to see how much the chain will
tighten/slacken with the swing arm travel thank you for the feedback,
it has been incredibly helpful!

----



.. image:: images/puch-maxi-swap/image_270614.jpg
   :alt: Build progress
   :class: pure-img


.. image:: images/puch-maxi-swap/image_270615.jpg
   :alt: Build progress
   :class: pure-img


.. image:: images/puch-maxi-swap/image_270616.jpg
   :alt: Build progress
   :class: pure-img


.. image:: images/puch-maxi-swap/image_271169.jpg
   :alt: Build progress
   :class: pure-img


.. image:: images/puch-maxi-swap/image_271170.jpg
   :alt: Build progress
   :class: pure-img



2022-12-29
----------


I have completed my analysis! Please let me know if I have made any
logical mistakes! Engine specification: Max. Torque & Rotating Speed:
9.3N.m/4500r/min Based on a sprocket with 50cm diameter, I've
calculated that it will apply a force of 186 newtons upon the
chain. For the purposes of my analysis, I assume all of this pressure
will directly act upon the mount. For the idler mount FEM analysis
I've selected a generic high carbon steel. I've considered a factor of
5 for the purposes of safety. Given the above I've calculated a
maximum Y displacement of -74.34 µm. I believe this amount to be
acceptable, and to demonstrate the mount is strong enough. For the Z
displacement under this load, I've calculated a displacement of
-0.54 mm. I do not believe this is enough to throw off the chain. the
Z displacement: the max shear stress also looks quite promising and
well within tolerances: I would like to emphasize that these
calculations are made with a safety factor of 5, and a simplified
model of the idler cog. I do not believe that the mount itself will be
the problem. I believe if there *is* to be a problem, it will be
eating bearings. If this is to happen, I believe it can be compensated
with stronger bearings (titanium bearings?). Again, please let me know
if I am making any mistakes in my analysis! I want to make something
safe and reliable!

----



.. image:: images/puch-maxi-swap/image_271171.jpg
   :alt: Build progress
   :class: pure-img


.. image:: images/puch-maxi-swap/image_271172.jpg
   :alt: Build progress
   :class: pure-img


.. image:: images/puch-maxi-swap/image_271174.jpg
   :alt: Build progress
   :class: pure-img


.. image:: images/puch-maxi-swap/image_271175.jpg
   :alt: Build progress
   :class: pure-img


.. image:: images/puch-maxi-swap/image_275074.jpg
   :alt: Build progress
   :class: pure-img



2022-12-29
----------


With a redesigned mount I've been able to achieve a maximum
displacement of 92.13 µm under a safety factor of 10. The engine at no
point will produce a force 10 times greater than what it is rated as
its maximum nominal output. Additionally, even though I do not
anticipate shear loads, with two points of contact, it will not be
able to rotate. For the sake of testing, I considered the scenario in
which there is a shear load equal to ten times the maximum nominal
engine output. In this case there is a maximum displacement of 0.12 mm
in the Z plane. This is not enough to derail the chain. With regards
to the concern about the mounting surface being insufficiently strong,
I agree. That is why every single bolt that I am using is triangulated
between sides of the frame. For example, the inner frame brace which
I've designed forms a connection to both the left and right engine
mount. I am not relying on the strength of the original frame, I am
heavily bracing it where necessary.

----



.. image:: images/puch-maxi-swap/image_275672.jpg
   :alt: Build progress
   :class: pure-img


.. image:: images/puch-maxi-swap/image_275673.jpg
   :alt: Build progress
   :class: pure-img


.. image:: images/puch-maxi-swap/image_275674.jpg
   :alt: Build progress
   :class: pure-img


.. image:: images/puch-maxi-swap/image_279239.jpg
   :alt: Build progress
   :class: pure-img


.. image:: images/puch-maxi-swap/image_279240.jpg
   :alt: Build progress
   :class: pure-img



2022-12-29
----------


As per the bearing, I've selected one with a dynamic radial load
bearing of 6672 newtons. You can see the bearing specifications here:
https://www.mcmaster.com/6153K152/

----


2022-12-29
----------


The chain line is the same.

----


2022-12-30
----------


If I change the bearing type from a ball bearing to a needle-roller
type bearing I can have a dynamic load rating of 20684 newtons (4650
lbs), and a static load rating of: 35808 newtons (8050
lbs). https://www.mcmaster.com/5905K551/ I cannot imagine this would
not be sufficient?

----


2022-12-31
----------


I was thinking I should cut it from carbon fiber to make it lighter ;-)

----


2022-12-31
----------


Hello James, you're absolutely right, and yes I thought about that,
but it is simply *not* possible to mount the sprocket of the engine
without radically moving the font wheel forwards. Since I did not want
to modify the existing chassis, I had to compromise on the position
and find another way to transfer the power.

----


2023-01-02
----------


I'm not sure why you think I am being antagonistic. I made it quite
clear many times that I am interested in pursuing the best and safest
solution! It is not like I am insisting that I *must* go the route of
an idler. I said I would make a jackshaft prototype, and I have. I
will be assembling it shortly on-chassis to see how it fits
together. Again to re-iterate. I am not married to any particular
idea. I am interested in the best, and safest solution. I am trying to
talk things out and understand them.

----


2023-01-02
----------


I want a multi speed manual transmission with a little more power. I
enjoy shifting between gears, and I enjoy the lightness of my moped. I
specifically want my Puch Maxi with a Honda engine and transmission
combination (the Lifan is just for mockup purposes). My objective is
to keep the Maxi frame entirely in factory condition. If that means
making a jacksaft for power transmission, I can do that. I understand
this engine is not designed for this chassis. I am however determined
to make it work, and to work well. The ultimate objective: to have fun
making things.

----


2023-01-03
----------


Yes, I've owned motorcycles in the past. I used to have a Suzuki
GN125, and I really loved that bike. I believe when it is all said and
done, the Honda engine has a lot of performance potential, and
shifting gears is a lot of fun. And yes, I've ridden a kitted Maxi, I
have two Maxis.

----


2023-01-07
----------


A new update. First the simple things: I created an exhaust mount: I
did try a few different profiles, first the thin one, and then the
thicker one: Here is how it looks from the side: the thicker one is
more robust, and it works very nicely with a b-spline. I will stick
with the thicker one!

----


2023-01-07
----------


With regards to the jackshaft design, I am pleased to say that I am
quite confident it will work. I did do a few design iterations:
Firstly I started with the following: this one uses a 14 tooth
sprocket with a distance of 55 mm from the pedal shaft center line. It
works, but it...

----


2023-01-27
----------


This electrical enclosure box was necessary for a few reasons: 1. I
wanted a place to put the CDI 2. I wanted a place to store the
electronics away from the exhaust (which is now on the other
side) 3. I wanted the electronics to be neat and protected from
water! 4. I wanted a way to route the cable. As you can see from the
design, it utilizes the hole in the side of the Maxi. It is set to be
40.30 mm in diameter, and this causes a perfect snap! Very
satisfying. Additionally, if you are *not* using the chain guard, it
will utilize it's bolt hole to mount on the front. If you *are* you
using the chain guard, the bolt hole for the chain guard goes through
the case. Here it is installed without the chain guard:

----


2023-02-02
----------


I am very happy and excited to report that I got my parts from
SendCutSend! They were wonderfully made, and of course came with a
small packet of candy (sour patch kids). I took out the 303 stainless
parts, and they were incredibly strong. I think I am going to redesign
the peg mount to make it much much less bulky and expensive. I could
not bend this with the pegs on it, standing on it, jumping on it. It
is incredibly solid, and I haven't even spot welded the tabs
together. I am confident I could significantly reduce the complexity
and cost of this part.

----


2023-02-02
----------


I then began prototyping the offset spacers in my mount. I had
calculated values for these, but it was time to test if these values
were accurate! All of the prototypes are made of PLA, but will be
replaced by 5052 aluminum with a 15mm OD and an 8mm ID (the same
dimensions, just made from aluminum). In the above photo you can see
the inner frame braces which serve to reinforce the frame in this
area. Finally, here is the whole assembly with the jackshafts as well:

----


2023-02-02
----------


Lastly, I mounted the engine: It fit perfectly, and I was very
satisfied! Then I mounted the exhaust: Then the carburetor:

----


2023-02-03
----------


Thank you wiild, that clears up so many things for me! I will probably
remove that sensor and connector then, since it serves no purpose for
me (or maybe I will use it to have a neutral light on the dashboard?
and/or gear position lights showing what gear I am in?). P.S. I did
end up ordering a harness that will arrive tomorrow with a new
connector, so I will probably just use that instead of cutting the
unused sensor. In any case, I will have a second connector available
for my second conversion ;-)

----


2023-02-04
----------


Just a follow-up, willd was correct, wiring is sorted! Engine runs, it
sounds great :-)

----


2023-02-11
----------


There have been a few changes made to the bike. Firstly, I designed a
new longer electrical box that will also hold the coil: This means
that the only exposed wiring is the wire going to the spark plug. When
everything is nicely buttoned up, here is what it looks like:

----


2023-02-11
----------


The next thing I began doing was testing the jackshaft mount in
earnest. I have been really struggling with thinking of a good
bearing/shaft retention strategy. In the end I decided to press fit
the bearings in the jackshaft mount and use star locking washers to
retain the sprockets on the shaft in the correct positions. Below you
can see a shot of the test fit of both chains: for some reason the
sprockets do not flow smoothly. I am not sure if it is because I was
using a test shaft made of PLA causing them to bend, or because I have
to grind a bevel on the gears, or because they are technically
motorcycle 420 sprockets, or because they are prototype gears and are
too narrow.

----


2023-02-11
----------


Finally, here is a shot of the new peg mount: in this configuration,
they are flipped up, instead of down as in the previous
iteration. They are also made of 6mm stainless steel, and are
incredibly strong. Here is a shot showing the lean angle they are
capable of: The angle is about 45 degrees, I think that is more than
sufficient for moped speeds. Combined with folding pegs, I think I
will be OK!

----


2023-02-12
----------


I don't think so, the lean angle is better than the factory pedals-
I've measured.

----


2023-05-14
----------


Finally after all of this work, the chain wasn't immediately binding
between the Jackshaft and the engine. It took about 4 laser cut
prototypes, and 6 PLA ones, and endless tweaking of the Jackshaft
sprockets, chains, the engine sprocket, etc. But I was able to drive
forward about 10 feet :-) The only reason I did not drive further was
because the engine kept dying on me, I have to tune the carburetor! I
have taken careful measurements and notes to try to tweak things
precisely. I believe there is still some improvement that can be had
by utilizing wider sprockets, and slightly different sprocket spacing
bushings. I will continue to refine it a little bit more, and when it
is ready, I will publish the definitive materials and build guide!
Hopefully a test ride video will be coming soon!

----


2023-05-14
----------


The weather is not so great, and the engine tuning is not so great,
but here is a ride! I'll need to add a choke lever for the engine so
that I can control it on the handlebars. The whole time you see me
riding it, the choke is fully engaged. The last things to
do: 1. Wiring the lights 2. Wiring the kill switch 3. Fitting the side
covers 4. Replacing the PLA spacers with machined aluminum (I already
have the material, just need to cut them with a bandsaw or a
lathe) 5. Attaching a license plate/making or buying a bracket

----


2023-05-15
----------


Thank you :-) I'll be sure to update as I finish up the final bits!

----


2023-05-15
----------


Yes indeed, I will be raising the pegs somehow, you were all right :-D
just have to figure out how to do it...!

----


2023-05-15
----------


Perhaps something like this:
https://www.treatland.tv/puch-chopper-pedal-conversion-p/puch-chrome-chopper-pegs.htm
where I then angle the pegs forward and down. Then I can take the
shifter and flip it upside down on the shaft... maybe that is the way.

----


2023-05-24
----------


I've now replaced the PLA spacers with ones cut from aluminum. This is
my first time cutting aluminum tubing. I ended up purchasing the
non-ferrous miter saw blade from Harbor freight. It worked pretty
well, but my mistake was operational and it ended up chipping the
edges of the spacers. I would push the miter saw down and as soon as
it cut, I would lift it up. This would lead to the smaller un
supported section of tubing often being caught by the edge of the
miter saw blade and nicking it. I ended up learning (towards the end
of processing the spacers), that I needed to perform the cut, keep the
blade down, and wait for it to stop spinning before raising it
up. This resulted in much cleaner cuts. In order to compensate for the
cut issues, I performed some filing to flatten the surfaces a little.

----


2023-05-29
----------


I mounted a license plate bracket:

----


2023-05-29
----------


I then mounted the side covers, but promptly removed them, as I
decided the bike looks better without them:

----


2023-05-29
----------


Lastly, I cut up the flywheel cover so that it would fit thew
jackshaft system. Here it is mounted to the bike:

----


2023-05-29
----------


The cases are currently protected by the peg mount which is a thick
3031 stainless steel plate. I took it for another test ride today to
see how it is after a small amount of tuning, and wow, this thing is
absolutely violent. I almost feel that I need to find a smaller rear
sprocket, because it is a *rocket*. I also keep blowing lights, but no
idea why that is. I've ordered more 12v lights from treats, let's see
what happens. Maybe I'll need a small battery to prevent voltage
spiking and blowing out bulbs. Final steps: - New, longer rear
shocks - Fix lights - Create (or buy) a trumpet intake

----


2023-05-29
----------


That's a good idea, thank you Jay.

----


2023-07-26
----------


I didn't try it, I also figured it would be too low. As soon as I am
back in my workshop I'll post an update with the new linkage I
designed.

----


2023-08-22
----------


Finally back at my workshop, and I've been able to complete the
linkage. I have to say, the results are *really* good. It actually
feels better than the original shifter in the original location. I
chose to use a shifter designed for some sort of Harley. It works
really well here, matches the rest of the bike as a simple black, and
is very comfortable on the foot. I'll have to do some more riding, and
then I think I will finally publish the complete materials and build
guide. Due to the shift linkage and elimination of the bottom bracket
for mounting the foot rests, I think it will actually be significantly
cheaper. I anticipate that someone could recreate this build for
around 100$ for all components + the engine cost. In total, I would
therefore estimate this to be a 400$ upgrade. I don't think an upgrade
gets cheaper than that!

----


2023-08-22
----------


Update: just snapped a chain! Way too much torque! I can even start in
third or fourth gear without issue. I think I need a smaller rear
sprocket. This thing will rev to the moon it seems. I also need a way
to keep the jackshaft shaft from falling out. Right now, it can just
roll right out. I'll have to create a cover of some sorts to prevent
it from doing so.

----


2023-08-24
----------


This thing is absolutely hectic. Does anyone know of a smaller tooth
rear sprocket I can purchase?

