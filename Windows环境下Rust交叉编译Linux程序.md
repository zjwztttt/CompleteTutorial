## 添加交叉编译链库
    rustup target add x86_64-unknown-linux-musl
## 黏贴以下内容到`config.toml`配置文件中
    [target.x86_64-unknown-linux-musl]
    linker = "rust-lld"
    rustflags = ["-C", "linker-flavor=ld.lld"]
## 编译Rust源码为Linux可执行程序
    cargo build --release --target=x86_64-unknown-linux-musl

## 返回[首页](https://github.com/zjwztttt/CompleteTutorial/blob/main/Rust%E5%AE%89%E8%A3%85%E4%B8%8E%E4%BD%BF%E7%94%A8.md#windows%E7%8E%AF%E5%A2%83%E7%BC%96%E8%AF%91linux%E5%8F%AF%E6%89%A7%E8%A1%8C%E7%A8%8B%E5%BA%8F)
