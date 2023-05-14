# 任务二：ArceOS 下载、编译和运行

ArceOS GitHub 网址：<https://github.com/rcore-os/arceos>

1. 克隆仓库

    ```shell
    git clone https://github.com/rcore-os/arceos.git
    ```

2. 编译
     1. 安装依赖：

        ```shell
        cargo install cargo-binutils
        ```

     2. 编译:（默认ARCH = x86_64）

        ```shell
        # arceos目录下
        make
        ```

      ![result](assert/task1.2.1.png)

3. 运行
   1. Hello World：(默认ARCH = x86_64)

        ```shell
        make justrun
        ```

   2. 运行特定APP:
    - 模板：

        ```shell
        make A=path/to/app ARCH=<arch> LOG=<log> NET=[y|n] FS=[y|n]
        ```

    - 例：

        ```shell
        make A=apps/helloworld ARCH=aarch64 LOG=info NET=N SMP=4 run
        ```

        ![result](assert/task1.2.2.png)
        详见：<https://github.com/rcore-os/arceos#example-apps-1>
