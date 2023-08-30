## 几个`python module`的栗子
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

## python使用模块的几个栗子
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

## 返回[上一页](https://github.com/zjwztttt/CompleteTutorial/blob/main/Rust%E7%BC%96%E8%AF%91python%E6%A8%A1%E5%9D%97.md)
## 返回[首页](https://github.com/zjwztttt/CompleteTutorial/blob/main/Rust%E5%AE%89%E8%A3%85%E4%B8%8E%E4%BD%BF%E7%94%A8.md#rust%E7%BC%96%E8%AF%91python%E6%A8%A1%E5%9D%97%E8%AF%A6%E7%BB%86%E6%95%99%E7%A8%8B%E8%AF%B7%E5%8F%82%E8%80%83)
