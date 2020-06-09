#### 当浏览器发起复杂请求，浏览器会先对服务器发起一次预检请求，也就是options，确定服务器是否允许跨域，如果允许，浏览器会发起第二次请求。

##### 简单请求：

> 满足以下2个条件

条件一，请求方法是以下方法之一

- HEAD
- POST
- GET

条件二，头信息不超过以下几种字段

- Accept
- Accept-Language
- Content-Language
- Last-Event-ID
- Content-Type：只限于三个值application/x-www-form-urlencoded、multipart/form-data、text/plain

##### 复杂请求：

> 非简单请求



###### 参考资料

[面试官：说说你对 options 请求的理解](https://mp.weixin.qq.com/s/uVgoaejZ9Iymbrvc9GECWQ)

[MDN参考链接](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Methods/OPTIONS)