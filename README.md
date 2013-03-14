Documentation
=============

Documentation for Open Source projects on the Renesas EMEV2 platform.

More discussion about this can be found on

https://groups.google.com/forum/?fromgroups#!forum/renesas-emev-osp

Basic build steps
=================

1) Setup up your system with all required tools, download our customized AOSP code and build, as explained in:

 https://github.com/Renesas-EMEV2/Documentation/blob/emev-4.1/Android.md

2) Download Kernel code, choose branch, configuration and build, as explained in:

 https://github.com/Renesas-EMEV2/Documentation/blob/emev-4.1/Kernel.md

3) Download bootloader code, as explained in:

 https://github.com/Renesas-EMEV2/Documentation/blob/emev-4.1/Bootloader.md

4) Package the Android file system:

    cd <AOSP home dir>/device/renesas/emev
    ./pack.sh <bootloader home dir>/fwupd/files

5) Prepare the firmware updater SD-card:

    cd <bootloader home>/fwupd
    ./fwupd <SD card root dir>


