### 核心本质

- express 静态资源服务器
- 使用中间件做代理

```
var express = require('express');
var app = express();
var proxy = require('http-proxy-middleware');
var proxyTable = {
    '/api/**': {
        target: 'http://app.xiaochina.net',
        changeOrigin: true
    }
}
Object.keys(proxyTable).forEach(function(key){
    app.use(proxy(key,proxyTable[key]));
})

app.use(express.static('build'));
app.get('/', function (req, res) {
    res.send('Hello World!');
});

var server = app.listen(3000, function () {
    var host = server.address().address;
    var port = server.address().port;

    console.log('Example app listening at http://%s:%s', host, port);
});
```
