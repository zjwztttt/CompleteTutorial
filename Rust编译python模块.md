## 在`Cargo.toml`配置文件中黏贴以下配置
    [lib]
    name = "python_rust"
    crate-type = ["cdylib"]
    
    [dependencies]
    pyo3 = "0.18.3"

## 编译`Python模块`需要`python环境`和`pip工具`安装`maturin库`
    pip3 install maturin
    
## 使用`maturin`编译Rust源码为`python模块`
    maturin build

## 其他
### [《Rust编译Python模块示例》](https://github.com/zjwztttt/CompleteTutorial/blob/main/Rust%E7%BC%96%E8%AF%91python%E6%A8%A1%E5%9D%97%E7%A4%BA%E4%BE%8B.md)

## 返回[首页](https://github.com/zjwztttt/CompleteTutorial/blob/main/Rust%E5%AE%89%E8%A3%85%E4%B8%8E%E4%BD%BF%E7%94%A8.md#rust%E7%BC%96%E8%AF%91python%E6%A8%A1%E5%9D%97%E8%AF%A6%E7%BB%86%E6%95%99%E7%A8%8B%E8%AF%B7%E5%8F%82%E8%80%83)
