## 在`Cargo.toml`配置文件中黏贴以下内容
    [lib]
    name = "TestDLL" #生成dll的文件名
    crate-type = ["cdylib"]
## 编译`x86`架构的`DLL`库
    cargo build --release --target i686-pc-windows-msvc

## 其他
### [Rust编译DLL库示例](https://github.com/zjwztttt/CompleteTutorial/blob/main/Rust%E7%BC%96%E8%AF%91DLL%E5%BA%93%E7%A4%BA%E4%BE%8B.md)
