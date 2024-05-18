## Windows Subsystem for Linux 安装教程

<details markdown="1">
<summary>
启用“适用于Linux的Windows子系统”功能(点击展开,方案二可跳过)
</summary>

#### 1.在windows任务栏中的搜索框里搜索并打开`启用或关闭windows功能`
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
#### 2.运行`终端管理员`并进入安装包所在的文件夹
#### 3.安装`Debian`
    Add-AppxPackage .\Debian.appx

</details>


<details markdown="1">
<summary>配置使用Linux子系统</summary>

#### 1.首次打开Linux子系统需要设置登录账号和密码(个人本地使用没有必要设置！)
#### 2.运行`终端管理员`设置默认登录账号为root
    Debian config --default-user root
#### 3.更新Linux子系统
    apt update && apt upgrade -y

</details>

## 四、将Linux子系统迁出C盘
#### 1.压缩并导出Linux子系统到D盘
    wsl.exe --export Debian d:\wsl-Debian.tar
#### 2.注销当前安装的Linux发行版
    wsl.exe --unregister Debian
#### 3.将Linux子系统导入到E盘
    wsl.exe --import Debian e:\RJKJ\wsl\Debian d:\wsl-Debian.tar --version 2


## [WSL数据包下载](https://github.com/microsoft/WSL)
## [玩转WSL子系统](玩转WSL子系统.md)
