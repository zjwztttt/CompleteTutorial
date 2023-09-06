## 让程序在后台静默运行的脚本
#### VBS脚本，将脚本粘贴到`.vbs`后缀的文件中并修改脚本中的程序路径和启动命令
    Set ws = CreateObject("wscript.shell")
    ws.run "程序所在路径\程序名称或启动命令",vbhide
#### Batch脚本，将脚本黏贴到`.bat`后缀的文件中并修改脚本中的程序路径和启动命令
    @echo off
    if "%1" == "h" goto begin
    mshta vbscript:createobject("wscript.shell").run("""%~nx0"" h",0)(window.close)&&exit
    :begin
    REM
    cd 程序所在路径
    程序名称或启动命令
    exit
