### 下载安装

[nginx 下载](http://nginx.org/en/download.html)

[linux下安装](http://www.nginx.cn/install)




### 常用指令

  ```
 /usr/local/webserver/nginx/sbin/nginx -s reload            # 重新载入配置文件
/usr/local/webserver/nginx/sbin/nginx -s reopen            # 重启 Nginx
/usr/local/webserver/nginx/sbin/nginx -s stop              # 停止 Nginx
  ```
  
  
  ### 主要配置
  
  > 代理地址
  
  ```
  
  ```
  
  > gzip 压缩
  
  ```
    gzip on; 

  ```

### 配置案例

```
server {
  listen 8080;
  server_name 20.20.20.20;

  location / {
    root /home/html;
    try_files $uri $uri/ /index.html;
  }

  location /api {
    proxy_paas http://20.110.2.3/api;
  }

  location /auth {
    proxy_paas http:/www.auth.com/auth;
  }
}

```
