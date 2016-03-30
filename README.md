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


