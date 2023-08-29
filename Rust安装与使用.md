## 一、准备工作：
### 指定`rustc`和`cargo`环境安装目录(添加系统环境变量)
    RUSTUP_HOME = E:\Rust\rustup
    CARGO_HOME = `E:\Rust\cargo

## 二、安装Rust开发环境
##### Rust开发环境的安装请看[此教程](https://blog.csdn.net/cnds123/article/details/105770367)

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

## 四、编译程序
    cargo build --release

## 五、交叉编译
### [《Linux环境编译Windows可执行程序》](https://github.com/zjwztttt/CompleteTutorial/blob/main/Linux%E7%8E%AF%E5%A2%83%E4%B8%8BRust%E4%BA%A4%E5%8F%89%E7%BC%96%E8%AF%91Windows%E7%A8%8B%E5%BA%8F.md)
### [《Windows环境编译Linux可执行程序》](https://github.com/zjwztttt/CompleteTutorial/blob/main/Windows%E7%8E%AF%E5%A2%83%E4%B8%8BRust%E4%BA%A4%E5%8F%89%E7%BC%96%E8%AF%91Linux%E7%A8%8B%E5%BA%8F.md)
## 六、静态编译
##### 在`config.toml`配置文件中黏贴以下内容
    [target.x86_64-pc-windows-msvc]
    rustflags = ["-C", "target-feature=+crt-static"]
##### 编译程序
    cargo build --release --target=x86_64-pc-windows-msvc

## 七、查看所有支持的`target`和已经安装的`target`
    rustup target list

## 八、查看支持的CPU架构和OS系统(更多交叉编译工具链库请[参阅](https://doc.rust-lang.org/nightly/rustc/platform-support.html))
    rustc --print target-list | pr -tw100 --columns 3

## 九、更新`Rust`环境
    rustup update stable

## 十、卸载Rust环境
    rustup self uninstall

## 十一、编译`WebAssembly`
#### 安装`wasm-pack`包(windows请获取[安装文件](https://rustwasm.github.io/wasm-pack/installer/))
    cargo install wasm-pack
#### 添加`target`(更多`target`请参阅[此文档](https://doc.rust-lang.org/nightly/rustc/platform-support.html)中的Tier2部分)
    rustup target add wasm32-unknown-unknown
#### 新建一个`wasm`包(wasm代码可以看[这篇教程](https://developer.mozilla.org/zh-CN/docs/WebAssembly/Rust_to_wasm)或者[这篇教程](https://www.wkwkk.com/articles/1c90cd3673398f7f.html))
    cargo new --lib hello-wasm
#### 在`config.toml`文件中黏贴以下内容
    [lib]
    crate-type = ["cdylib"]
#### 在`[dependencies]`块中添加以下配置项
    wasm-bindgen = "0.2"
#### 构建`wasm`包
    wasm-pack build --target web
    
## 十二、编译`DLL`库(详细教程请[参考](https://mp.weixin.qq.com/s/XUpjfPye_C56GJQp3YdMzA))
#### 在`config.toml`配置文件中黏贴以下内容
    [lib]
    name = "TestDLL" #生成dll的文件名
    crate-type = ["cdylib"]
#### 编译`x86`架构的`DLL`库
    cargo build --release --target i686-pc-windows-msvc

## 十三、编译`python module`(详细教程请[参考](https://mp.weixin.qq.com/s/X6fZiCuxAGxV0TC4o75yDw))
#### 在`config.toml`配置文件中黏贴以下配置
    [lib]
    name = "python_rust"
    crate-type = ["cdylib"]
    
    [dependencies]
    pyo3 = "0.18.3"

## 十四、验证版本
    rustup -V
    rustc -V
    cargo -V
    wasm-pack -V

## 十五、几个`WebAssembly`模块的栗子
#### 例子1
    // 导入wasm_bindgen库
    extern crate wasm_bindgen;
    // 从wasm_bindgen库中导入prelude模块
    use wasm_bindgen::prelude::*;

    // 声明一个名为sum的导出函数
    #[wasm_bindgen]
    pub fn sum(a: i32, b: i32) -> i32 {
        return a + b;
    }
#### 例子2
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
#### 例子3
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
#### 例子4

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
#### 例3
    <script type="module">
        // 导入WebAssembly模块并从中导入sum函数
        import init, {sum} from "./templates/pkg/hello_wasm.js";
        // 初始化WebAssembly模块并调用sum函数
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
    
## 十六、几个DLL库的栗子
#### 例1
    #[no_mangle]
    pub extern fn hello() {
        println!("hello Rust DLL!");
    }
### `C#`读取DLL库的几个小栗子
#### 例1
    class Program
    {
        [DllImport("TestDLL.dll", EntryPoint = "hello", CallingConvention = CallingConvention.Cdecl)]
        public static extern void hello();

        static void Main(string[] args)
        {
            hello();
            Console.ReadLine();
        }
    }

