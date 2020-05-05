# B4
Build your Beagle Bone Black.

1. Build u-boot
2. Build kernel
3. Build rootfs

**1. Build u-boot**

1.1  Get the latest toolchain for cross-compiling (Debian/Ubuntu).

```
https://releases.linaro.org/components/toolchain/binaries/latest-7/arm-linux-gnueabihf/
```

1.2  Install packages for dependencies before compiling (Debian/Ubuntu).

```
sudo apt-get install u-boot-tools gawk wget git diffstat unzip texinfo gcc-multilib build-essential \ 
chrpath socat libsdl1.2-dev xterm picocom ncurses-dev lzop git libncurses5-dev perl
```

1.3  Get the u-boot from TI repository

```
git clone git://git.ti.com/ti-u-boot/ti-u-boot.git uboot
cd uboot/
git checkout ti-u-boot-2020.01
git checkout -b MyBranchName
```

1.4  Configure .config file for Beagle Bone Black (am335x) and compile.

```
make distclean
make am335x_evm_config
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf-
```

1.5  Backup the outputs.
```
MLO
tools/mkimage
u-boot.img
```

**2. Build kernel**

2.1  Get the kernel from TI repository.

```
git clone git://git.ti.com/ti-linux-kernel/ti-linux-kernel.git linux
cd linux/
git checkout ti-linux-4.9.y 
git checkout -b MyBranchName
```
2.2  Configure config file for Beagle Bone Black (am335x) and compile kernel.

```
make ARCH=arm omap2plus_defconfig
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf-
```
2.3  Backup the outputs.

```
arch/arm/boot/zImage
arch/arm/boot/dts/am335x-boneblack.dtb
```

**3.  Build rootfs (with buildroot)**

3.1  Get the buildroot source code from repository.

```
git clone git://git.busybox.net/buildroot
cd buildroot/
git checkout -b 2020.02
```
3.2  Configure buildroot for BBB and compile.

```
make beaglebone_defconfig
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf-
```

3.3  Backup the outputs.

```
output/images/rootfs.tar
```

Using buildroot alone generates all the required items such as MLO, u-boot.img, zImage, am335x-boneblack.dtb and rootfs.tar to start up BBB. As we do, you may apply the items separately. Hereby we use output rootfs.tar from buildroot, other items are provided by kernel and u-boot build outputs.

**References**
1. TI Beagle Bone - http://www.ti.com/tool/PROCESSOR-SDK-AM335X
2. TI SDK documentation - http://software-dl.ti.com/processor-sdk-linux/esd/docs/latest/linux/index.html
3. itdev building Beagle Bone - https://www.itdev.co.uk/blog/building-linux-kernel-cross-compiling-beaglebone-black
4. UcanLinux (Turkish) - http://www.ucanlinux.com/eski-blog-yaz%C4%B1lar%C4%B1
5. Mehmet Alınbay Gömülü Linux Notları (Turkish) https://linux-readdocs.readthedocs.io/en/latest/index.html




