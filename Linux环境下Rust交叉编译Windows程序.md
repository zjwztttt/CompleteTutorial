## 添加交叉编译工具链
    rustup toolchain install stable-x86_64-pc-windows-gnu
    rustup target add x86_64-pc-windows-gnu
## 安装mingw-w64
    apt update -y && apt upgrade && apt install mingw-w64
## 编译源代码为Windows可执行程序
    cargo build --release --target=x86_64-pc-windows-gnu

## 返回[首页](https://github.com/zjwztttt/CompleteTutorial/blob/main/Rust%E5%AE%89%E8%A3%85%E4%B8%8E%E4%BD%BF%E7%94%A8.md#linux%E7%8E%AF%E5%A2%83%E7%BC%96%E8%AF%91windows%E5%8F%AF%E6%89%A7%E8%A1%8C%E7%A8%8B%E5%BA%8F)
