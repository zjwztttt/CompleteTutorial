## windows for linux 子系统常用命令
### 1. 安装指定的Linux系统
    wsl.exe --install -d Debian
### 2. 更新WSL
    wsl.exe --update
### 3. 查看安装在本地的WSL子系统
    wsl.exe -l --all  -v
### 4. 列出可用的Linux发行版
    wsl.exe -l -o
### 5. 设置默认Linux发行版
    wsl.exe --set-default Debian
### 6. 进入某一个WSL子系统中
    wsl.exe -u root -d debian
### 7. 设置WSL的默认版本
    wsl.exe --set-default-version 2
### 8. 执行某一个`WSL`子系统`etc`目录下的`init.wsl`服务脚本
    wsl.exe -u root -d debian sudo /etc/init.wsl start
### 9. 导出分发版本为`tar`文件到D盘
    wsl.exe --export Ubuntu-20.04 d:\wsl-ubuntu20.04.tar
### 10. 注销当前分发版
    wsl.exe --unregister Ubuntu-20.04
### 11. 重新导入并安装WSL到`d:\wsl\ubuntu20.04`目录
    wsl.exe --import Ubuntu-20.04 d:\wsl\ubuntu20.04 d:\wsl-ubuntu20.04.tar --version 2
### 12. 以指定的用户运行WSL
    wsl.exe --user root
### 13. 设置默认登录用户为`root`
    Debian config --default-user root
### 14. 删除`tar`文件
    del d:\wsl-ubuntu20.04.tar
