# mongoDB

## 下载安装

1. 配置mongo 的yum源

```
cd /etc/yum.repos.d 
vim mongodb-org-4.0.repo 
```
输入
```
[mngodb-org]
name=MongoDB Repository
baseurl=http://mirrors.aliyun.com/mongodb/yum/redhat/7Server/mongodb-org/4.0/x86_64/
gpgcheck=0
enabled=1
```

更新

```
 yum update
```

安装

```
yum -y install mongodb-org
```

查看

```
whereis mongod
```
修改配置
```
vim /etc/mongod.conf
```
bindIp: 172.0.0.1  改为 bindIp: 0.0.0.0



## 启动

- 启动
```
systemctl start mongod.service

```

- 停止

```
systemctl stop mongod.service
```

- 查看状态

```
systemctl status mongod.service
```

- 开机启动

```
systemctl enable mongod.service
```


### 外网访问，关闭防火墙

CentOS 7.0默认使用的是firewall作为防火墙，这里改为iptables防火墙。
关闭firewall：
systemctl stop firewalld.service #停止firewall
systemctl disable firewalld.service #禁止firewall开机启动

vim /etc/sysconfig/iptables

iptables文件添加

-A INPUT -m state --state NEW -m tcp -p tcp --dport 27017 -j ACCEPT

> 重启防火墙
```
service iptables restart
```



300M =>500M



```
mongo --host localhost --port 27017  // 测试本连接

mongo --host 10.0.0.167 --port 27017 // 测试远程， 防火墙，端口  0.0.0.0  
```