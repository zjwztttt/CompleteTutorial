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
#### Batch脚本，隐藏桌面快捷方式小箭头
    reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\Shell Icons" /v 29 /d "%systemroot%\system32\imageres.dll,197" /t reg_sz /f
    
    taskkill /f /im explorer.exe
    
    attrib -s -r -h "%userprofile%\AppData\Local\iconcache.db"
    
    del "%userprofile%\AppData\Local\iconcache.db" /f /q
    
    start explorer
    
    Pause
#### Batch脚本，恢复桌面快捷方式小箭头
    reg delete "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\Shell Icons" /v 29 /f
    
    taskkill /f /im explorer.exe
    
    attrib -s -r -h "%userprofile%\AppData\Local\iconcache.db"
    
    del "%userprofile%\AppData\Local\iconcache.db" /f /q
    
    start explorer
    
    pause
#### Regedit脚本，将脚本黏贴到`.reg`后缀的文件中并修改脚本中的注册表项、显示名称和执行程序路径，给通过解压缩部署的绿色程序开启右键菜单的功能
    Windows Registry Editor Version 5.00
    
    [HKEY_CLASSES_ROOT\*\shell\注册表项]
    @="显示在Windows的右键菜单中的名称"
    "Icon"="执行程序的路径"
    
    [HKEY_CLASSES_ROOT\*\shell\注册表项\Command]
    @="执行程序的路径 \"%1\""
    
    [HKEY_CLASSES_ROOT\Directory\shell\注册表项]
    @="显示在Windows的右键菜单中的名称"
    "Icon"="执行程序的路径"
    
    [HKEY_CLASSES_ROOT\Directory\shell\注册表项\Command]
    @="执行程序的路径 \"%V\""
    
    [HKEY_CLASSES_ROOT\Directory\Background\shell\注册表项]
    @="显示在Windows的右键菜单中的名称"
    "Icon"="执行程序的路径"
    
    [HKEY_CLASSES_ROOT\Directory\Background\shell\注册表项\Command]
    @="执行程序的路径 \"%V\""
#### Regedit脚本，删除注册表中的项
    Windows Registry Editor Version 5.00
    
    [-HKEY_CLASSES_ROOT\*\shell\注册表项]
    [-HKEY_CLASSES_ROOT\Directory\shell\注册表项]
    [-HKEY_CLASSES_ROOT\Directory\Background\shell\注册表项]
