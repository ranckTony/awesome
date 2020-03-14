# 开启http2的实操流程

### 版本要求：
- [nginx 1.9.5+](http://nginx.org/)
- [OpenSSL 1.0.2+](https://www.openssl.org/)

### 生成证书

temp：这个流程的含义还需要继续深挖

```
openssl genrsa -des3 -out server.key 2048

openssl rsa -in server.key -out server.key

openssl req -new -x509 -key server.key -out ca.crt -days 3650

openssl req -new -key server.key -out server.csr

openssl x509 -req -days 3650 -in server.csr -CA ca.crt -CAkey server.key -CAcreateserial -out server.crt

cat server.key server.crt > server.pem

```


### 重新生成nginx程序

1. 下载，解压，进入解压后的源码路径，例如： /usr/local/nginx-1.16.1
```
wget http://nginx.org/download/nginx-1.16.1.tar.gz

tar -xzvf nginx-1.16.1.tar.gz

cd nginx-1.16.1
```
2. 执行配置，需要带参数 http_v2_module http_ssl_module 
```
./configure --prefix=/usr/local/nginx  --with-http_v2_module --with-http_ssl_module 
```
3. 执行make，**注意：make执行完毕后不需要make install，以免覆盖**
```
make
```
4. 备份原有./sbin/nginx 程序(自己切换目录或其他)
```
cp /usr/local/nginx/sbin/nginx /usr/local/nginx/sbin/nginx.back
```
5. copy /usr/local/nginx-1.16.1/objs下生成的nginx程序到院nginx安装目录下
```
copy /usr/local/nginx-1.16.1/objs/nginx /usr/local/nginx/sbin/
```
6. 查看配置模块
```
/usr/local/nginx/sbin/nginx -V

```
命令行中显示，其中 configure arguments 后面就是生成nginx程序时附加的模块
> nginx version: nginx/1.16.1
built by gcc 4.8.5 20150623 (Red Hat 4.8.5-39) (GCC) 
built with OpenSSL 1.0.2k-fips  26 Jan 2017
TLS SNI support enabled
configure arguments: --prefix=/usr/local/nginx --with-http_v2_module --with-http_ssl_module



### nginx配置

```
server {
    listen 443 ssl http2;

    ssl_certificate server.crt;
    ssl_certificate_key server.key;
}
```

注意： 把以前的 
```
ssl on;
```
删掉，在listen中写


### 常见错误

> nginx: [warn] the "ssl" directive is deprecated, use the "listen ... ssl" directive instead in /usr/local/nginx/conf/nginx.conf:40



