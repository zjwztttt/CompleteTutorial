### 复制文件到指定目录
    cp 文件名 目标目录
### 查看程序的安装目录
    whereis 程序名称
### 服务启动
    service 服务名 start
    systemctl start 服务名
### 服务停止
    service 服务名 stop
    systemctl stop 服务名
### 服务重启
    service 服务名 restart
    systemctl restart 服务名
### 开机自启服务
    systemctl enable 服务名
### 查看服务运行日志
    systemctl status 服务名
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
    kill $(cat /var/run/hypercorn.pid)
### 以程序包名称关闭进程
    pkill -SIGTERM 包名称
### 安装GCC编译器
    apt install build-essential
### 查看GCC编译器版本
    gcc --version
### 查看G++编译器版本
    g++ --version
### 安装CMake编译器
    apt install cmake
### 查看系统版本
    cat /etc/os-release
