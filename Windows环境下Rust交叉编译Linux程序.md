## 添加交叉编译链库
    rustup target add x86_64-unknown-linux-musl
## 黏贴以下内容到`config.toml`配置文件中
    [target.x86_64-unknown-linux-musl]
    linker = "rust-lld"
    rustflags = ["-C", "linker-flavor=ld.lld"]
## 编译Rust源码为Linux可执行程序
    cargo build --release --target=x86_64-unknown-linux-musl
