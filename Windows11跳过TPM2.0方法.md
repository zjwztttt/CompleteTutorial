## 1.修改注册表的方法
#### 转到注册表以下路径
    计算机 \HKEY_LOCAL_MACHINE\SYSTEM\Setup
#### 右键点击 Setup 文件夹选择新建项，并将其重命名为
    LabConfig
#### 双击打开 LabConfig 文件夹，点击右侧空白处新建 DWORD32 位值，将其命名为：
    BypassTPMCheck
#### 双击此项将其键值修改为
    00000001
#### 继续在右侧空白处新建 DWORD32 位值，将其重命名为
    BypassSecureBootCheck
#### 双击将其键值修改为
    00000001
#### 继续在右侧空白处新建 DWORD32 位值，将其重命名为
    BypassCpuCheck
#### 双击将其键值修改为
    00000001
#### 保存后关闭注册表，然后点击安装程序的返回箭头，重新点击下一步即可开始安装
## 2.利用Windows10引导文件安装Windows11的方法
