# 第二阶段：Linux 6.1 in Qemu 验证（5.8-5.20）

此阶段重点放在 Linux 6.1 内核的编译，不需要引入 rust4linux，尽量配置为 AArch64。

Qemu 支持的树莓派板子: <https://www.qemu.org/docs/master/system/arm/raspi.html>

`raspi0` and `raspi1ap`
ARM1176JZF-S core, 512 MiB of RAM

`raspi2b`
Cortex-A7 (4 cores), 1 GiB of RAM

`raspi3ap`
Cortex-A53 (4 cores), 512 MiB of RAM

`raspi3b`
Cortex-A53 (4 cores), 1 GiB of RAM

树莓派 6.1 内核源码: <https://github.com/raspberrypi/linux/tree/rpi-6.1.y>
