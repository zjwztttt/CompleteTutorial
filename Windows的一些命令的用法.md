## 1.安装系统时在提示未连接到网络的界面找不到“我没有网络可连接”的按钮
#### 在“未连接到网络”界面点按键盘上的`Shift`和`F10`键，在打开的命令提示符窗口中输入以下命令，然后系统会自动重启
    oobe\bypassnro

## 2.设置应用程序在Windows开机的时候自动启动
#### 在`运行`输入框中输入以下这条命令点击确定后会打开一个文件夹，将任何可执行程序的快件方式添加到这个文件夹中就能实现开机自动启动
    shell:startup

## 3.将应用程序添加到右键菜单中的“发送到”选项卡中
#### 在`运行`输入框中输入以下这条命令点击确定后会打开一个文件夹，将任何可执行程序的快捷方式添加到这个文件夹中就能实现右键菜单发送到
    shell:sendto

## 4.将应用程序添加到开始菜单中
#### 在`运行`输入框中输入以下这条命令点击确定后会打开一个文件夹，将任何可执行程序的快捷方式添加到这个文件夹中就能出现在开始菜单中
    shell:Programs

## 5.打开用户文件夹
#### 在`运行`输入框中输入以下这条命令点击确定后会打开当前登录账号的文件夹
    %UserProfile%
