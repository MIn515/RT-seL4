# RT-seL4

seL4 kernel from https://github.com/seL4/seL4

Build Instruction
=================

In the `RT-seL4` folder

(1) Build RISC-V toolchain

Build multilib RISC-V toolchain configured with "--with-arch=rv64imafdc --with-abi=lp64 --enable-multilib" flags

```
git submodule update --init --recursive
cd riscv-gnu-toolchain
export SEL4RISCV=../riscv
./configure --prefix="${SEL4RISCV}" --with-arch=rv64imafdc --with-abi=lp64 --enable-multilib
# for seL4 kernel
make
# for FIMI-TEE SDK
make linux
```

(2) Clone seL4 (10.1.1) and apply patch for Keystone

```
cd ..
repo init -u https://github.com/seL4/sel4test-manifest.git -b refs/tags/10.1.1
repo sync
patch -d kernel -p0 < seL4_kernel_keystone.patch
```

(4) Build seL4 runtime with vault.sh script

Open `vault.sh` and change OUTPUT_DIR to your `<build_dir>/overlay/root`.

```
./vault.sh
```

The script will create `build/binary-files` directory.



