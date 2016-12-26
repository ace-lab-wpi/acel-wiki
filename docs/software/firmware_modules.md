# Firmware Modules

## Overview of Available Modules #

The current list of modules (with documentation) is:

* [Autotune](./autotune.md)
* [GenericI2CSensor]() (to be added)

**Note**: Not all modules are present in all firmware images.

Modules are included in a firmware image when it is listed in the `MODULES` or `OPTMODULES` list in the Makefile for the board firmware (see `./flight/targets/<board>/Makefile`).

Modules listed in the `MODULES` list are called Built-in.  Modules listed in the `OPTMODULES` list are called Optional.

## Using Existing Modules #

### Module Settings ##

The `ModuleSettings` UAVO is read by the firmware **only once** during board initialization.  The fields in this UAVO control the behaviour of the modules included in the firmware build.

**Note**: This UAVO may include settings for modules that are not present in the firmware.

**Note**: Some modules may require additional configuration before being able to start.

**Note**: Changes to the `ModuleSettings` UAVO only take effect on the next reboot of your board.

### Optional Modules ##

Optional modules are built into a firmware image but do not run by default.  Optional modules only run when they are explicitly enabled in the `ModuleSettings.State` UAVO field.

In many cases, an optional module will have a dedicated config tab in the GCS which will take care of enabling the module on the next boot.

Optional modules may be enabled by setting the relevant entry in the `ModuleSettings.State` field to `Enabled`.

### Built-in Modules ##

Built-in modules will be started automatically during firmware initialization.

**Note**: Even built-in modules may requre additional configuration before being able to start.

## Adding a New Module (Developer) #

Here is a rough outline of what you'll need to do to create a new module and add it to a firmware image:
* Create the new module directory
  * `./flight/Modules/<module-name>`
  * The <module-name> is typically written in CamelCase and should consist of only upper and lower-case letters.
* Create one or more .c files that implement the code for your module
  * `./flight/Modules/<module-name>/*.c`
  * Find another module that you can use as a basis for your new module
* Add the new module to `./flight/targets/<board>/fw/Makefile`
  * Add your new module to the `MODULES` or `OPTMODULES` list
* Add an entry for your module to the `ModuleSettings` UAVO
  * see `./shared/uavobjectdefinition/modulesettings.xml`
  * module should be added to the `ModuleSettings.State` field
  * any module-specific settings should be added as new fields
* Add your module's task (if any) to the `TaskInfo` UAVO
  * see `./shared/uavobjectdefinition/taskinfo.xml`
  * only required if your module has a task (most do)
