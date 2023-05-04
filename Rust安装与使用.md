### Rust简介
#### Rust 是 Mozilla 公司的一款编程语言，最早的版本在2010年由 Mozilla 公司的 Graydon Hoare 开发并推出。该语言被设计用于大规模并行、多线程的网络应用程序的开发，为的是提高系统的可扩展性、安全性和速度。 Rust 语言是一种支持将变量指针引用进行多重使用，不同于通过分配和释放存储空间来传递值的传统功能语言。 Rust 是一种系统级别的语言，具有高度的安全和性能，并且内存安全和并发性能也是其优点
### Rust安装(Windows篇)
#### 我们在安装Rust开发环境时并不希望它安装在我们的`C`盘中破坏我们`C`盘稳定的系统环境，所以我们希望将环境搭建在其他空闲磁盘下,比如在`E`盘下新建一个名称为`Rust`的文件夹专门用来存放Rust安装的所有环境，以下所有操作都是基于此文件夹展开的
##### 1.新建一个名为`rustup`的文件夹，并将此`E:\Rust\rustup`路径添加到环境变量`RUSTUP_HOME`中
##### 2.新建一个名为`cargo`的文件夹，并将此`E:\Rust\cargo`路径添加到环境变量`CARGO_HOME`中
##### 3.Rust开发环境的安装请看[此教程](https://blog.csdn.net/cnds123/article/details/105770367)
### 使用cargo build打包项目
    cargo build --release
#### 如果你使用的是Rust语言，你可以使用cargo命令来构建你的项目。cargo是Rust的官方构建工具和包管理器，它可以帮助你构建、测试和打包你的Rust项目。你可以在命令行中进入你的项目目录，然后运行cargo build --release命令来构建你的项目。这将在target/release目录下生成一个可执行文件。如果你想将整个项目打包为一个单独的可执行文件，你可以考虑使用第三方工具，例如cargo-bundle。它可以帮助你将你的Rust项目打包为一个独立的应用程序，包括所有依赖项和资源文件。

#### cargo-bundle是一个第三方工具，可以帮助你将你的Rust项目打包为一个独立的应用程序。要安装cargo-bundle，你可以运行cargo install cargo-bundle命令。这将把最新版本的cargo-bundle作为子命令添加到你的默认cargo安装中1。安装完成后，你需要在你的项目的Cargo.toml文件中添加一个[package.metadata.bundle]部分。这一部分描述了生成的包的各种属性，例如名称、图标、描述、版权以及任何生成额外数据所需的打包脚本。完整的清单格式可以在cargo-bundle的GitHub页面上找到1。要构建一个应用程序包，只需在你的项目目录（其中包含Cargo.toml文件）中运行cargo bundle命令。如果你想打包一个发布版本，你必须在调用时添加--release标志。
