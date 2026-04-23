# Windows Subsystem for Debian 系统 Rust 安装使用教程
## 一、准备工作：
### 更新系统以及安装必要工具
    apt update -y && apt upgrade -y && apt install curl
## 二、开始安装：
### 安装 Rust 编程环境
    curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
### 在Debian终端窗口中执行以上命令的过程中出现选项时请输入1回车继续
### 当Debian终端窗口中显示 `Rust is installed now. Great!` 代表安装成功
## 三、创建项目：
### 选定一个空文件夹作为项目的存放目录
    cargo new 项目名称
## 四、静态编译(musl推荐)：
### 在Debian终端窗口中执行以下命令安装`musl`工具链
    rustup target add x86_64-unknown-linux-musl
### 在Debian终端窗口中的项目根目录下执行以下命令编译项目
    cargo build --release --target x86_64-unknown-linux-musl
## 五、静态编译(GNU)：
### 在项目的根目录创建`.cargo`文件夹，在`.cargo`文件夹中创建`config.toml`文件并在文件内编辑以下配置
    [target.x86_64-unknown-linux-gnu]
    rustflags = ["-C", "target-feature=+crt-static"]
### 在Debian终端窗口中的项目根目录下执行以下命令编译项目
    cargo build --release
## 六、想在Debian系统环境下编译出可在Windows系统中运行的程序请前往[查看交叉编译](./Linux环境下Rust交叉编译Windows程序.md)
## 七、遇到问题：
### 在执行编译运行命令时Debian终端窗口中显示以下错误内容
    error: linker `cc` not found
       |
       = note: No such file or directory (os error 2)
    error: could not compile `Mosquito` (bin "Mosquito") due to 1 previous error
### 解决方案(安装GCC编译器)
    apt install build-essential -y
### 
