
Kernel
======

More discussion about this can be found on

https://groups.google.com/forum/?fromgroups#!forum/renesas-emev-osp

Downloading
-------------------------

Kernel source code, based upon the 2.6.35.7 base version, is stored on a public GIT repository at:

 https://github.com/Renesas-EMEV2/Kernel

To download the complete source repository, the easiest way is to "clone" it in your local host:

	git clone git@github.com:Renesas-EMEV2/Kernel.git

(you need to have 'git' installed on your host first). This will create a Kernel/ sub-directory.

The following git branches exist in the repository, at present:

* Livall_JB: valid for an Android JellyBean (JB) build
* Livall_GB: valid for an Android GingerBread (GB) build
* emev-4.1 - Obsolete - for an Android JellyBean (JB) build
* MyPad - Obsolete - for Android GingerBread (GB) build

All of these branches include patches for Android and the Renesas Emma EV2 SoC platform drivers, but each differ for board-specific drivers and options. Before building a version valid for JB and a given board, you need to check the proper branch out, e.g.:

	cd Kernel
	git checkout Livall_JB

How to build
------------

You need an ARM EABI cross-compiler toolchain installed on your host, to build the kernel.

The Android Open Source Project (AOSP) comes with a gcc 4.4.3 toolchain included. If you downloaded the AOSP, you only have to included the AOSP toolchain in your PATH. E.g.:

	export PATH=<AOSP home>/prebuilt/linux-x86/toolchain/arm-eabi-4.4.3/bin:$PATH

See also https://github.com/Renesas-EMEV2/Documentation/blob/emev-4.1/Android.md, about downloading AOSP.

Though not mandatory, I'd suggest to use the same toolchain to build both the Android and the Kernel binaries.

To build the Kernel, just do:

	export CROSS_COMPILE=arm-eabi-  (or the prefix of your toolchain, if you use a different one)
	export ARCH=arm
	cd <kernel root dir>
	make emev_Livall_JB_defconfig    (see below for other possible configurations)
	make

To complete the build, the 'mkimage' tool is required. If you miss it on your host, install it with:

	sudo apt-get install uboot-mkimage

Configurations
--------------

We prefer not to branch new kernel versions on our git repository, unless we are going to move to a major kernel release, like 3.5, or significant changes are made to the same base version. Additional customizations on top of the base version, covering different board manufacturing and device peripherals, should be handled through confguration options. 

On top of a default configuration, something else could also be changed through the kernel standard tool 'make menuconfig', before building. For example, default configuration defines a touchscreen driver, but we have tablets mounting different touchscreens: e.g. PixCir or Goodix. You need to choose the proper driver before building.

The major default configurations in the "Livall_JB" branch are the following:

* emev_Livall_JB_defconfig

for a "Livall" tablet board and an Android JB build, with a PixCir "Tango M48" touchscreen driver selected by default. Note, the Goodix GT801 touchscreen driver code is present too and may be choosen with: 'make menuconfig' -> drivers -> input -> touchscreens, un-selecting PixCir and selecting Goodix.

* emev_Livall_upd_defconfig

for a Livall tablet board and used along cramfs Linux (Wind River) for firmware updates from SD-card. See also Bootloader docs about this (https://github.com/Renesas-EMEV2/Documentation/blob/emev-4.1/Bootloader.md)

* emev_Livall_GB_defconfig

for a "Livall" tablet board and PixCir touchscren driver, for an Android GB build.

The older "emev-4.1" branch include "emev_mypad_*" configurations, but they're not mantained anymore.



