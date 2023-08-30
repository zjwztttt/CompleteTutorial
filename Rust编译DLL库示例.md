## 几个DLL库的栗子
#### 例1
    #[no_mangle]
    pub extern fn hello() {
        println!("hello Rust DLL!");
    }
## `C#`读取DLL库的几个小栗子
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

## 返回[上一页](https://github.com/zjwztttt/CompleteTutorial/blob/main/Rust%E7%BC%96%E8%AF%91DLL%E5%BA%93.md)
## 返回[首页](https://github.com/zjwztttt/CompleteTutorial/blob/main/Rust%E5%AE%89%E8%A3%85%E4%B8%8E%E4%BD%BF%E7%94%A8.md#rust%E7%BC%96%E8%AF%91dll%E5%BA%93%E8%AF%A6%E7%BB%86%E6%95%99%E7%A8%8B%E8%AF%B7%E5%8F%82%E8%80%83)
