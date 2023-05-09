### 将文件夹压缩为`.tar.gz`(常用来打包项目)
    tar -czvf 压缩文件名.tar.gz 文件夹名称
### 解压`.tar.gz`格式的压缩文件
    tar -xzvf 压缩文件名.tar.gz
### 将文件夹压缩为`.zip`
    zip -r 压缩文件名.zip 文件夹名称
### 解压`.zip`格式的压缩文件
    unzip 压缩文件名.zip
### 以程序名称关闭进程
    kill -9 `ps aux | grep your_script.py | grep -v grep | awk '{print $2}'`
### 以PID关闭进程
    kill -9 60120
### 以PID文件关闭进程
    
