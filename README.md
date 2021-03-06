# xsec-ssh-firweall

xsec-ssh-firewall为一个简易的SSH密码防暴力破解程序，通过读取SSH的`auth.log`判断恶意IP，执行`iptables`进行封杀。本项目采用Go语言开发。

## 使用方法

设置好配置文件`conf/app.ini`后直接启动`./ssh_firewall`即可。

建议使用`supvervisor`或`nohup`将其跑在后台。

```ini
INTERFACE       = eth0
BLOCKTIME       = 60
WHITE_IPLIST    = 127.0.0.1,8.8.8.8,4.4.4.4,10.10.10.20

[logs]
sshd_log        = /var/log/ 
```

### 配置文件说明：

1. INTERFACE表示外网的网卡名
1. BLOCKTIME表示对暴力破解来源IP的封禁时间，单位为分钟
1. WHITE_IPLIST为白名单，防止自己连续3次输错密码后无法登录服务器
1. sshd_log为ssh log的位置，保持默认即可

## 使用效果截图：

![](https://docs.xsec.io/images/ssh-firewall/ssh-firewall.png)
