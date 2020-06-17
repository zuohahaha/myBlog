---
title: Object.is()'
date: 2020-06-17 15:40:43
tags:
---


##### 相同：

都是严格比较

##### 不同：


```
-0 === +0  //true
```



```
Object.is(-0,+0) //false
```




```
NaN === NaN  //false
```



```
Object.is(NaN,NaN) //true
```
