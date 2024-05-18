## Windows Subsystem for Linux 安装教程

## 一、启用“适用于Linux的Windows子系统”功能
#### 1.在windows任务栏中的搜索框里搜索并打开`启用或关闭windows功能`
#### 2.向下滑动列表找到并勾选`适用于Linux的Windows子系统`，然后点击确定
#### 3.等待功能启用完成后点击`立即重新启动`

## 二、下载安装Linux子系统
### 方案一
#### 1.打开`Microsoft Store`
#### 2.搜索并下载`Debian`
#### 3.更新WSL到最新版
### 方案二
#### 1.以管理员身份运行`终端`
#### 2.列出可以安装的Linux子系统的发行版
    wsl.exe -l -o
#### 3.下载并安装`Debian`
    wsl.exe --install Debian
### 方案三
#### 1.下载[Linux子系统安装包](https://learn.microsoft.com/en-us/windows/wsl/install-manual#downloading-distributions)
#### 2.打开`终端`并进入安装包所在的文件夹
#### 3.安装`Debian`
    Add-AppxPackage .\Debian.appx

## 三、配置使用Linux子系统
#### 1.首次打开Linux子系统需要设置登录账号和密码(个人本地使用没有必要设置！)
#### 2.打开`终端`设置默认登录账号为root
    sudo -i
#### 3.


## [WSL数据包下载](https://github.com/microsoft/WSL)
## [玩转WSL子系统](玩转WSL子系统.md)
