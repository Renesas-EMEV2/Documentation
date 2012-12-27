
Kernel
======

More discussion about this can be found on

https://groups.google.com/forum/?fromgroups#!forum/renesas-emev-osp

Downloading
-------------------------

Kernel code, which is based upon the 2.6.35.7 kernel base version, patched for Android and the Renesas Emma EV2 SoC specific drivers, is stored on the GIT repository at:

 https://github.com/Renesas-EMEV2/Kernel

To download, the easiest way is:

	git clone git@github.com:Renesas-EMEV2/Kernel.git

The following valid branches exist here at present:

* MyPad: valid for Android GingerBread (GB) build
* emev-4.1: valid for an Android JellyBean (JB) build

So, for example, before building the version valid for JB, you need to check it out:

	git checkout emev-4.1

How to build
------------

You need an ARM EABI cross-compiler toolchain installed on your host, to build the kernel.

The Android Open Source Project (AOSP) comes with a gcc 4.4.3 toolchain included. If you downloaded the AOSP, you only have to have it included in your PATH. E.g.:

	export PATH=<AOSP home>/prebuilt/linux-x86/toolchain/arm-eabi-4.4.3/bin:$PATH

See also https://github.com/Renesas-EMEV2/Documentation/Android.md, about downloading AOSP.

Though not mandatory, I'd suggest to use the same toolchain to build both the Android and the Kernel binaries.

To build the Kernel just do:

	export CROSS_COMPILER=arm-eabi-  (or the prefix of your toolchain)
	export ARCH=arm
	cd <kernel root dir>
	make <config>  (see below for possible configurations)
	make

To complete the build, the 'mkimage' tool is required. If you miss it on your host, install with:

	sudo apt-get install uboot-mkimage

Configurations
--------------

We prefer not to branch new kernel versions on our git repository, unless we are going to move to a major kernel release, like 3.8 or newer. Additional customizations on top of this base version, covering different board manufacturing and device peripherals, should be handled through confguration options. 

The major default configurations defined for the Renesas EMEV platforms, up to now, are the following:

* emev_mypad_gb_defconfig

For a "Livall" tablet board, for an Android GB build, with a PixCir touchscren driver by default. Note, the Goodix GT801 touchscrewn driver code is present too and can be choosen with 'make menuconfig', selecting it from drivers-input-touchcreens and unselecting the PixCir one.

* emev_mypad_jb_defconfig

For a "Livall" tablet board, for an Android JB build, with a Goodix GT801 touchscreen driver by default. Note, the PixCir touchscreen driver code is present too and can be choosen with 'make menuconfig' selecting it from drivers-input-touchcreens and unselecting the Goodix one.

* emev_mypad_upd_defconfig

For a Livall tablet board, for a cramfs Linux (Wind River), used during firmware update from SD-card. See also Bootloader docs about this (https://github.com/Renesas-EMEV2/Documentation/Bootloader.md)




