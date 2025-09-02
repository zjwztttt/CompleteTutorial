## Linux中的服务`.service`文件，以下只列出配置一版程序够用，更详细的配置请[参考](https://blog.csdn.net/blood_Z/article/details/128848056)或者[参考备份](Linux/Linux的service文件详解.md)
    [Unit]
    Description=fraps service
    After=network.target syslog.target
    Wants=network.target

    [Service]
    Type=simple
    ExecStart=/root/frp_0.51.3_linux_amd64/frps -c /root/frp_0.51.3_linux_amd64/frps.ini

    [Install]
    WantedBy=multi-user.target
