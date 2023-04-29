### Rust简介
#### Rust 是 Mozilla 公司的一款编程语言，最早的版本在2010年由 Mozilla 公司的 Graydon Hoare 开发并推出。该语言被设计用于大规模并行、多线程的网络应用程序的开发，为的是提高系统的可扩展性、安全性和速度。 Rust 语言是一种支持将变量指针引用进行多重使用，不同于通过分配和释放存储空间来传递值的传统功能语言。 Rust 是一种系统级别的语言，具有高度的安全和性能，并且内存安全和并发性能也是其优点
### Rust安装
#### 你可以通过设置环境变量来自定义Rust开发环境的安装目录。你需要设置两个环境变量：RUSTUP_HOME和CARGO_HOME。RUSTUP_HOME用于指定rustup的安装目录，而CARGO_HOME用于指定cargo的安装目录1。例如，如果你想将Rust开发环境安装在D盘的Rust文件夹下，你可以将RUSTUP_HOME和CARGO_HOME分别设置为D:\Rust\rustup和D:\Rust\cargo。然后再运行安装程序来安装Rust开发环境。
#### cargo-bundle是一个第三方工具，可以帮助你将你的Rust项目打包为一个独立的应用程序。要安装cargo-bundle，你可以运行cargo install cargo-bundle命令。这将把最新版本的cargo-bundle作为子命令添加到你的默认cargo安装中1。安装完成后，你需要在你的项目的Cargo.toml文件中添加一个[package.metadata.bundle]部分。这一部分描述了生成的包的各种属性，例如名称、图标、描述、版权以及任何生成额外数据所需的打包脚本。完整的清单格式可以在cargo-bundle的GitHub页面上找到1。要构建一个应用程序包，只需在你的项目目录（其中包含Cargo.toml文件）中运行cargo bundle命令。如果你想打包一个发布版本，你必须在调用时添加--release标志。
