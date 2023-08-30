## 更新`Rust`环境
    rustup update stable

## 卸载Rust环境
    rustup self uninstall

## 十四、验证版本
    rustup -V
    rustc -V
    cargo -V
    wasm-pack -V

## 查看所有支持的`target`和已经安装的`target`
    rustup target list

## 查看全部的`target`(更多交叉编译工具链库请[参阅](https://doc.rust-lang.org/nightly/rustc/platform-support.html))
    rustc --print target-list | pr -tw100 --columns 3
