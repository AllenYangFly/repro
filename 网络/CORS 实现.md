https://ruby-china.org/topics/28998
https://www.rails365.net/articles/cors-jin-jie-zhi-preflight-qing-qiu-er
https://www.rails365.net/articles/cors-jin-jie-zhi-she-zhi-qing-qiu-tou-xin-xi-san
https://www.rails365.net/articles/cors-jin-jie-zhi-cookie-chu-li-si
https://www.rails365.net/articles/cors-jin-jie-expose-headers-wu

> 为什么把CORS跨域技术单独拿出来讲？因为CORS是目前公司使用最广泛的方案。

### 跨域

同源策略: 协议、域名、端口

![](https://l.ruby-china.com/photo/2016/f9c96332fada251f48632297ccf73d5b.png)


### CORS过程

1. 浏览器发送跨域请求 -> server 请求头中会有一个origin的字段标明请求来源
2. 服务器应答后
3. 如果请求相应头中没有设置，Access-Control-Allow-Origin： '*'


### 跨域获取cookie

1. 前端设置withCredentials : true
2. Access-Control-Allow-Credentials: true

### 特定域名

1. 在nginx中设置域名的访问，限定header中'Access-Control-Allow-Origin'字段的结果。

### 预检查请求( preflight ）

PUT或DELETE这种非简单请求，请求前会先发送一个 OPTIONS 的预检查请求。

先询问服务器是否支持DELETE方法，再用响应头信息的方式返回给浏览器。浏览器根据响应信息查看服务器是否支持DELETE方法，如果支持的话，就再发起真实的DELETE方法，不支持就报错了。

1. 设置'Access-Control-Allow-Methods'： 'GET, POST, OPTIONS, DELETE';