## 十七、几个`python module`的栗子
#### 例1
    use pyo3::prelude::*;

    /// 求两个数的和
    #[pyfunction]
    fn sum(a: isize, b: isize) -> PyResult<isize> {
        Ok(a + b)
    }

    /// 一个用Rust实现的Python模块。
    ///
    /// 这个函数的名字必须与`Cargo.toml`中的`lib.name`匹配
    #[pymodule]
    fn python_rust(_py: Python, module: &PyModule) -> PyResult<()> {
        module.add_function(wrap_pyfunction!(sum, module)?)?;
        Ok(())
    }
#### 例2
    use pyo3::prelude::*;

    /// 求两个数的和
    #[pyfunction]
    fn sum(a: isize, b: isize) -> PyResult<isize> {
        Ok(a + b)
    }

    #[pyfunction]
    fn multiple(a: isize, b: isize) -> PyResult<isize> {
        Ok(a * b)
    }

    /// 一个用Rust实现的Python模块。
    ///
    /// 这个函数的名字必须与`Cargo.toml`中的`lib.name`匹配
    #[pymodule]
    fn python_rust(_py: Python, module: &PyModule) -> PyResult<()> {
        module.add_function(wrap_pyfunction!(sum, module)?)?;
        module.add_function(wrap_pyfunction!(multiple, module)?)?;
        Ok(())
    }
#### 例3
    use pyo3::prelude::*;

    /// 排序
    #[pyfunction]
    fn sort(mut vec: Vec<isize>) -> PyResult<Vec<isize>> {
        vec.sort();
        Ok(vec)
    }

    /// 一个用Rust实现的Python模块。
    ///
    /// 这个函数的名字必须与`Cargo.toml`中的`lib.name`匹配
    #[pymodule]
    fn python_rust2(_py: Python, module: &PyModule) -> PyResult<()> {
        module.add_function(wrap_pyfunction!(sort, module)?)?;
        Ok(())
    }
#### 例4
    use pyo3::prelude::*;

    #[pyclass]
    struct Dog {
        #[pyo3(get, set)]
        pub id: isize,
        #[pyo3(get, set)]
        pub name: String,
    }

    #[pymethods]
    impl Dog {
        #[new]
        fn new(id: isize, name: String) -> Self {
            Self {
                id,
                name,
            }
        }

        fn run(&self) {
            println!("{} is running!", self.name);
        }
    }
    
    #[pymodule]
    fn python_rust2(_py: Python, module: &PyModule) -> PyResult<()> {
        module.add_class::<Dog>()?;
        Ok(())
    }
#### 以上例子需要用`python`环境和`pip`工具安装`maturin`库
    pip3 install maturin
    
#### 使用`maturin`编译以上Rust例子为`python module`
    maturin build
    
### python使用模块的几个栗子
#### 例1
    import python_rust

    sum = python_rust.sum(5, 6)
    print(sum)
#### 例2
    import python_rust2

    sort = python_rust2.sort([2, 3, 7, 4, 5, 0, 2, 1])
    print(sort)
#### 例3
    import python_rust2

    dog = python_rust2.Dog(id = 1, name = "Shirley")
    dog.run()
