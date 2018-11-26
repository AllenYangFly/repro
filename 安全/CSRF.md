https://github.com/dwqs/blog/issues/68

> 跨站请求伪造

1. 受害者登录a.com，并保留了登录凭证（Cookie）。
2. 攻击者引诱受害者访问了b.com。
3. b.com 向 a.com 发送了一个请求：a.com/act=xx。浏览器会…
4. a.com接收到请求后，对请求进行验证，并确认是受害者的凭证，误以为是受害者自己发送的请求。
5. a.com以受害者的名义执行了act=xx。

### 攻击方式

get -> 图片/链接

post -> 伪造form

### 防御
> CSRF（通常）发生在第三方域名。
CSRF攻击者不能获取到Cookie等信息，只是使用。

阻止不明外域的访问:
* Origin Header
* Referer Header

敏感信息验证码: 

token: 
1. 用户打开页面的时候，服务器需要给这个用户生成一个Token，该Token通过加密算法对数据进行加密，输出到前端页面。
2. Token存在服务器的Session中
3. 之后的请求，要带上这个token


token可以在产生并放于Session之中，然后在每次请求时把Token从Session中拿出，与请求中的Token进行比对，但这种方法的比较麻烦的在于如何把Token以参数的形式加入请求。
