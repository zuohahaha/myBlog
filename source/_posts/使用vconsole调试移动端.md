---
title: '''使用vconsole调试移动端'''
date: 2020-06-17 15:39:37
tags: 经验
---

#### 移动端调试js库 vconsole


```
<script src="js/vconsole.min.js" type="text/javascript" charset="utf-8"></script>
```
	
```
// 初始化vConsole

window.vConsole = new window.VConsole({
			defaultPlugins: ['system', 'network', 'element', 'storage'], // 可以在此设定要默认加载的面板
			maxLogNumber: 1000,
			onReady: function() {
				// console.log('vConsole is ready.');
			},
			onClearLog: function() {
				// console.log('on clearLog');
			}
		});
```
