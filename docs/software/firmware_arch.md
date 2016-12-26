# Architecture Overview

There are a few core concepts required to understand Tau Labs software, and especially the firmware side.

## Modules

**flight/Modules**

[Modules](./firmware_modules.md) are the core logical units on the firmware side. They are generally fairly compact logical components of the flight software, such as a module to get sensor data, or a module to estimate the attitude. Modules can only communicate either via drivers calls (PiOS) or by getting and setting data via UAVObjects.

## PiOS

**flight/PiOS**

PiOS (Pilot Operating System) is the hardware abstraction layer. It is divided into two main sections. The **flight/PiOS/STM32Fxx** sections which are hardware specific (currently only supporting STM32 F1, F3, and F4 series processors).  The **flight/PiOS/Common** directory contains drivers that run on all platforms via the hardware specific platforms.  PiOS contains all the [[drivers|Development Drivers]] for external sensor chips, PWM generation and input, PPM, serial communications, etc.

## UAVObjects

**shared/uavobjectdefinition**

Details on adding a new UAVObject can be found [here](../tutorials/create_new_uavobjects.md)

UAVObjects are the data (and setting) representation used on both the firmware side and the GCS side.  They are implemented as data structures generated dynamically from xml definitions. These data objects are transferred from the firmware side to the ground control side and also used for inter-module communication on the firmware.

On the firmware side these interface via FreeRTOS primitives such as queues. Modules can block on updates from an object, so that when another module performs an update the first module resumes. Based on the meta data for that object, updates may be transferred to the ground control system with different frequencies.

The eventdispatcher ( **flight/UAVObjects/eventdispatcher** ) is responsible for performing these updates and handling the FreeRTOS interface as well as storage in the UAVObjectManager ( **flight/UAVObjects/uavobjectmanager** ).  The telemetry module performs the updates to the ground control system ( **flight/Modules/Telemetry/telemetry** ).

## UAVTalk

**flight/UAVTalk**

[UAVTalk](./uavtalk_protocol.md) is the protocol used to serialize UAVObjects, as well as send updates or request updates.
