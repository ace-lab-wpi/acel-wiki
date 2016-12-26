# Build and Debug GCS using Qt Creator

It is possible to use Qt Creator to build and debug GCS.
You should open the /ground/ground.pro project file with Qt Creator. The next step is to set the shadow library and change the build directory to /build/ground.

[Qt Creator](http://s21.postimg.org/vot5kpad3/taulabsqtcreator.png)

NOTE
If you get an error related to "backendcapabilities.h: No such file or directory" change line #include "backendcapabilities.h" to #include "phonon/backendcapabilities.h"


WINDOWS NOTES

You may need to run Creator as admin.

Make sure Creator can find your Python27 install (i.e. put it in system path).
