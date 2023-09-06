xxx.service 文件配置详解
.service文件是用来注册systemctl管理的服务所需要的配置文件

[Unit]
Description给出当前服务的简单描述。
Documentation给出文档位置。
After表示在什么服务之后启动。
Before表示在什么服务之前启动。
Wants表示该服务和某服务存在某种弱依赖关系，即某服务停止运行或退出不影响该服务继续运行。
Requires则表示”强依赖”关系，即某服务停止运行或退出，改服务也必须停止运行。
Wants与Requires只涉及依赖关系，与启动顺序无关，默认情况下是同时启动的。
Conflicts：代表冲突的服务，即这个项目后面接的服务如果有启动，那么我们这个 unit 本身就不能启动，我们 unit 有启动，则此项目后的服务就不能启动，就是冲突性的检查。
注意：After和Before只涉及启动顺序，不涉及依赖关系。

[Service]
Type ：定义启动类型

simple（默认值）：ExecStart启动的进程为主进程
forking：ExecStart将以fork()方式启动，此时父进程将会退出，子进程将成为主进程
oneshot：类似于simple，但只执行一次，Systemd 会等它执行完，才启动其他服务
dbus：类似于simple，但会等待 D-Bus 信号后启动
notify：类似于simple，启动结束后会发出通知信号，然后 Systemd 再启动其他服务
idle：类似于simple，但是要等到其他任务都执行完，才会启动该服务。一种使用场合是为让该服务的输出，不与其他服务的输出相混
ExecStart：定义启动进程时执行的命令，就是手动启动时执行的命令。

ExecReload：重启服务时执行的命令。

ExecStop：停止服务时执行的命令。

ExecStartPre：启动服务之前执行的命令。

ExecStartPost：启动服务之后执行的命令。

ExecStopPost：停止服务之后执行的命令。

killmod：定义 Systemd 如何停止 sshd 服务。

control-group（默认值）：当前控制组里面的所有子进程，都会被杀掉
process：只杀主进程
mixed：主进程将收到 SIGTERM 信号，子进程收到 SIGKILL 信号
none：没有进程会被杀掉，只是执行服务的 stop 命令
Restart：定义了 sshd 退出后，Systemd 的重启方式。

no（默认值）：退出后不会重启
on-success：只有正常退出时（退出状态码为0），才会重启
on-failure：非正常退出时（退出状态码非0），包括被信号终止和超时，才会重启
on-abnormal：只有被信号终止和超时，才会重启
on-abort：只有在收到没有捕捉到的信号终止时，才会重启
on-watchdog：超时退出，才会重启
always：不管是什么退出原因，总是重启
对于守护进程，推荐设为on-failure。对于那些允许发生错误退出的服务，可以设为on-abnormal。

RestartSec：表示 Systemd 重启服务之前，需要等待的秒数。

user可以设置服务的用户名

WorkingDirectory指定服务的安装目录

RemainAfterExit：当设置为 RemainAfterExit=1 时，则当这个 daemon 所属的所有程序都终止之后，此服务会再尝试启动。这对于Type=oneshot 的服务很有帮助

TimeoutSec： 若这个服务在启动或者是关闭时，因为某些缘故导致无法顺利 “ 正常启动或正常结束” 的情况下，则我们要等多久才进入 “ 强制结束 ” 的状态！

EnvironmentFile：可以指定启动脚本的环境配置文件！例如 sshd.service 的配置文件写入到/etc/sysconfig/sshd 当中！你也可以使用 Environment= 后面接多个不同的Shell 变量来给予设置

[Install]
WantedBy：表示该服务所在的 Target。 Target的含义是服务组，表示一组服务。WantedBy=multi-user.target指的是服务所在的Target是multi-user.target。

Systemd 默认的启动 Target就是multi-user.target，在这个组里的所有服务，都将开机启动。
查看 multi-user.target 包含的所有服务：

 systemctl list-dependencies multi-user.target
1
Also：当目前这个 unit 本身被 enable 时， Also 后面接的 unit 也请 enable。 也就是具有相依性的服务可以写在这里。

Alias：进行一个链接的别名，当 systemctl enable 相关的服务时则此服务会进行链接文件的创建，以multi-user.target 为例，这个组是用来作为默认操作环境default.target 的规划，因此当你设置成 default.target时，这个/etc/systemd/system/default.target 就会链接到/usr/lib/systemd/system/multi-user.target。
————————————————
版权声明：本文为CSDN博主「万山寒」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/blood_Z/article/details/128848056
