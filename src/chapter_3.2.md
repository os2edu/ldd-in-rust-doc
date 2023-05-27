# 任务一：R4L e10000 网卡驱动代码内核模块编译

- 米明恒代码： <https://github.com/myrfy001/r4l-e1000>
- 肖络元代码： <https://github.com/rcore-os/e1000-driver> <https://github.com/elliott10/e1000-driver/tree/dev/src>
- 陈乐代码： <https://github.com/rcore-os/nvme_driver>

## linux 内核下载

代码地址： <https://github.com/os2edu/rust-for-linux-6.1> （目前驱动可以在这个内核运行）

下载、解压后进入，查看 Documentation/rust/quick-start.rst 可以看到开启内核里 Rust 支持的一些先决条件

```shell
# 1. 指定 rustc 版本：
rustup override set $(scripts/min-tool-version.sh rustc)

# 2. 添加 rust 源码
rustup component add rust-src

# 3. libclang：从 https://releases.llvm.org/download.html 下载最新编译好的内容，将 bin 文件夹加入环境变量

# 4. 指定 binggen 版本：
cargo install --locked --version $(scripts/min-tool-version.sh bindgen) bindgen

# 5. 其余内容在安装 rust 时都已自动安装

# 6. 检查依赖是否满足
make LLVM=1 rustavailable
```

## 内核配置

```shell
# 1. 选择基本环境，当前版本内核支持的并不宽泛，x86_64 和 arm64（aarch64）的限制少：
make x86_64_defconfig
# 2.1 General setup ->
#       [*] Rust support
# 2.2 Kernel hacking ->
#       [*] Sample kernel code ->
#           [*] Rust samples ->
#               [*] Minimal
# 2.3 Device Driver ->
#   Network device support ->
#     Ethernet driver suppart ->
#      Intel devices ->
#        <*> Intel(R) PRO/100+ support
#        <M> Intel(R) PRO/100 Gigabit Ethernet support
#        <*> Intel(R) PRO/1000 PCI-Express Gigabit Ethernet support
make LLVM=1 menuconfig
# 3. 编译
make LLVM=1
```

为了保证顺利加载驱动模块需要将 busybox 重新编译与内核架构一致

进入 BusyBox 源代码所在的目录

```shell
make clean
```

生成默认的 .config 文件：

```shell
make defconfig
```

运行 `make menuconfig`

```shell
make menuconfig
```

在菜单界面中，找到以下选项：

```
Busybox Settings  --->
    Build Options  --->
```

选中 Build BusyBox as a static binary (no shared libs)，然后按 Y 键。这将确保 BusyBox 静态链接，使其在不同系统上更容易运行。

保存配置并退出 menuconfig。

编译 BusyBox：

```shell
make
```

安装 BusyBox：

```shell
make install
```

这将在 \_install 子目录中创建一个包含 BusyBox 可执行文件和符号链接的文件系统。然后将 BusyBox 的二进制文件复制到适当的目录，以便在您的环境中使用。

## r4l e1000 驱动模块下载

```shell
git clone https://github.com/myrfy001/r4l-e1000.git
```

注意 build_image 脚本，需要根据你的电脑更改相应的路径。

例如：

```shell
set -e

# Build the kernel module
make -C ~/rust-for-linux-6.1 M=$PWD LLVM=1 CLIPPY=1

# Copy the build kernel module to the rootfs folder, there should be a usable busybox at `rootfs` folder
cp ./r4l_e1000_demo.ko ../rootfs

# Build the rootfs image
pushd ../rootfs && \
find . | cpio -o --format=newc > ../rootfs.img && \
popd


# Run QEMU to test the kernel, the network traffic will be dumped to `dump.dat` and you can use wireshark to explore the result.
qemu-system-x86_64 \
-netdev "user,id=eth0" \
-device "e1000,netdev=eth0" \
-object "filter-dump,id=eth0,netdev=eth0,file=dump.dat" \
-kernel ../rust-for-linux-6.1/arch/x86/boot/bzImage \
-append "root=/dev/ram rdinit=sbin/init ip=10.0.2.15::10.0.2.1:255.255.255.0 console=ttyS0" \
-nographic \
-initrd ../rootfs.img
```
