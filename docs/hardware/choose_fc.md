# Choose a flight controller for dRonin

dRonin supports many different flight controller boards. Which one you choose depends on your model, the capabilities you want, and your budget. You can build a quadcopter or a plane for less than $60 using the most affordable boards, or you can spend $100 on the flight controller alone.

## Supported controllers

### STM32F4 Controllers
These boards support all features (subject to hardware limitations).
* [BrainFPV](http://brainfpv.com/) Small and light with integrated OSD
* [BrainFPV RE1](http://brainfpv.com) Next generation BrainFPV
* [AeroQuad32](http://aeroquad.com/showwiki.php?title=AeroQuad32-Flight-Control-Board-v2)
* [[Sparky2]] - more powerful version of Sparky1 with integrated radio.
* [[Revolution|RevoMini]] - OpenPilot Revolution board.
* [Quanton](http://www.quantec-networks.de/shop/en/quanton/1/quanton-flight-control-rev.-1) - Powerful platform with large amounts of connectivity including 8 PWM in and 8 PWM out, and four serial ports.
* [Gemini](http://www.team-blacksheep.com/products/prod:gemini) - Mini FPV hex racer from Team Black Sheep that uses the Colibri flight controller, a derivative of the Quanton

### STM32F3 Controllers
These boards support all features except PicoC scripting (subject to hardware limitations).
* [Lumenier LUX](http://www.getfpv.com/lumenier-lux-flight-controller.html) F3 based flight controlled for FPV racing.
* [[Sparky]] - Small single sided flight controller. Fully supported.
* DTFc Integrated PDB board from DTFUHF

These boards are not supported!
* SPRF3 (a.k.a seriously pro racing F3): the hardware is more than often poor and cannot be flashed easily ( see [dronin on sp f3 flight controller](https://forum.dronin.org/forum/d/239-dronin-on-sp-f3-flight-controller) )

### STM32F1 Controllers
These boards support only a limited feature set. Navigation is not supported.
* [[OpenNaze/Naze32|OpenNaze Naze32]] - Popular platform, basic support, can't yet be flashed from GCS. dRonin also works on Naze32-based brushed flight controllers such as the Quanum Pico/Micro Scisky32.
* [CC3D](http://www.openpilot.org/products/openpilot-coptercontrol-platform/) - Popular older platform, easy to setup and well documented, see [[Getting started|Configuring-your-new-board-for-basic-flight]]

## Popular setups

### To build a micro brushed multicopter

The easiest way to build a micro brushed multicopter is with a board that has integrated brushed motor drivers, and can run on 1S batteries (3.7V) without additional equipment. Some of these boards even integrate a radio receiver or transceiver.

For the easiest build, you'll want a board with at least four integrated brushed motor drivers, unless you're using an external brushed motor driver. Your choices are many.  You can go with the Brushed Sparky2, which is the only brushed STM32F4 flight controller on the market. It supports all dRonin features including navigation if you add a GPS. If you want a more affordable board, like one of the numerous Naze32-based flight controllers listed below.

Here should be a brushed micro board comparison table.
* The [Brushed Sparky2](http://buildandcrash.blogspot.fr/2015/03/brushedsparky-v02.html) has an integrated OpenLRS 433MHz transceiver and STM32F4, as well as powerful FETs.
* The [Quanum Pico (a.k.a Micro Scisky 32)](http://www.hobbyking.com/hobbyking/store/__86503__Quanum_Pico_32bit_Brushed_Flight_Control_Board.html) has an integrated DSM2 receiver and is very affordable.
* The [BBB32 (a.k.a Beef's Brushed Board)](http://fisselrc.com/BBB32/rev1/BBB32v1_user_guide.html)

There are others that should work, like NANO-B-FC and LulFro.

### To build a brushless multicopter

While you can build a larger multicopter with a basic STM32F1 board like the Naze32 or CC3D, it is preferable that you use a STM32F4 or STM32F3 board for better performance and access to the full features of dRonin.

If you want to build an FPV multicopter, the BrainFPV is probably the best choice, as there is an integrated OSD. If you don't require the integrated OSD, two great boards are the Sparky2 and the Revolution. Of course, dRonin will work great on any of the supported STM32F4 boards.
