https://juejin.im/post/5ad6ad575188255c272273c4
http://www.ruanyifeng.com/blog/2014/09/illustration-ssl.html

![](https://upload-images.jianshu.io/upload_images/449687-4e2ec739a1487779?imageMogr2/auto-orient/)

![](https://user-gold-cdn.xitu.io/2018/5/21/1638197d96d391ca?imageslim)

> https类似于http。只不过是数据利用了 SSL/TSL 加密

1. 请求服务器，告诉他我是https
2. 服务器返回一个使用证书，证书里有 签名、服务器公钥（都使用权威机构私钥进行加密）+ 服务厂商信息
3. 浏览器根据自带的三方权威机构公钥解密，拿到签名，通过算法校验签名的合法性
4. 浏览器自己生成一个对称秘钥K，用服务器的公钥进行加密
5. 服务器通过秘钥解密，拿到秘钥K
6. 之后使用秘钥K，加密数据进行传输