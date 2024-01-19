# RT-seL4
https://github.com/seL4/seL4


Build Instruction
===============================

(1) Build RISC-V toolchain

Build multilib RISC-V toolchain configured with "--with-arch=rv64imafdc --with-abi=lp64 --enable-multilib" flags



(2) Clone seL4 (10.1.1) and apply patch for Keystone 

```
repo init -u https://github.com/seL4/sel4test-manifest.git -b refs/tags/10.1.1
repo sync
patch -d kernel -p0 < seL4_kernel_keystone.patch
```

(4) Build seL4 runtime with vault.sh script

Open `vault.sh` and change OUTPUT_DIR to your `<build_dir>/overlay/root`.

```
./vault.sh
```

The script will create `sel4test` directory under the overlay directory.
You can insert the driver, and run `./sel4test.ke` to run seL4 tests.
