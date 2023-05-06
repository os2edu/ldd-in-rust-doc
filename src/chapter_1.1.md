# Chapter 1

- Qemu GitHub 网址：<https://github.com/qemu/qemu>
- Qemu 使用手册：<https://www.qemu.org/docs/master/system/index.html>

1. 安装qemu:

    ```shell
    git clone https://git.qemu.org/git/qemu.git --depth 1
    ```

2. 安装依赖:

    ```shell
    sudo apt install ninja-build
    sudo apt install build-essential
    sudo apt install pkg-config
    sudo apt-get install libglib2.0-dev
    sudo apt-get install libpixman-1-dev
    ```

3. 将Qemu加入路径

    ```shell
    export PATH=(your path):$PATH
    ```

4. 设置Qemu编译生成的目标为RISC-V，AArch64，X86

      ```shell
      ./configure --target-list=aarch64-softmmu
      ```

     - 如果需要配置多个目标，可在target-list=后面添加，并以逗号分隔，例如：

      ```shell
      ./configure --target-list=aarch64-softmmu,riscv64-softmmu,x86_64-softmmu
      ```

      ![result](assert/task1.2.png)

    - 其他可生成的目标：

      ```shell
      set target list (default: build all) Available targets: aarch64-softmmu alpha-softmmu arm-softmmu avr-softmmu cris-softmmu hppa-softmmu loongarch64-softmmu m68k-softmmu microblaze-softmmu microblazeel-softmmu mips-softmmu mips64-softmmu mips64el-softmmu mipsel-softmmu nios2-softmmu or1k-softmmu ppc-softmmu ppc64-softmmu riscv32-softmmu riscv64-softmmu rx-softmmu s390x-softmmu sh4-softmmu sh4eb-softmmu sparc-softmmu sparc64-softmmu tricore-softmmu x86_64-softmmu xtensa-softmmu xtensaeb-softmmu
      ```

5. 编译

``` shell
make
```

![result](assert/task1.2.png)

- Qemu for RISC-V
- Qemu for AArch64
- Qemu for X86
