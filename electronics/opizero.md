<!-- TITLE: Opizero -->
<!-- SUBTITLE: A quick summary of Opizero -->

# ARMbian


```sh
git clone --depth 1 https://github.com/armbian/build
cd build
./compile.sh BOARD=orangepizero BRANCH=next RELEASE=buster BUILD_DESKTOP=no KERNEL_ONLY=no KERNEL_CONFIGURE=no
```

* KERNEL_ONLY (yes|no): leave empty to display selection dialog each time
set to “yes” to compile only kernel, u-boot and other packages for installing on existing Armbian system
set to “no” to build complete OS image for writing to SD card