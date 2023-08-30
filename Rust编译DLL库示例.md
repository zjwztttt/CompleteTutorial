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

## 返回[首页](https://github.com/zjwztttt/CompleteTutorial/blob/main/Rust%E5%AE%89%E8%A3%85%E4%B8%8E%E4%BD%BF%E7%94%A8.md)
