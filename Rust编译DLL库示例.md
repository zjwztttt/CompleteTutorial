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
