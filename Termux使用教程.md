### 1.查看当前源列表
    apt sources
### 2.修改源文件替换源地址
    nano /data/data/com.termux/files/usr/etc/apt/sources.list
### 3.搜索程序安装包
    pkg search 程序名称
### 4.安装程序或更换软件源
    pkg install 安装包名称或源文件
### 5.卸载程序
    pkg uninstall 安装包名称
### 6.重新安装程序
    pkg reinstall 安装包名称
### 7.更新软件源
    pkg update
### 8.升级程序
    pkg upgrade
### 9.列出可供安装的所有安装包
    pkg list-all
### 10.列出已经安装的包
    pkg list-installed
### 11.显示某个安装包的详细信息
    pkg show 安装包名称
### 12.显示某个安装包的相关文件夹路径
    pkg files 安装包名称
### 13.开启Termux访问本机存储文件夹
    termux-setup-storage
### 14.查看本机IP地址
    ifconfig
## 源文件
#### 1.清华大学的源文件
    tsinghua.sources
#### 2.中科大的源文件
    ustc.sources
#### 3.阿里云的源文件
    aliyun.sources
## 源地址
#### 1.清华大学的源地址
    deb https://mirrors.tuna.tsinghua.edu.cn/termux stable main
## 示例
### 1.安装OpenSSH
    pkg install openssh
#### 启动OpenSSH
    sshd
#### 查看Termux的用户名
    whoami
#### 其他设备连接OpenSSH
    ssh Termux的用户名 @ Termux的IP地址 -p 8022
#### 其他设备退出OpenSSH连接
    exit
### 2.切换Root用户
### 没有获取Root权限的手机
#### 安装proot工具
    pkg install proot
#### 模拟Root用户
    termux-chroot
### 已经获取Root权限的手机
#### 安装tsu工具
    pkg install tsu
#### 切换为Root用户
    tsu
#### 手机会弹出请求Root授权的窗口，通过授权即可！
#### 退出Root用户
    exit
## 解决Android12以上的系统强杀Termux后台的问题
#### 在Termux分屏显示下进入手机的开发者选项中并打开无线调试并记下端口号
#### 点击使用配对码配对设备并在弹出的菜单中记下配对码与这个IP地址与端口号
#### 在Termux窗口中输入以下命令
    apt update && apt upgrade -y && apt install git -y && git clone https://github.com/SaicharanKandukuri/termux-android12-phantom-fixcd termux-android12-phantom-fix && bash runme.sh
#### 输入配对码弹出菜单里的端口号
#### 输入配对码
#### 输入无线调试界面中的端口号
### Tmoe大佬解决脚本
    bash -c "$(curl -L l.tmoe.me)"
