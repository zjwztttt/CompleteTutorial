## 例子1
    // 导入wasm_bindgen库
    extern crate wasm_bindgen;
    // 从wasm_bindgen库中导入prelude模块
    use wasm_bindgen::prelude::*;

    // 声明一个名为sum的导出函数
    #[wasm_bindgen]
    pub fn sum(a: i32, b: i32) -> i32 {
        return a + b;
    }
## 例子2
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
## 例子3
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
## 例子4

## 前端加载WebAssembly模块的几个小栗子
## 例1
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
## 例2
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
## 例3
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

## 以上代码可以用以下命令运行
    python3 -m http.server

## 返回[上一页](https://github.com/zjwztttt/CompleteTutorial/blob/main/Rust%E7%BC%96%E8%AF%91WebAssembly%E6%A8%A1%E5%9D%97.md)
## 返回[首页](https://github.com/zjwztttt/CompleteTutorial/blob/main/Rust%E5%AE%89%E8%A3%85%E4%B8%8E%E4%BD%BF%E7%94%A8.md)
