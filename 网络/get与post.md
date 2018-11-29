### 区别：

最直观的区别就是GET把参数包含在URL中明文传输，POST通过 body传递参数。

GET能被缓存，POST不能缓存 。

restful定义不同

浏览器堆GET和POST的长度限制不同，一般GET不超过2K。

GET产生一个TCP数据包；POST产生两个TCP数据包。
对于GET方式的请求，浏览器会把http header和data一并发送出去，服务器响应200（返回数据）；
而对于POST，浏览器先发送header，服务器响应100 continue，浏览器再发送data，服务器响应200 ok（返回数据）。
