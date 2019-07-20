<!-- TITLE: Opizero -->
<!-- SUBTITLE: A quick summary of Opizero -->


# Orange pi zero
![Screenshot From 2019 07 11 04 53 27](/uploads/electronics/screenshot-from-2019-07-11-04-53-27.png "Screenshot From 2019 07 11 04 53 27")


![Screenshot From 2019 07 11 04 50 30](/uploads/electronics/screenshot-from-2019-07-11-04-50-30.png "Screenshot From 2019 07 11 04 50 30")


# OrangePi Build System
https://github.com/orangepi-xunlong/OrangePi_Build

OS base: ubuntu-18.04.2-desktop-amd64.iso


```sh
git clone https://github.com/orangepi-xunlong/OrangePi_Build.git
cd OrangePi_Build
./Build_OrangePi.sh

```

Choose Orange Pi Zero


```sh
cd OrangePiH2

```

edit OrangePiH2/scripts/uboot_compile.sh

Replace this line

```sh
#CORES=$((`cat /proc/cpuinfo | grep processor | wc -l` - 1))
CORES=1
```


Backup the uboot/Makefile


Replace uboot for https://github.com/friendlyarm/h3_lichee/tree/master/brandy/u-boot-2011.09  or download from [Uboot](/uploads/electronics/uboot.tgz "Uboot") 

`****Update*** only replace main/*.lds files`

then replace this lines in  uboot/arch/arm/config.mk

```text
#CROSS_COMPILE ?= $(CURDIR)/../toolchain/gcc-arm/bin/arm-linux-gnueabi-
CROSS_COMPILE ?= $(CURDIR)/../toolchain/bin/arm-linux-gnueabi-

```

Replace the backuped the uboot/Makefile for the backuped one.



```sh
sudo apt purge qemu-user-static
sudo apt install qemu-user-static
```

Create eth0 config file:

OrangePiH2/output/rootfs/etc/network/interfaces.d/eth0

Like this


```text
auto eth0
iface eth0 inet static
        address 192.168.0.110
        netmask 255.255.255.0
        gateway 192.168.0.1
        dns-nameservers 8.8.8.8

```



Then:

```sh
./build.sh
```








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



