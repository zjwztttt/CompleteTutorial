# 申请`.crt`和`.key`格式的证书
## Debian/Ubuntu系统执行以下命令：
    apt update -y && apt install -y curl && apt install -y socat
## CentOS系统执行以下命令：
    yum update -y && yum update -y && yum install -y socat
## 运行Acme脚本
    curl https://get.acme.sh | sh
## 申请证书及密钥
##### 【将代码中注释的邮箱和域名，改为你自己的】
    ~/.acme.sh/acme.sh --register-account -m xxxx@gmail.com
    ~/.acme.sh/acme.sh  --issue -d 输入你的域名  --standalone
## 下载证书及密钥
    ~/.acme.sh/acme.sh --installcert -d 输入你的域名 --key-file /root/private.key --fullchain-file /root/cert.crt
# 申请`.pem`格式的证书
## 安装OpenSSL
    apt update -y && apt full-upgrade && apt install -y openssl
## 申请证书
    openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -days 365
