# nodejs中获取请求参数

**req.body、req.query、req.params、req.param()**

### 1. req.body
> 需引入body-parser

    接收post传值
<!--more-->
### 2. req.query
> nodejs自带，无需引入

    接收get传参

    示例：/app/user/:id

### 3. req.params
> nodejs自带

    接收restful风格参数

    示例：/app/user/:id

### 4.req.param()
> 已弃用
