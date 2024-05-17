## windows for linux 子系统常用命令
### 1. 安装指定的Linux系统为默认子系统
    wsl --install -d Debian
### 2. 查看安装在本地的WSL子系统
    wsl --list
### 3. 查看WSL分发版本
    wsl -l --all  -v
### 4. 进入某一个WSL子系统中
    wsl -u root -d debian
### 5. 执行某一个`WSL`子系统`etc`目录下的`init.wsl`服务脚本
    wsl -u root -d debian sudo /etc/init.wsl start
### 6. 导出分发版本为`tar`文件到D盘
    wsl --export Ubuntu-20.04 d:\wsl-ubuntu20.04.tar
### 7. 注销当前分发版
    wsl --unregister Ubuntu-20.04
### 8. 重新导入并安装WSL到`d:\wsl\ubuntu20.04`目录
    wsl --import Ubuntu-20.04 d:\wsl\ubuntu20.04 d:\wsl-ubuntu20.04.tar --version 2
### 9. 设置默认登录用户为`root`
    Debian config --default-user root
### 10. 删除`tar`文件
    del d:\wsl-ubuntu20.04.tar
