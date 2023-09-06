## 让程序在后台静默运行的脚本
#### VBS脚本，将脚本粘贴到`.vbs`后缀的文件中并修改脚本中的程序路径和启动命令
    Set ws = CreateObject("wscript.shell")
    ws.run "E:\RJAZ\alist-windows-amd64\alist.exe server",vbhide
