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
#### Regedit脚本，给通过解压缩部署的绿色程序开启右键菜单的功能
    Windows Registry Editor Version 5.00
    
    [HKEY_CLASSES_ROOT\*\shell\VSCode]
    @="Open with &VSCode"
    "Icon"="E:\\RJAZ\\VSCode\\Code.exe"
    
    [HKEY_CLASSES_ROOT\*\shell\VSCode\Command]
    @="E:\\RJAZ\\VSCode\\Code.exe \"%1\""
    
    [HKEY_CLASSES_ROOT\Directory\shell\VSCode]
    @="Open with &VSCode"
    "Icon"="E:\\RJAZ\\VSCode\\Code.exe"
    
    [HKEY_CLASSES_ROOT\Directory\shell\VSCode\Command]
    @="E:\\RJAZ\\VSCode\\Code.exe \"%V\""
    
    [HKEY_CLASSES_ROOT\Directory\Background\shell\VSCode]
    @="Open with &VSCode"
    "Icon"="E:\\RJAZ\\VSCode\\Code.exe"
    
    [HKEY_CLASSES_ROOT\Directory\Background\shell\VSCode\Command]
    @="E:\\RJAZ\\VSCode\\Code.exe \"%V\""
