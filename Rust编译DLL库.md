## 在`Cargo.toml`配置文件中黏贴以下内容
    [lib]
    name = "TestDLL" #生成dll的文件名
    crate-type = ["cdylib"]
## 编译`x86`架构的`DLL`库
    cargo build --release --target i686-pc-windows-msvc
