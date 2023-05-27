# 任务三：ArceOS in Qemu for AArch64/RISC-V 验证

1.  AArch64 验证

确保任务二中步骤 3.运行的例子中以下命令执行无误

```shell
# arceos目录下
make A=apps/helloworld ARCH=aarch64 LOG=info NET=N SMP=4 run
```

程序正常运行出现预期结果，即完成 AArch64 验证

2.  RISC-V 验证

```shell
# arceos目录下
make A=apps/helloworld ARCH=riscv64 LOG=info NET=N SMP=4 run
```

程序正常运行出现预期结果，即完成 RISC-V 验证
