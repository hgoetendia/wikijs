<!-- TITLE: Opizero -->
<!-- SUBTITLE: A quick summary of Opizero -->

# ARMbian

## Build
```sh
git clone --depth 1 https://github.com/armbian/build
cd build
./compile.sh BOARD=orangepizero BRANCH=next RELEASE=buster BUILD_DESKTOP=no KERNEL_ONLY=no KERNEL_CONFIGURE=no
```

* BRANCH (default|next|dev): you can set kernel and u-boot branch manually to skip dialog prompt; some options may not be available for all devices

* RELEASE (stretch|jessie|bionic|xenial): you can set OS release manually to skip dialog prompt; use this option with KERNEL_ONLY=yes to create board support package

* BUILD_DESKTOP (yes|no):
set to “yes” to build image with minimal desktop environment
set to “no” to build image with console interface only

* KERNEL_ONLY (yes|no): leave empty to display selection dialog each time
set to “yes” to compile only kernel, u-boot and other packages for installing on existing Armbian system
set to “no” to build complete OS image for writing to SD card

* KERNEL_CONFIGURE (yes|no):
leave empty to display selection dialog each time
set to “yes” to configure kernel (add or remove modules or features). Kernel configuration menu will be brought up before compilation
set to “no” to compile kernel without changing default or custom provided configuration


## Install in SD Card


```sh
sudo dd bs=1M if=/home/xxx/armbian/build/output/images/Armbian_5.91_Orangepizero_Debian_buster_next_4.19.57.img of=/dev/sdc conv=fdatasync
```

* fdatasync - physically write output file data before finishing
* fsync - likewise, but also write metadata
* dsync - use synchronized I/O for data
* sync - likewise, but also for metadata

