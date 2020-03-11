# nginx专栏

### 安装

### 配置

### 启动

```
 /usr/local/nginx/sbin/nginx -c /usr/local/nginx/conf/nginx.conf
```
### 重启

```
 /usr/local/nginx/sbin/nginx -s reload /usr/local/nginx/conf/nginx.conf
```

### 关闭

```
 /usr/local/nginx/sbin/nginx -s quit  // 从容关闭，当前工作完成后关闭
  /usr/local/nginx/sbin/nginx -s stop // 瞬间关闭

```

### 热启动