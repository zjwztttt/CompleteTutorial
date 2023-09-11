# 申请`.crt`和`.key`格式的证书
## Debian/Ubuntu系统执行以下命令：
    apt update -y && apt install -y curl && apt install -y socat
## CentOS系统执行以下命令：
    yum update -y && yum update -y && yum install -y socat
## 运行Acme脚本
    curl https://get.acme.sh | sh
