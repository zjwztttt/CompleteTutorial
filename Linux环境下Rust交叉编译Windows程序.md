## 添加交叉编译工具链
    rustup toolchain install stable-x86_64-pc-windows-gnu
    rustup target add x86_64-pc-windows-gnu
## 安装mingw-w64
    apt update -y && apt upgrade && apt install mingw-w64
## 编译源代码为Windows可执行程序
    cargo build --release --target=x86_64-pc-windows-gnu
