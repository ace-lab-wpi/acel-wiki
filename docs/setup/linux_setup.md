# Development Setup: Linux

Consider forking the project on GitHub before proceeding with this procedure if you intend to contribute back to the project. (More details on this are at [Tracking Development with Git](https://dronin.readme.io/v20161004/docs/tracking-development-with-git))

## 1. Set up prerequisites for the build environment
### UBUNTU/MINT/DEBIAN BASED DISTRIBUTIONS
First ensure your package manager is up to date:
```
sudo apt-get update
```
Next, get a host compiler and other build tools, along with your revision control environment:
```
sudo apt-get install build-essential gdb wget debhelper ccache git
```
If you are running a 64-bit version of Linux (if you run uname -m and the output says x86_64 you are in a 64-bit environment), you'll also need to install 32-bit compatibility libraries.
```
sudo apt-get install gcc-multilib
```
Finally, install some additional libraries required to compile GCS
```
sudo apt-get install zlib1g-dev libusb-1.0-0-dev libudev-dev libgl1-mesa-dev
```
### FEDORA-BASED DISTRIBUTIONS
Install the required packages:
```
sudo dnf install libstdc++.i686 gcc-c++ ccache
sudo dnf install libusb-devel qt5-qtdeclarative-devel qt5-qtimageformats qt5-qtserialport-devel qt5-qtsvg-devel qt5-qtxmlpatterns-devel SDL-devel systemd-devel zlib-devel
```

## 2. Check out the dRonin repository and build
### CLONE THE SOURCE CODE REPOSITORY
First, clone the dRonin repository. Change to an appropriate directory to check out the code. If you have your own fork, specify its URL on the git command line (otherwise you can use the parent fork per the below example).
```
git clone git://github.com/d-ronin/dRonin.git
cd dRonin
```

### AUTOMATIC DOWNLOAD AND INSTALL OF REQUIRED PROGRAMS
The dRonin build environment is capable of installing the rest of the tools that it needs.

Qt build tools
Next, run make qt_sdk_install, copy the path from the output in your terminal and paste it into the installer when prompted.

```
 Do not install Qt to the default location!

When running the qt sdk install command, you'll be told where to install qt, then the GUI installer will open. Here is what it will look like:

*** NOTE NOTE NOTE ***
*
*  In the GUI, please use exactly this path as the installation path:
*        /some/path/src/dRonin/tools/Qt5.5.1
*
*** NOTE NOTE NOTE ***
Be sure to copy the specified path into the installer when prompted for the install location!
```
Arm cross compilation toolchain
This is easy. Just type: make arm_sdk_install

## 3. Build the software
You should be ready to go. Type make all to compile the entire project. Type make to see a list of possible make arguments.

## 4. Install udev rules
You need to grant permission for normal users (ie. not root) to access your flight-controller boards from the GCS. This is accomplished by installing specific udev rules for the various flight controller boards.

Check if your user is in the group "plugdev" by running 'groups'

 If you're not in group "plugdev"...

If you're not in the group "plugdev", you can add the group to your user by running this command:
```
sudo usermod -a -G plugdev user
```
Then, log-out and log back in and check again by running groups

Next, run these commands to install the dRonin udev rules:
```
sudo cp package/linux/deb/_package.udev /etc/udev/rules.d/45-dronin-permissions.rules
sudo udevadm control --reload-rules
```
## 4. Run GCS
Launch the gcs with ./build/ground/gcs/bin/drgcs and connect to / flash your board.
