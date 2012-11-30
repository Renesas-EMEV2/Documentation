
Kernel
======

More discussion about this can be found on

https://groups.google.com/forum/?fromgroups#!forum/renesas-emev-osp

How to build
------------

Have an arm EABI toolchain installed on your host.

Note - Android AOSP comes with a toolchain included.

	export CROSS_COMPILER=arm-eabi-  (or the prefix of your toolchain)
	export ARCH=arm
	make <config>  (see below for possible configurations)
	make

Repositories and branches
-------------------------

Kernel is stored under this GIT repo on:

https://github.com/Renesas-EMEV2/RenesasEV2-BSPGB-Kernel

The following valid branches exist here at present:

* MyPad: valid for Android GingerBread (GB) build
* emev-4.1: valid for an Android JellyBean (JB) build

Both are based upon the 2.6.35.7 kernel base version, patched for Android and the Renesas Emma EV2 SoC specific drivers.

Configurations
--------------

We prefer not to branch new kernel versions, unless we are going to move to a major kernal release, like 3.8 or newer. Additional customizations on top of this base version, covering different board manufacturing and device peripherals, should be handled through confguration options. 

The major default configurations defined for the Renesas EMEV platforms, up to now, are the following:

* emev_mypad_gb_defconfig

For a "Livall" tablet board, for Android GB build, with PixCir touchscren driver. Note, the Goodix GT801 touchscrenn driver code is present and can be choosen with 'make menuconfig', selecting it from drivers-input-touchcreens and unselecting the PixCir one.

* emev_mypad_jb_defconfig

For a "Livall" tablet board, for Android JB build, with GT801 touchscreen driver. Note, the PixCir touchscrenn driver code is present and can be choosen with 'make menuconfig' selecting it from drivers-input-touchcreens and unselecting the Goodix one.

* emev_mypad_upd_defconfig

For a Livall tablet board, for a cramfs Linux (Wind River), used during firmware update from SD-card.
See also Bootloader docs.




