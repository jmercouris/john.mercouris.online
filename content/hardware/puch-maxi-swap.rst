Puch Maxi 1P52FMI Engine Swap: A Complete Build Log
===================================================

:Date: 2023-08-24
:Author: John Mercouris
:Category: Hardware
:Description: Modifying a classic moped with a modern engine.
:Tags: moped, puch maxi, engine swap, 1P52FMI, honda, engineering, CAD, fabrication
:status: draft

Abstract
--------

This is my journey documenting the complete build process of swapping
a 1P52FMI (Honda-style) engine into a Puch Maxi frame. This project
took approximately 8 months from initial concept to rideable bike.

Background
----------

The Puch Maxi is a moped that was sold from the 1970s-1980s- likely as
a response to rising fuel prices. It presented a solution for people
to get around without a lot of money.

A moped is ostensibly a bicycle with an engine, in practice, the
pedals are hardly useful (they exist only to legally legitmize it as a
"bicycle").

The Puch Maxi originally came with a 50cc 2-stroke engine (known as an
E50). This engine is able to accelerate a Maxi to a blistering 25-30
MPH (potentially faster on a steep down grade). While this engine is
great, simple, and with significant aftermarket support, it does have
some inherent flaws.

Firstly, being a two stroke means that you have to pre-mix oil and
gasoline every time you fill up the fuel tank. What this means: you
either hope the gas station you are visiting happens to have two
stroke oil, or you carry around a small bottle of oil with you.

Secondly, this engine is incredibly slow. While 50cc might be OK if
you are able to use a bike path, in the USA, one is not allowed to
ride a moped on bike paths. Ergo, you must ride in the main traffic
thoroughfares, something hardly comfortable when it takes you 30
seconds to reach 30MPH.

Thirdly, and finally, if you want any usable amount of performance,
you will be significantly compromising the reliability of your
engine. While many 2-stroke enthusiasts embrace, and even enjoy this
fact, I want a reliable machine that I can use to drive around.


The Beginning
-------------

My build began after I rebuilt my Puch Maxi (affectionately named
Pistachio). Upon completion, I of course had to completely redo it.


.. figure:: images/puch-maxi-swap/image_268247.jpg
   :alt: Build progress
   :class: pure-img

   Here is Pistachio shortly after being rebuilt.


I had two new goals: I wanted to more effortlessly keep up with
traffic, and I wanted to shift gears. I could have designed a gearbox
for the E50, but it seemed beyond my engineering capabilities. I
figured it would be better to adapt an existing engine and
transmission combination to fit the Puch Maxi frame.

The obvious choice was the 1P52FMI engine/gearbox. Being a Honda
clone, this meant that I would be able to fit a Honda engine (in the
future) without any further modification, thus, I began taking
measurements.


.. image:: images/puch-maxi-swap/image_268248.jpg
   :alt: Build progress
   :class: pure-img


Offering up the engine, it appears it *will* fit in the
allotted space. I also know that my Puch Maxi frame is a little wonky-
even the OEM e50 engine interferes with the front-fender (I have
broken several spark plug mounts). I ended up creating a complete
scale CAD model of the frame, and engine to play with mounting
positions in a 3D space.


.. image:: images/puch-maxi-swap/image_268249.jpg
   :alt: Build progress
   :class: pure-img


From this CAD prototype, I ended up playing with several positions and
angles. I would move the X, Y, and the angle of the engine until I
could get something that fit properly. Even with CAD, I ended up
producing around eight prototype engine mounts to find something that
fit just *right*. Every movement of the engine was a compromise. My
task was complicated by my appreciation for these frames- no cutting
was allowed! Everything needed to be an addition! Finally, I settled
on an angle and mount design that was manufacturable.



.. image:: images/puch-maxi-swap/image_268250.jpg
   :alt: Build progress
   :class: pure-img


.. image:: images/puch-maxi-swap/image_268251.jpg
   :alt: Build progress
   :class: pure-img



