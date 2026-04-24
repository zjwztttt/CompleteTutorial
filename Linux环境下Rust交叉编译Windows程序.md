## 添加交叉编译工具链
    rustup target add x86_64-pc-windows-gnu
## 安装mingw-w64
    apt update -y && apt upgrade && apt install mingw-w64
## 编译源代码为Windows可执行程序
    cargo build --release --target=x86_64-pc-windows-gnu

## 返回[WSLD](WSL/Rust在WSDB系统上的安装与使用教程.md)
## 返回[首页](https://github.com/zjwztttt/CompleteTutorial/blob/7e6e572c208774c3771bbaa10a385aebc0635a6a/Rust%E5%AE%89%E8%A3%85%E4%B8%8E%E4%BD%BF%E7%94%A8.md)
