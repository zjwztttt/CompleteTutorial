## 安装`wasm-pack`包(windows请获取[安装文件](https://rustwasm.github.io/wasm-pack/installer/))
    cargo install wasm-pack
## 添加`target`(更多`target`请参阅[此文档](https://doc.rust-lang.org/nightly/rustc/platform-support.html)中的Tier2部分)
    rustup target add wasm32-unknown-unknown
## 新建一个`wasm`包(wasm代码可以看[这篇教程](https://developer.mozilla.org/zh-CN/docs/WebAssembly/Rust_to_wasm)或者[这篇教程](https://www.wkwkk.com/articles/1c90cd3673398f7f.html))
    cargo new --lib hello-wasm
## 在`Cargo.toml`文件中黏贴以下内容
    [lib]
    crate-type = ["cdylib"]
## 在`[dependencies]`块中添加以下配置项
    wasm-bindgen = "0.2"
## 构建`wasm`包
    wasm-pack build --target web

## 其他
### [《WebAssembly模块示例》]()
