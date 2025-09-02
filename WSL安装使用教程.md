## Windows Subsystem for Linux 安装教程

<details markdown="1">
<summary>
启用“适用于Linux的Windows子系统”功能(方案二可跳过)
</summary>

#### 1.在windows任务栏中的搜索框里搜索并打开`启用或关闭 Windows 功能`
#### 2.向下滑动列表找到并勾选`适用于Linux的Windows子系统`，然后点击确定
#### 3.等待功能启用完成后点击`立即重新启动`

</details>

<details markdown="1"><summary>下载安装Linux子系统</summary>

### 方案一
#### 1.打开`Microsoft Store`
#### 2.搜索并下载`Debian`
#### 3.更新WSL到最新版
### 方案二
#### 1.运行`终端管理员`
#### 2.列出可以安装的Linux子系统的发行版
    wsl.exe -l -o
#### 3.下载并安装`Debian`
    wsl.exe --install Debian
### 方案三
#### 1.下载[Linux子系统安装包](https://learn.microsoft.com/en-us/windows/wsl/install-manual#downloading-distributions)
#### 2.安装`Debian`
#### 3.更新WSL到最新版

### 方案四(离线/无网络环境安装)
#### 1.下载并安装WSL安装包
#### 2.将方案三下载的Linux子系统的安装包解压到任意文件夹里
#### 3.创建Debian的快捷方式
#### 4.在`运行`窗口中输入以下命令并点击确定
    shell:programs
#### 5.将Debian的快捷方式剪切到打开的目录中
#### 6.如果打开Debian报错，可以在终端管理员窗口执行以下命令
    dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart

</details>


<details markdown="1">
<summary>配置使用Linux子系统</summary>

#### 1.首次打开Linux子系统需要设置登录账号和密码(个人本地使用没有必要设置！)
#### 2.运行`终端管理员`设置默认登录账号为root
    Debian config --default-user root
#### 3.更新Linux子系统
    apt update && apt upgrade -y

</details>

<details markdown="1">
<summary>将Linux子系统迁出C盘</summary>

#### 1.压缩并导出Linux子系统到D盘
    wsl.exe --export Debian d:\wsl-Debian.tar
#### 2.注销当前安装的Linux发行版
    wsl.exe --unregister Debian
#### 3.将Linux子系统导入到E盘
    wsl.exe --import Debian e:\RJKJ\wsl\Debian d:\wsl-Debian.tar --version 2

</details>

<details markdown="1">
<summary>限制Linux子系统的内存</summary>

#### 1.打开运行窗口输入以下命令打开用户文件夹
    %UserProfile%
#### 2.新建一个.wslconfig文件并且粘贴以下配置
    # 设置适用于在WSL 2上运行的所有Linux发行版
    [wsl2]
    # 分配给WSL的内存
    memory=4GB
    # 设置交换分区的容量
    swap=2GB
    # 指定绑定到 WSL VM 中的通配符或localhost 的端口是否可通过 localhost:port 从主机连接
    localhostforwarding=true
#### 3.保存以后执行如下命令关闭WSL
    wsl.exe --shutdown
#### 4.打开Linux子系统输入以下命令查看内存
    free -h
</details>

## [WSL安装包下载](https://github.com/microsoft/WSL)
## [玩转WSL子系统](WSL/玩转WSL子系统.md)
