---
title: css实现饼图百分比
date: 2020-06-24 11:42:40
tags:
---

```
<div class="pie-block">
    <div class="pie">
    	<!-- 如果学习进度低于50%，下发style设置成这样，rotate内是学习的进度 transform: rotate(0.1turn);
    	如果学习进度高于50% 需要用1减去学习进度然后将得到的数字写到rotate里面 需要设置成这样 transform: rotate(0.1turn);background-color:#F93B00  -->
    	<div class="pie-child" style="transform: rotate(0.3turn);">
    	</div>
    </div>
</div>
```


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

.pie-child {
	content: '';
	display: block;
	margin-left: 50%;
	height: 100%;
	border-radius: 0 100% 100% 0/50%;
	background-color: inherit;
	-webkit-transform-origin: left;
	transform-origin: left;
	-webkit-transform: rotate(.5turn);
	transform: rotate(.5turn);
}
```

##### 原理：

父元素设置渐变色，子元素为一个半圆，盖在父元素一端，通过子元素旋转来模拟百分比饼图，子元素高于50%时需要颠倒父元素渐变色。

