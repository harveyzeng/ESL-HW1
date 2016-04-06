# ESL-HW1
Assignment: RISC-V Tool Chain Building & Linux Booting

#1. Build RISC-V Gnu tool chain and test it with a simple "Hello World" C program.


First, clone the tools from the riscv-tools GitHub repository:

    $ git clone https://github.com/riscv/riscv-tools.git

    $ cd $TOP/riscv-tools

    $ git submodule update --init --recursive

Install the related library

    $ sudo apt-get install autoconf automake autotools-dev curl libmpc-dev libmpfr-dev libgmp-dev gawk build-essential bison flex texinfo gperf libtool patchutils bc

Set library path

    $ export RISCV=$TOP/riscv

    $ export PATH=$PATH:$RISCV/bin

Build RISC-V Gnu tool chain

    $ ./build.sh

Testing Your Toolchain

    $ cd $TOP

    $ echo -e '#include <stdio.h>\n int main(void) { printf("Hello world!\\n"); return 0; }' > hello.c

    $ riscv64-unknown-elf-gcc -o hello hello.c

    $ spike pk hello

the outcome is the hello_world.png


#2. Download Linux and build it with RISC-V g++ compiler

First, clone the tools from the riscv GitHub repository:

    $ git clone https://github.com/riscv/riscv-tools.git

    $ cd $TOP/riscv-tools

    $ git submodule update --init

Install the related library

    $ sudo apt-get install autoconf automake autotools-dev curl libmpc-dev libmpfr-dev libgmp-dev gawk build-essential bison flex texinfo gperf libtool patchutils bc

Set library path

    $ export RISCV=$TOP/riscv

    $ export PATH=$PATH:$RISCV/bin

Run the build script

    $ ./build-spike-only.sh

#Building riscv64-unknown-linux-gnu-gcc

Enter the riscv-gnu-toolchain directory and run the configure script to generate the Makefile.

    $ ./configure --prefix=$RISCV

Run this command to start the build process:

    $ make linux

#Building the Linux Kernel

    $ cd $TOP

    $ git clone https://github.com/riscv/riscv-linux.git linux-3.14.33

    $ curl -L https://www.kernel.org/pub/linux/kernel/v3.x/linux-3.14.33.tar.xz | tar -xJkf -


#Configuring the Linux Kernel

    $ make ARCH=riscv defconfig

    $ make -j16 ARCH=riscv

# Building BusyBox






the outcome is the linux.png









#reference
1.http://coldnew.github.io/blog/2015/busybox_for_riscv_on_qemu/

2.https://github.com/riscv/riscv-tools











