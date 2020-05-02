# B4
Build your own Black Bone Black.

1. Build your own u-boot.

Get the latest toolchain for cross-compiling.

https://releases.linaro.org/components/toolchain/binaries/latest-7/arm-linux-gnueabihf/

Install packages for dependencies before compiling.

sudo apt-get install gawk wget git diffstat unzip texinfo gcc-multilib build-essential chrpath socat libsdl1.2-dev xterm picocom ncurses-dev lzop git libncurses5-dev perl

Get the latest u-boot source code.

git clone https://gitlab.denx.de/u-boot/u-boot.git

Configure .config file for Black Bone Black (am335x) and compile.

make distclean
make am335x_evm_config
ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- make
