# http协议

### 七层网络模型

- 物理层 定义物理设备网卡端口网线怎么传输数据
- 数据链路层 0 1传输数据
- 网络层 逻辑链路，找到目标
---
- 传输层 tcp/ip协议 udp  端到端服务，数据分片、传输、组装
- 应用层 http协议


### http历史

1. http /0.9
  - get请求
  - 无header信息
  - 数据传输完毕立刻关闭

2. http /1.0
  - 新增大量method
  - header
  - state code
  - 缓存
  - 字符集
  - 权限

3. http /1.1（https）
  - 持久连接
  - pipline-同一个连接发送多个请求
  - host（同一个物理服务器里面多个服务）

4. http2 (未普及)
数据二进制帧传输，头信息压缩，推送

### 三次握手

1. syn=1 seq=x 
2. syn=1,ack=x=1,seq=y
3. ack=y+1,seq=z

- syn 序号
- ack确认序号

目的防止服务器开启太多不必要的连接
第三次的目的在于确认客户端有收到服务端发送的信息，避免丢包超时问题


### uri url urn

统一资源标识符
统一资源定位符
统一资源命名

### http报文格式

```
curl -v http://www.baidu.com
```


### http访问控制 CORS 跨域资源共享

浏览器的安全策略，

```
Access-Control-Allow-Origin
```

简单请求


cors 预请求

get post header不需要预请求

content-type不属于
- application/x-www-form-urlencoded
- multipart/form-data
- text/plain

```
Access-Control-Allow-Origin: http://foo.example
Access-Control-Allow-Methods: POST, GET, OPTIONS
Access-Control-Allow-Headers: X-PINGOTHER, Content-Type
Access-Control-Max-Age: <s>  // 多少秒内不需要发送预请求
```