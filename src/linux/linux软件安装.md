# linux 软件安装


### 源码安装

- 下载源码
- 解压
- 配置
- 编译
- 安装



```
wget http://nginx.org/download/nginx-1.9.9.tar.gz  

tar -zxvf  nginx-1.9.9.tar.gz


./configure
 
make
 
make install

```



> 通常安装在 /usr/local 目录下



### yum 安装

Yum（全称为Yellow dog Updater, Modified）是一个在Fedora和RedHat以及CentOS中的Shell前端软件包管理器。 基于RPM包管理，能够从指定的服务器自动下载RPM包并且安装，可以自动处理依赖性关系，并且一次安装所有依赖的软件包

```
yum -y install wget
```
