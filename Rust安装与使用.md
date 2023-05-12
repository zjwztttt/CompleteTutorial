### 一、Rust简介
#### Rust 是 Mozilla 公司的一款编程语言，最早的版本在2010年由 Mozilla 公司的 Graydon Hoare 开发并推出。该语言被设计用于大规模并行、多线程的网络应用程序的开发，为的是提高系统的可扩展性、安全性和速度。 Rust 语言是一种支持将变量指针引用进行多重使用，不同于通过分配和释放存储空间来传递值的传统功能语言。 Rust 是一种系统级别的语言，具有高度的安全和性能，并且内存安全和并发性能也是其优点

### 二、Rust安装(Windows篇)
#### 我们在安装Rust开发环境时并不希望它安装在我们的`C`盘中破坏我们`C`盘稳定的系统环境，所以我们希望将环境搭建在其他空闲磁盘下,比如在`E`盘下新建一个名称为`Rust`的文件夹专门用来存放Rust安装的所有环境，以下所有操作都是基于此文件夹展开的
##### 1.新建一个名为`rustup`的文件夹，并将此`E:\Rust\rustup`路径添加到环境变量`RUSTUP_HOME`中
##### 2.新建一个名为`cargo`的文件夹，并将此`E:\Rust\cargo`路径添加到环境变量`CARGO_HOME`中
##### 3.Rust开发环境的安装请看[此教程](https://blog.csdn.net/cnds123/article/details/105770367)

### 三、为Rust切换交叉编译工具链(更多交叉编译工具链库请[参阅](https://doc.rust-lang.org/nightly/rustc/platform-support.html))
#### 1.用`rustup-init.exe`安装`mingw`(此方法只有在安装Rust开发环境时有效，已经安装完的无效)
##### 在安装`rust`开发环境时选择2，在需要输入`host triple`时输入以下命令
    x86_64-pc-windows-gnu
##### 安装完成后运行以下命令
    rustup toolchain install stable
#### 2.单独安装`mingw`(此方法是针对已经安装完Rust开发环境后想将交叉编译链库切换为`mingw`时)
    rustup toolchain install stable-x86_64-pc-windows-gnu
##### 修改依赖为`mingw`
    rustup default stable-x86_64-pc-windows-gnu

### 四、编译程序
#### 1.使用`cargo build`打包项目(在命令行中进入你的项目目录)
    cargo build --release
#### 2.使用`cargo-bundle`打包项目
##### 安装cargo-bundle
    cargo install cargo-bundle
##### 在`cargo.toml`文件中的`[package]`块下添加以下信息(需要将引号中的内容改成你的项目目录)
    description = "Your package description"
##### 在`Cargo.toml`文件中添加以下块
    [package.metadata.bundle]
###### 这一部分描述了生成的包的各种属性，例如名称、图标、描述、版权以及任何生成额外数据所需的打包脚本。完整的清单格式可以查阅`cargo-bundle`的[GitHub页面](https://github.com/burtonageo/cargo-bundle)
##### 使用以下命令打包一个发布版本
    cargo bundle --release
### 五、更新`Rust`环境
    rustup update
### 六、卸载Rust环境
    rustup self uninstall
### 七、编译`WebAssembly`
#### 安装`wasm-pack`包(windows请获取[安装文件](https://rustwasm.github.io/wasm-pack/installer/))
    cargo install wasm-pack
#### 添加目标 wasm32-unknown-unknown(请参阅[此文档](https://doc.rust-lang.org/nightly/rustc/platform-support.html)中的Tier2部分)
    rustup target add wasm32-unknown-unknown
#### 新建一个`wasm`包(wasm代码可以看[这篇教程](https://developer.mozilla.org/zh-CN/docs/WebAssembly/Rust_to_wasm)或者[这篇教程](https://www.wkwkk.com/articles/1c90cd3673398f7f.html))
    cargo new --lib hello-wasm
#### 构建`wasm`包
    wasm-pack build --target web
### 八、验证版本
    rustup -V
    rustc -V
    cargo -V
    wasm-pack -V
### 九、几个`WebAssembly`模块的栗子
#### 例子1
    // 导入wasm_bindgen库
    extern crate wasm_bindgen;
    // 从wasm_bindgen库中导入prelude模块
    use wasm_bindgen::prelude::*;
    
    // 声明一个名为alert的外部函数
    #[wasm_bindgen]
    extern {
        pub fn alert(s: &str);
    }
    
    // 声明一个名为greet的导出函数
    #[wasm_bindgen]
    pub fn greet(name: &str) {
        // 调用alert函数并显示一条消息
        alert(&format!("Hello, {}!", name));
    }
### 例子2
    // 导入wasm_bindgen库
    extern crate wasm_bindgen;
    // 从wasm_bindgen库中导入prelude模块
    use wasm_bindgen::prelude::*;

    // 声明一个名为console_log的外部函数
    #[wasm_bindgen]
    extern {
        #[wasm_bindgen(js_namespace = console)]
        fn log(s: &str);
    }

    // 声明一个名为greet的导出函数
    #[wasm_bindgen]
    pub fn greet(name: &str) {
        // 调用console_log函数并显示一条消息
        log(&format!("Hello, {}!", name));
    }
### 例子3

### 前端加载WebAssembly模块的几个小栗子
#### 例1
    <!DOCTYPE html>
    <html>
        <head>
            <meta charset="utf-8">
            <title>hello-wasm example</title>
        </head>
        <body>
            <!-- 导入WebAssembly模块 -->
            <script type="module">
                // 导入WebAssembly模块并从中导入greet函数
                import init, {greet} from "./pkg/hello_wasm.js";
                // 初始化WebAssembly模块并调用greet函数
                init().then(() => {
                    greet("WebAssembly")
                });
            </script>
        </body>
    </html>
#### 例2
    <script type="module">
        // 导入WebAssembly模块并从中导入greet函数
	import init, {greet} from "./templates/pkg/hello_wasm.js";		
	fetch('https://api.ipify.org?format=json')
	    .then(response => response.json())
	    .then(data => {
	        const ip = data.ip;
		// 初始化WebAssembly模块并调用greet函数
		init().then(() => {
		    // 将IP地址传递给WebAssembly模块
		    greet(ip);
                });
            });
    </script>
### 例3
    <script type="module">
        // 导入WebAssembly模块并从中导入greet函数
	import init, {sum} from "./templates/pkg/hello_wasm.js";
	// 初始化WebAssembly模块并调用greet函数
	init().then(() => {
	    // 将"a"和"b"传递给WebAssembly模块并将返回的结果赋值给"result"变量
	    var result = sum(5735, 7312);
	    //将"结果写入页面"
	    document.write("wasm sum 5735 +7312  = " + result)
	    //将结果打印在调试日志中
	    console.log(result);
	});
    </script>

### 以上代码可以用以下命令运行
    python3 -m http.server

