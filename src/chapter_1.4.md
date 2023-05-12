# 任务四：ArceOS + 网卡驱动 in Qemu for AArch64 验证

1.  配置
    在qemu目录下

      ```shell
      sudo apt-get install libslirp-dev
      sudo apt install flex
      sudo apt install bison
      ./configure --target-list=aarch64-softmmu --enable-slirp
      ```

 ![picture](assert/task1.4.1.png)

2.  编译
      
      ```shell
      make
      ```

![picture](assert/task1.4.2.png)

3.  运行
    返回arceos目录下

      ```shell
      make A=apps/net/httpserver ARCH=aarch64 LOG=info NET=y SMP=4 run
      
      rust-objcopy --binary-architecture=aarch64 apps/net/httpserver/httpserver_qemu-virt-aarch64.elf --strip-all -O binary apps/net/httpserver/httpserver_qemu-virt-aarch64.bin

      qemu-system-aarch64 -m 128M -smp 4 -cpu cortex-a72 -machine virt -kernel apps/net/httpserver/httpserver_qemu-virt-aarch64.bin -device virtio-net-device,netdev=net0 -netdev user,id=net0,hostfwd=tcp::5555-:5555,hostfwd=udp::5555-:5555 -nographic
      ```
    
![picture](assert/task1.4.3.png)

成功后显示得到的网址

![picture](assert/task1.4.4.png)

复制到浏览器中访问，或者访问localhost:(端口号)，得到:

![picture](assert/task1.4.5.png)

同时终端更新Log:

![picture](assert/task1.4.6.png)