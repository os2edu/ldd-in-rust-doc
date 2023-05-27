# 第一阶段：ArceOS in Qemu 验证（4.24-5.1）

## 任务零：Ubuntu 22.04 开发环境搭建

1. 在 Windows 上安装 WSL
   - 参考链接：<https://learn.microsoft.com/zh-cn/windows/wsl/install#troubleshooting-installation>
   - 如果出现问题，参考链接：<https://learn.microsoft.com/zh-cn/windows/wsl/install-manual>
2. 安装 Ubuntu-22.04。
   - 安装过程详见 1.1 中链接。以下是可安装的有效分发的列表：

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

1. 安装 rust

   - rust 官网：<https://www.rust-lang.org/>
   - 安装 rust:

     ```shell
     curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
     ```

   - 获取 rust 的最新版本：

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

   - 按 Esc 键退出编辑模式，按 : 键并输入 wq，保存并退出。
   - 加载修改后的配置：

     ```shell
     source ~/.bashrc
     ```

   - 检查 cargo 是否能正常使用（查看版本）：

     ```shell
     cargo --version
     ```

   - 更多关于 rust 的安装可参考：<https://www.rust-lang.org/tools/install>

2. 安装 git

   ```shell
   sudo apt update

   sudo apt install git
   ```

3. 安装 make

   ```shell
   sudo apt install make
   ```
