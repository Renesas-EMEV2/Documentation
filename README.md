Documentation
=============

Documentation for Open Source projects on the Renesas EMEV2 platform.

More discussion about this can be found on

https://groups.google.com/forum/?fromgroups#!forum/renesas-emev-osp

Basic BUILD steps
=================

* Follow instructions to setup your env, download and build AOSP, as in 

 https://github.com/Renesas-EMEV2/Documentation/Android.md

* Follow instructions to download and build Kernel, as in 

 https://github.com/Renesas-EMEV2/Documentation/Kernel.md

* Follow instructions to download Bootloader, as in 

 https://github.com/Renesas-EMEV2/Documentation/Bootloader.md

* Package the Android file system

	cd <AOSP home dir>/device/renesas/emev
	./pack.sh <bootloader home dir>/fwupd/files

* Prepare the firmware updater SD-card

	cd <bootloader home>/fwupd
	./fwupd <SD card root dir>
