## Linux中的服务`.service`文件，以下只列出配置一版程序够用，更详细的配置请[参考](https://blog.csdn.net/blood_Z/article/details/128848056)或者[参考备份](https://github.com/zjwztttt/CompleteTutorial/blob/main/Linux%E7%9A%84service%E6%96%87%E4%BB%B6%E8%AF%A6%E8%A7%A3.md)
    [Unit]
    Description=fraps service
    After=network.target syslog.target
    Wants=network.target

    [Service]
    Type=simple
    ExecStart=/root/frp_0.51.3_linux_amd64/frps -c /root/frp_0.51.3_linux_amd64/frps.ini

    [Install]
    WantedBy=multi-user.target
