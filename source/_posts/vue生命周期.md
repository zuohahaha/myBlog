---
title: vue生命周期
date: 2020-07-06 13:42:29
tags:
---

钩子函数 | 发生什么
---|---
beforeCreate | 初始化vue默认生命周期函数和默认事件
created | data、methods初始化完毕
beforeMount | 模板在内存中等待渲染到页面
mounted | vue初始化完毕，已经将Dom渲染到页面
beforeUpdate | 页面dom还是旧的，data中的数据是新的
更新之间 | 执行diff算法，将最新data生成一个dom树到内存中，然后将这个dom树跟页面dom对比，差量更新dom渲染到页面
updated | 页面dom及data都是新的
beforeDestroy | data、methods可用
destroyed | data、methods不可用



