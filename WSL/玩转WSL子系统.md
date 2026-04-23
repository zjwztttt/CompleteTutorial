## windows for linux 子系统常用命令
### 1. 安装指定的Linux系统
    wsl.exe --install -d Debian
### 2. 更新WSL
    wsl.exe --update
### 3. 显示WSL状态(包括默认版本以及发行版)
    wsl --status
### 4. WSL关机
    wsl --shutdown
### 5. 查看安装在本地的WSL子系统
    wsl.exe -l --all  -v
### 6. 列出可用的Linux发行版
    wsl.exe -l -o
### 7. 设置默认Linux发行版
    wsl.exe --set-default Debian
### 8. 进入某一个WSL子系统中
    wsl.exe -u root -d debian
### 9. 设置WSL的默认版本
    wsl.exe --set-default-version 2
### 10. 执行某一个`WSL`子系统`etc`目录下的`init.wsl`服务脚本
    wsl.exe -u root -d debian sudo /etc/init.wsl start
### 11. 导出分发版本为`tar`文件到D盘
    wsl.exe --export Ubuntu-20.04 d:\wsl-ubuntu20.04.tar
### 12. 注销当前分发版
    wsl.exe --unregister Ubuntu-20.04
### 13. 重新导入并安装WSL到`d:\wsl\ubuntu20.04`目录
    wsl.exe --import Ubuntu-20.04 d:\wsl\ubuntu20.04 d:\wsl-ubuntu20.04.tar --version 2
### 14. 以指定的用户运行WSL
    wsl.exe --user root
### 15. 设置默认登录用户为`root`
    Debian config --default-user root
##### 如果以上命令无法设置默认登陆用户，以root用户登录Linux终端编辑`/etc/wsl.conf`文件
    [user]
    default=root
##### 更多关于`wsl.conf`文件中的配置可以参阅[官方文档](https://learn.microsoft.com/en-us/windows/wsl/wsl-config#user-settings)
### 16. 删除`tar`文件
    del d:\wsl-ubuntu20.04.tar
