## 在`Cargo.toml`配置文件中黏贴以下内容
    [lib]
    name = "TestDLL" #生成dll的文件名
    crate-type = ["cdylib"]
## 编译`x86`架构的`DLL`库
    cargo build --release --target i686-pc-windows-msvc

## 其他
### [《Rust编译DLL库示例》](https://github.com/zjwztttt/CompleteTutorial/blob/main/Rust%E7%BC%96%E8%AF%91DLL%E5%BA%93%E7%A4%BA%E4%BE%8B.md)

## 返回[首页](https://github.com/zjwztttt/CompleteTutorial/blob/main/Rust%E5%AE%89%E8%A3%85%E4%B8%8E%E4%BD%BF%E7%94%A8.md#rust%E7%BC%96%E8%AF%91dll%E5%BA%93%E8%AF%A6%E7%BB%86%E6%95%99%E7%A8%8B%E8%AF%B7%E5%8F%82%E8%80%83)
