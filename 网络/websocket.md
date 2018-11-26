webSocket 是一个持久化协议，它基于TCP传输协议，并复用HTTP的握手通道。

1、客户端发送GET 请求， upgrade
2、服务器给客户端 switching protocol
3、就进行了webSocket的通信了

### 如何建联

1. 客户端：申请协议升级
    客户端发起协议升级请求。采用的是标准的HTTP报文格式，且只支持GET方法。请求头中Sec-WebSocket-Key

2. 服务器端: 响应协议升级
    服务器端返回状态代码101表示协议切换，根据Sec-WebSocket-Key，经过`SHA-1`和`base64`编码返回Sec-WebSocket-Accept

3. 一旦服务器发送这个请求头，握手就完成了，你可以开始交换数据！

### 建联逻辑
```javascript
  var ws = new WebSocket('ws://localhost:8080');
  ws.onopen = function () {
    console.log('ws onopen');
    ws.send('from client: hello');
  };
  ws.onmessage = function (e) {
    console.log('ws onmessage');
    console.log('from server: ' + e.data);
  };
  ws.onClose = function (e) {
    console.log('ws onmessage');
    console.log('from server: ' + e.data);
  }
```

### 心跳
在经过握手之后的任意时刻里，无论客户端还是服务端都可以选择发送一个pings给另一方。 当pings消息收到的时候，接受的一方必须尽快回复一个有相同载荷数据的pongs消息。
