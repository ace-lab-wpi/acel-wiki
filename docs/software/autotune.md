# Introduction to Autotune

Autotune is an exciting feature originally developed on TauLabs and thoroughly improved in dRonin. The concept is to let the aircraft perform a calibration routine and try to come up with sane stability values without any user configuration.

With this module one can reconfigure his airframe in the field and perform an autotune on the spot to give a solid flying platform without manually trying to retune values for optimal performance.

Autotune used to be a complex step by step procedure, it has now reached a level of simplicity that makes documentation unnecessary. This page is mainly present to state how simple autotune is and to encourage anyone to try it without loosing to much time on the numerous deprecated procedures that can be find elsewhere and applicable to old OpenPilot or even Taulab.

### Warning

* Only Roll and Pitch are automatically tuned, for yaw tuning you will have to post/share your tunes (see below).
* Currently this feature is intended for Multirotor Aircraft ONLY!
* This plugin uses lots of resources. On CC3D boards, you should disable other modules (such as TxPID) before activating autotune, and use less than 5 inputs, preferably in PPM mode. PWM and DSM do use more resources.
* This plugin is going to make your aircraft shake, etc, so test with some reasonable space.  
* Once again: perform this operation in an open and safe environment, the aircraft is likely to gain altitude when the test starts and shed altitude when it ends (approx. 1m).
* If your original PIDs are totally wrong, the aircraft is likely to shake a lot during the process. The better the aircraft flies before autotune, the less it will shake during the autotune process.

## Autotune Process

To use autotune, here are the steps:

### Add Autotune to the Flight Mode switch
* On the GCS Configuration page, select the Input section.
* In the Input section, select the Flight Mode Switch Settings tab.
* Set one of the Flight Mode Switch Positions settings to Autotune in the pull-down menu.
* Click “Save”

### Enable Autotune
* On the GCS Configuration page, select the Autotune section.
* In the Autotune section, select the Pre-Autotune tab and check the “Enable Autotune Module” box.
* Click “Save”.
* Power cycle your board, i.e disconnect both battery & USB!

### Autotune the flight controller
* Before you start Autotune, make a note of your current PID settings, you'll need these settings to compare them with the calculated values.
* Take off normally and hover
* Activate Autotune by moving Flight Mode switch into the selected position.
* The aircraft will gain altitude and begin to oscillate.  Each axis takes approximately 30 seconds to calibrate, so expect this oscillation behaviour to last around 60 seconds.
* Use your normal control inputs to maintain a hover in the general area, but try to minimize control inputs to the degree this is practical. The aircraft will stop oscillating and descend when Autotune cycle is complete.
* With the craft still in Autotune mode, land the aircraft normally and disarm the flight-controller (this saves the calculation).
* Check the controller is properly DISARMED, and shut-off the aircraft

Note that unlike Taulabs and early pre-release, your autotune calculations are Saved! To do so, disarm while in autotune mode. On the contrary, if you change flightmode without disarming, autotune values will be discarded. Note2 in future release the settings could/will be saved as soon as the autotune has been fully completed (no need to disarm). To be confirmed...

For the record in Taulabs or early pre-release one had to leave the aircraft powered and maintain the flightmode to autotune otherwise Autotune calculations would have been lost. Older Taulab/OpenPilot documentation do reflect this and are crowded with complex procedures and safety measures aimed at not deleting the autotune data. dRonin autotune is much more simple in every way.

### Verify and apply the settings
* Connect the flight controller to the GCS
* On the Configuration page, select the Autotune section.
* Look at the “Computed Values” and compare them to your previous PID settings.
* Move the damping and sensitivity slider so as to adjust the computed values to your flying style.
* If the computed values are vastly different than the settings you were previously using, only use these new settings with caution.
* If the Tau values are reported to big, just try another autotune without any outside wind turbulence to see if the Tau gets better. If the Tau still remains high (> 0.05), you will probably have to reduce the damping value.
* If you want to save the settings generated with Autotune to the board, click the “Apply Computed Values” button. This will apply the computed values in the [stabilization] tab. Note: your settings are not already saved on the flight controller yet.
* Move to [stabilization], check the values again and click the “Save” button.

### Fine tune
* Go back to the field and test the aircraft with your favourite flight mode, DO NOT ACTIVATE the autotune flightmode as you could reset the previously calculated settings!
* If you do not like the feel, just get back to the GCS, and adjust the damping / noise settings, until the behaviour suits your flying style. You can just repeat this damping/sensitivity adjustment as many time as necessary, with this respect dRonin is much more comprehensive than earlier OpenPilot & Taulab firmware (not presuming the progress on Taulab as of 2016 though).
* Once everything is satisfactory, just share your autotune results! As a bonus you'll get a guideline for Yaw fine tuning!

### Disable Autotune
* Remove Autotune from your Flight Mode switch.
* Disable Autotune by selecting the Pre-Autotune tab and unchecking the “Enable Autotune Module” box.
* Click the “Save” button.
* Power cycle your board, i.e disconnect both battery & USB.

Further readings : [PIDs Tuning by R. James Cotton](https://github.com/d-ronin/dRonin/raw/next/flight/Doc/Autotuning%20Derivation.pdf)
