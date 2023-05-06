### Rust简介
#### Rust 是 Mozilla 公司的一款编程语言，最早的版本在2010年由 Mozilla 公司的 Graydon Hoare 开发并推出。该语言被设计用于大规模并行、多线程的网络应用程序的开发，为的是提高系统的可扩展性、安全性和速度。 Rust 语言是一种支持将变量指针引用进行多重使用，不同于通过分配和释放存储空间来传递值的传统功能语言。 Rust 是一种系统级别的语言，具有高度的安全和性能，并且内存安全和并发性能也是其优点
### Rust安装(Windows篇)
#### 我们在安装Rust开发环境时并不希望它安装在我们的`C`盘中破坏我们`C`盘稳定的系统环境，所以我们希望将环境搭建在其他空闲磁盘下,比如在`E`盘下新建一个名称为`Rust`的文件夹专门用来存放Rust安装的所有环境，以下所有操作都是基于此文件夹展开的
##### 1.新建一个名为`rustup`的文件夹，并将此`E:\Rust\rustup`路径添加到环境变量`RUSTUP_HOME`中
##### 2.新建一个名为`cargo`的文件夹，并将此`E:\Rust\cargo`路径添加到环境变量`CARGO_HOME`中
##### 3.Rust开发环境的安装请看[此教程](https://blog.csdn.net/cnds123/article/details/105770367)
### 在安装`rustup`时选择2，在需要输入`host triple`时输入以下命令
    x86_64-pc-windows-gnu
### 安装完成后运行以下命令
    rustup toolchain install stable
#### 以上是随`rustup`一起安装`mingw`的方式
### 安装`mingw`
    rustup toolchain install stable-x86_64-pc-windows-gnu 
### 修改`MSVC`依赖为`mingw`
    rustup default stable-x86_64-pc-windows-gnu
#### 以上是单独安装`mingw`的方式
### 使用`cargo build`打包项目(在命令行中进入你的项目目录)
    cargo build --release
### 使用`cargo-bundle`打包项目
#### cargo-bundle是一个第三方工具，可以帮助你将你的Rust项目打包为一个独立的应用程序，运行以下命令安装它
    cargo install cargo-bundle
#### 在`cargo.toml`文件中的`[package]`块下添加以下信息(需要将引号中的内容改成你的项目目录)
    description = "Your package description"
#### 在`Cargo.toml`文件中添加以下块
    [package.metadata.bundle]
##### 这一部分描述了生成的包的各种属性，例如名称、图标、描述、版权以及任何生成额外数据所需的打包脚本。完整的清单格式可以查阅`cargo-bundle`的[GitHub页面](https://github.com/burtonageo/cargo-bundle)
#### 使用以下命令打包一个发布版本
    cargo bundle --release
#### 卸载Rust环境
    rustup self uninstall
