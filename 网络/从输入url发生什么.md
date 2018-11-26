https://kmknkk.xin/2018/03/04/%E5%BD%93%E6%88%91%E4%BB%AC%E5%9C%A8%E6%B5%8F%E8%A7%88%E5%99%A8%E4%B8%AD%E8%BE%93%E5%85%A5%E4%B8%80%E4%B8%AAURL%E5%90%8E%EF%BC%8C%E5%8F%91%E7%94%9F%E4%BA%86%E4%BB%80%E4%B9%88%EF%BC%9F/
https://segmentfault.com/a/1190000006879700#articleHeader3


### DNS查询

    1 浏览器缓存 – 浏览器会缓存DNS记录一段时间。
    2 系统缓存 – 如果在浏览器缓存里没有找到需要的记录，浏览器会做一个系统调用
    3 向域名服务器发送请求 - 从.com顶级域名服务器到baidu的域名服务器。

浏览器缓存，系统缓存，路由器缓存，IPS服务器缓存，根域名服务器缓存，顶级域名服务器缓存，主域名服务器缓存

### 建立TCP连接
![](https://user-gold-cdn.xitu.io/2017/11/9/d8bf92c7906718271fdb8b0d2d5fe5b4?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

标志位SYN

Seq序号

确认序号ACK

第一次握手：建立连接时，客户端发送syn包(syn=j)到服务器，并进入SYN_SENT状态，等待服务器确认；

第二层握手：服务器接收到syn包，必须确认客户端的SYN(ack=j+1)，同时自己也发送一个SYN包(syn=k)，即SYN+ACK包，此时服务器进入SYN_RECV状态；

第三次握手：客户端收到服务器的SYN_ACK包，向服务器发送确认包ACK(ack=k+1)，此包发送完毕，客户端和服务器进入ESTABLISHED(TCP连接成功)状态，完成三次握手。

经过三次握手建立TCP连接，TCP三次握手的的好处在于：发送方可以确认接收方仍然在线，不会因为白发送而浪费资源。

### 浏览器发送HTTP请求

### 服务器处理请求并返回HTTP报文

### 浏览器渲染

### js脚本执行