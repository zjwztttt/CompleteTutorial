## 一、准备工作：
### 指定`rustc`和`cargo`环境安装目录(添加系统环境变量)
    RUSTUP_HOME = E:\Rust\rustup
    CARGO_HOME = `E:\Rust\cargo

## 二、安装Rust开发环境
### [《官方安装教程》](https://rustup.rs/)
### [《第三方安装教程》](https://blog.csdn.net/cnds123/article/details/105770367)

## 三、Rust开发环境依赖`MSVC`切换为`Mingw`
#### 1. 用`rustup-init.exe`安装`mingw`(此方法只有在安装Rust开发环境时有效，已经安装完的无效)
> 在安装`rust`开发环境时选择2，在需要输入`host triple`时输入以下命令   
    
    x86_64-pc-windows-gnu
    
> 安装完成后运行以下命令
    
    rustup toolchain install stable
#### 2. 单独安装`mingw`(此方法是针对已经安装完Rust开发环境后想将依赖切换为`mingw`时)
    
    rustup toolchain install stable-x86_64-pc-windows-gnu
> 修改依赖为`mingw`
    
    rustup default stable-x86_64-pc-windows-gnu

## 四、静态编译(在项目根目录新建`.Cargo`文件夹并在文件夹中新建`config.toml`文件，黏贴以下内容到新建的`config.toml`文件中) 
    [target.x86_64-pc-windows-msvc]
    rustflags = ["-C", "target-feature=+crt-static"]

## 五、编译程序
    cargo build --release --target=x86_64-pc-windows-msvc

## 六、交叉编译
### [《Linux环境编译Windows可执行程序》](https://github.com/zjwztttt/CompleteTutorial/blob/main/Linux%E7%8E%AF%E5%A2%83%E4%B8%8BRust%E4%BA%A4%E5%8F%89%E7%BC%96%E8%AF%91Windows%E7%A8%8B%E5%BA%8F.md)
### [《Windows环境编译Linux可执行程序》](https://github.com/zjwztttt/CompleteTutorial/blob/main/Windows%E7%8E%AF%E5%A2%83%E4%B8%8BRust%E4%BA%A4%E5%8F%89%E7%BC%96%E8%AF%91Linux%E7%A8%8B%E5%BA%8F.md)

## 七、其他
### [《Ruat的一些常用命令》](https://github.com/zjwztttt/CompleteTutorial/blob/main/Rust%E7%9A%84%E4%B8%80%E4%BA%9B%E5%B8%B8%E7%94%A8%E5%91%BD%E4%BB%A4.md)
### [《Rust使用wasm-pack编译WebAssembly》](https://github.com/zjwztttt/CompleteTutorial/blob/main/Rust%E4%BD%BF%E7%94%A8wasm-pack%E7%BC%96%E8%AF%91WebAssembly%E6%A8%A1%E5%9D%97.md)
### [Rust使用Trunk编译WebAssembly](https://github.com/zjwztttt/CompleteTutorial/blob/main/Rust%E4%BD%BF%E7%94%A8Trunk%E7%BC%96%E8%AF%91WebAssembly%E6%A8%A1%E5%9D%97.md)
### [《Rust编译DLL库》](https://github.com/zjwztttt/CompleteTutorial/blob/main/Rust%E7%BC%96%E8%AF%91DLL%E5%BA%93.md)(详细教程请[参考](https://mp.weixin.qq.com/s/XUpjfPye_C56GJQp3YdMzA))
### [《Rust编译Python模块》](https://github.com/zjwztttt/CompleteTutorial/blob/main/Rust%E7%BC%96%E8%AF%91python%E6%A8%A1%E5%9D%97.md)(详细教程请[参考](https://mp.weixin.qq.com/s/X6fZiCuxAGxV0TC4o75yDw))
