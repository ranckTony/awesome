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
  - 数据二进制帧传输
  - 头信息压缩
  - 推送

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
- multipart/form-data 二进制
- text/plain

```
Access-Control-Allow-Origin: http://foo.example
Access-Control-Allow-Methods: POST, GET, OPTIONS
Access-Control-Allow-Headers: X-PINGOTHER, Content-Type
Access-Control-Max-Age: <s>  // 多少秒内不需要发送预请求
```

### http缓存

```
Cache-Control: private
```

- private 只有请求者可以缓存 
- public 任何代理都可以缓存
- no-store 不缓存，永远在服务端那最新的数据
- no-cache 验证缓存，可以使用缓存，但是需要在服务器验证

```
Cache-Control: max-age=31536000 // 缓存多少秒，浏览器缓存，（url不变的情况）不会向服务端发送请求的

s-maxage // 只有代理服务器中才有效
```

#### 重新验证
```
Cache-control: must-revalidate // max-age失效 原服务端缓存验证
```

#### 缓存验证

- Last-Modified
- ETag

上次修改时间，请求里面带If-modified-Sence

### session 和 cookie

- 不能跨域设置cookie
- session实现可以通过cookie或者其它方式实现
- httpOnly，禁止客户端读取cookie
- max-age
- domain设置cookie的域
- 同源请求中request将cookie拼接成字符串传到服务器

### http长连接

一个tcp连接中进行多个http请求减少三次握手的开销，可设置超时断开
chrome允许并发六个tcp连接

```
Connection: keep-alive | close
```

http2 信道复用，一个tcp一切ok
www.google.com 做到了

### http数据协商

> 客服端要求
- Accept 申明想要的数据类型
- Accep-Encoding  编码压缩方式
- Accept-Language 语言
- User-Agent 客户端

> 服务端返回
- Content-Type
- Content-Encoding
- Content-language


Vary 指定一个请求头，控制缓存
header-name
User-Agent 

### 重定向

301 永久重定向，缓存在浏览器
302 临时重定向

### 内容安全策略 CSP

```
 Content-Security-Policy
```

xss 脚本注入攻击，富文本编辑器中插入脚本

```
Content-Security-Policy: default-src https:

Content-Security-Policy-Report-Only: default-src https:; report-uri /csp-violation-report-endpoint/
```


### https

- 公钥
- 私钥（服务器上）

握手的时候传输公钥

三个随机数生成主密钥进行传输数据加密

客户端，随机数，加密套件
服务端，公钥，随机数
客户端 加密随机数


#### 用nignx部署https服务

https 默认端口 443

chrome 认为权威机构签发的证书才算安全


#### http2

- 信道复用
- 分帧传送
- server push 服务端推送

