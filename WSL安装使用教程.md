## Windows Subsystem for Linux 安装教程

## 一、启用“适用于Linux的Windows子系统”功能(方案二可跳过)
#### 1.在windows任务栏中的搜索框里搜索并打开`启用或关闭windows功能`
#### 2.向下滑动列表找到并勾选`适用于Linux的Windows子系统`，然后点击确定
#### 3.等待功能启用完成后点击`立即重新启动`

## 二、下载安装Linux子系统
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

## 三、配置使用Linux子系统
#### 1.首次打开Linux子系统需要设置登录账号和密码(个人本地使用没有必要设置！)
#### 2.运行`终端管理员`设置默认登录账号为root
    Debian config --default-user root
#### 3.更新Linux子系统
    apt update && apt upgrade -y
## 四、将Linux子系统迁出C盘
#### 1.压缩并导出Linux子系统到D盘
    wsl.exe --export Debian d:\wsl-Debian.tar
#### 2.注销当前安装的Linux发行版
    wsl.exe --unregister Debian
#### 3.将Linux子系统导入到E盘
    wsl.exe --import Debian e:\RJKJ\wsl\Debian d:\wsl-Debian.tar --version 2

<details markdown="1"> <summary><h3>智能代理国内和被墙网站</h3>（点击这里）</summary>
 
您可以使用 Hiddify-Next 客户端，或者直接在 Hiddify-Manager 面板中，使用以下 3 种模式连接到互联网。
1. 仅通过代理连接被封锁的网站。
2. 通过代理连接除中国、俄罗斯、伊朗等国内网站外的所有网站。这样就可以不用代理打开国内网站了（推荐）
3. 通过代理连接所有网站。

同时，以上解决方案也可以抵抗 Internet 过滤实体的检测，并防止对服务器的常见攻击，即检测的可能性很小，但是，不要忘记了禁用除 22、80 和 443 之外的其他端口。  

</details>

## [WSL数据包下载](https://github.com/microsoft/WSL)
## [玩转WSL子系统](玩转WSL子系统.md)