Mounting the Accessories and More
----------------------------------


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


.. image:: images/puch-maxi-swap/image_268252.jpg
   :alt: Build progress
   :class: pure-img


The next step was to begin mounting the accessories needed for the
engine to run. You can see the carburetor and intake mounted, no
problem with space, the wire shield even fits! You can also see the
position of the shifter on this side.


.. image:: images/puch-maxi-swap/image_268253.jpg
   :alt: Build progress
   :class: pure-img


Due to the lower ground clearance of this engine, I also designed a
mount for foot pegs directly below the engine. As with all other
components, this mount is designed for manufacturability. It is
designed to be bent within a hydraulic brake (and the same width 3MM
stainless steel). This should be far beyond robust. Here is what it
looks like from the side:


.. image:: images/puch-maxi-swap/image_268254.jpg
   :alt: Build progress
   :class: pure-img


Here is a view that shows you what the layout looks like from the
top. Viewing this, you might believe that the bike would lean to the
right, but it is in fact almost perfectly balanced. The cylinder runs
almost directly down the center-line of the frame.


.. image:: images/puch-maxi-swap/image_268256.jpg
   :alt: Build progress
   :class: pure-img



The Chain Line
--------------

The next big challenge was going to be figuring out the chainline. On
most motorcycles (bicycles, too), the main sprocket coming off the
engine (or the pedals) is in a straight line with the swing-arm pivot,
and the rear sprocket. Among many things, this ensures that as the
rear wheel moves up and down, the chain does not increase or decrease
in length.


.. image:: images/puch-maxi-swap/image_268257.jpg
   :alt: Build progress
   :class: pure-img


.. image:: images/puch-maxi-swap/chain_line.jpg
   :alt: Build progress
   :class: pure-img


As can be seen from the image above, we do not have a straight line
for our chain to run. The red line indicates the route that our chain
would take. Not only is this chain line more or less impossible, it
will also collide with the rear swing arm. We would have to mount our
wheel on only one side.


Trying to find a solution to this problem I looked around for
inspiration and came across this:


.. image:: images/puch-maxi-swap/image_268541.jpg
   :alt: Build progress
   :class: pure-img


I had seen similar chain guides used within the engines of modern
vehicles, and figured it would be possible. Looking at the angle we
have to contend with, it seems significantly more extreme than what is
shown on the motorcycle above. Still, modern engines have similarly
tight chain lines (with the big difference being that modern engines
are filled with oil).

After considering this for a while, I decided that it was likely not
possible. I pursued a different tack. I thought about mounting a
sprocket to enable the chain to angle up and around the swing arm.

.. image:: images/puch-maxi-swap/image_268660.jpg
   :alt: Build progress
   :class: pure-img


Here you can see some of the FEM analysis I did to determine how
strong the sprocket mount would need to be.

With an engine specification: Max. Torque & Rotating Speed:
9.3N.m/4500r/min and a sprocket with a 50cm diameter, I calculated
that it will theoretically apply a force of 186 newtons upon the
chain. For the purposes of my analysis, I assume all of this pressure
will directly act upon the mount. For the idler mount FEM analysis
I've selected a generic high carbon steel. I considered a factor of
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
with stronger bearings (titanium bearings?).


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


Mounting the Exhaust
---------------------

The next step within the fabrication process was to mount the exhaust.


.. image:: images/puch-maxi-swap/image_269062.jpg
   :alt: Build progress
   :class: pure-img


Because the exhaust was now mounted on the opposite side, I could not
reuse the existing mount. I had to create a new one.


.. image:: images/puch-maxi-swap/image_269063.jpg
   :alt: Build progress
   :class: pure-img


I 3D printed the following brackets, anticipating that they too would
be made out of 3D printed sheet cut metal.


.. image:: images/puch-maxi-swap/image_269064.jpg
   :alt: Build progress
   :class: pure-img


Here they are mounted to the frame.


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


2023-07-26
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
