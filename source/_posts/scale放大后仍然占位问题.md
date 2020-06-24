---
title: scale放大后仍然占位问题
date: 2020-06-24 11:43:19
tags:
---
1.给当前元素添加个外层容器

2.设置外层容器的宽高

3.给当前元素设置

```
transform-origin: left top;
```


示例


```
.pie-block{
	width: 0.6rem;
	height: 0.6rem;
}
.pie {
	width: 6rem;
	height: 6rem;
	border-radius: 50%;
	background: #fff;
	border: 10px solid #F93B00;
	background-image: -webkit-linear-gradient(left, transparent 50%, #F93B00 0);
	background-image: linear-gradient(to right, transparent 50%, #F93B00 0);
	margin: 0 0.25rem 0 0.5rem;
	transform: scale(0.1);
	transform-origin: left top;
}
```
