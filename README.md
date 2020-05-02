# B4
Build your own Beagle Bone Black.

1. Build your own u-boot
2. Build your own kernel
3. Build your own busybox

**1. Build your own u-boot**

1.1  Get the latest toolchain for cross-compiling.

https://releases.linaro.org/components/toolchain/binaries/latest-7/arm-linux-gnueabihf/


1.2  Install packages for dependencies before compiling (Debian/Ubuntu).

```
sudo apt-get install u-boot-tools gawk wget git diffstat unzip texinfo gcc-multilib build-essential \ 
chrpath socat libsdl1.2-dev xterm picocom ncurses-dev lzop git libncurses5-dev perl
```

1.3  Get the latest u-boot source code.

```
git clone https://gitlab.denx.de/u-boot/u-boot.git
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


