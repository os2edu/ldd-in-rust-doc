# Chapter 1

1. 在Windows上安装WSL
   - 参考链接：<https://learn.microsoft.com/zh-cn/windows/wsl/install#troubleshooting-installation>
   - 如果出现问题，参考链接：<https://learn.microsoft.com/zh-cn/windows/wsl/install-manual>
2. 安装Ubuntu-22.04。
   - 安装过程详见1.1中链接。以下是可安装的有效分发的列表：

| NAME                                | FRIENDLY NAME                       |
| ----------------------------------- | ----------------------------------- |
| Ubuntu                              | Ubuntu                              |
| Debian                              | Debian GNU/Linux                    |
| kali-linux                          | Kali Linux Rolling                  |
| Ubuntu-18.04                        | Ubuntu 18.04 LTS                    |
| Ubuntu-20.04                        | Ubuntu 20.04 LTS                    |
| Ubuntu-22.04                        | Ubuntu 22.04 LTS                    |
| OracleLinux_8_5                     | Oracle Linux 8.5                    |
| OracleLinux_7_9                     | Oracle Linux 7.9                    |
| SUSE-Linux-Enterprise-Server-15-SP4 | SUSE Linux Enterprise Server 15 SP4 |
| openSUSE-Leap-15.4                  | openSUSE Leap 15.4                  |
| openSUSE-Tumbleweed                 | openSUSE Tumbleweed                 |

1. 安装rust
   - rust 官网：<https://www.rust-lang.org/>
   - 安装rust:

      ```shell
      curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
      ```

   - 获取rust的最新版本：

      ```shell
      rustup update
      ```

   - 配置环境变量：

      ```shell
      vim ~/.bashrc
      ```

   - 按 i 键进入编辑模式，在文件最后加入：

      ```shell
      export PATH=~/.cargo/bin:$PATH
      ```

   - 按Esc键退出编辑模式，按 : 键并输入wq，保存并推出。
   - 加载修改后的配置：

      ```shell
      source ~/.bashrc
      ```

   - 检查cargo是否能正常使用（查看版本）：

      ```shell
      cargo --version
      ```

   - 更多关于rust的安装可参考：<https://www.rust-lang.org/tools/install>

2. 安装git

      ```shell
      sudo apt update

      sudo apt install git
      ```

3. 安装make

      ```shell
      sudo apt install make
      ```
