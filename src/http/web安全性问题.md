# web安全性问题

### 常见的攻击方式

- XSS  站脚本攻击（Cross Site Scripting）
  - javascript 脚本注入
  - 窃取cookie
  - 改变dom，恶意广告，恶意连接，打开大量窗口
  - 乱发请求，大访问量的网站攻击小网站，插入一个 img src
  - 
- 


- 系统IP和cookie绑定。
- HTTPonly的cookie
- http CSP 内容安全策略，指定特定路径脚本
- 基于代码的处理，过滤掉 script ，要递归过滤
- 使用转码