
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

Repositories
------------

Kernel is stored under this GIT repo on:

https://github.com/Renesas-EMEV2/RenesasEV2-BSPGB-Kernel

Branches
--------

* MyPad: valid for Android GingerBread (GB) build
* emev-4.1: valid for an Android JellyBean (JB) build

Configurations
--------------

* emev_mypad_gb_defconfig

For a "Livall" tablet board, for Android GB build, with PixCir touchscren driver.

* emev_mypad_jb_defconfig

For a "Livall" tablet board, for Android JB build, with Goodix (GT801) touchscreen driver.

* emev_mypad_upd_defconfig

For a Livall tablet board, for a cramfs Linux (Wind River), used during firmware update from SD-card.
See also Bootloader docs.




