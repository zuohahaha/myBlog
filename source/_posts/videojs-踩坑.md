---
title: '''videojs-踩坑'''
date: 2020-06-17 15:40:18
tags: 经验
---

初始化videojs
		
```
var myPlayer = videojs('my-video', {
	//设置倍速播放
	playbackRates: [0.5, 0.75, 1, 1.25, 2],
	// 重新设置播放条按钮顺序
	controlBar: {
		children: [
			'playToggle', 'volumePanel', 'currentTimeDisplay', 'progressControl', 'timeDivider', 'durationDisplay',
			'liveDisplay', 'seekToLive', 'remainingTimeDisplay', 'customControlSpacer', 'playbackRateMenuButton',
			'chaptersButton', 'descriptionsButton', 'subsCapsButton', 'audioTrackButton', 'fullscreenToggle'
		]
	}
	// currentTimeDisplay: true, // 当前时间
	// timeDivider: true, // 时间分割线
	// durationDisplay: true, // 总时间
	// progressControl: true, // 进度条
	// remainingTimeDisplay: false, //
	// customControlSpacer: true, //
	// fullscreenToggle: true, // 全屏按钮
	// volumePanel: false
});
```

通过css设置，显示时间，隐藏斜杠/

```
.video-js .vjs-current-time, .vjs-no-flex .vjs-current-time {
	display: block;
}
.video-js .vjs-duration, .vjs-no-flex .vjs-duration{
	display: block;
}

.vjs-remaining-time.vjs-time-control.vjs-control{
	display: none;
}
```

 启用x5内核，微信端使用x5内核，设置后播放不会全屏
 
```
x5-video-player-type="h5"
```
			
播放器方向  landscape横屏，portraint竖屏  默认竖屏

```
x5-video-orientation="portraint"
```
> webkit-playsinline和playsinline: 视频播放时局域播放，不脱离文档流 。

播放器填充

```
style="object-fit:fill"
```

AirPlay功能可以实现影音文件的无线播放--ios

```
x-webkit-airplay="allow"
```
 
是否支持全屏

```
x5-video-player-fullscreen:"true"
```


videojs 事件汇总

// 监听videojs加载完成
```
videojs("my-video").ready(function() {
	console.log("加载完毕")
	var myPlayer = this;
	myPlayer.play();


	this.on("loadstart", function() {
		console.log("开始请求数据 ");
	})
	this.on("progress", function() {
		console.log("正在请求数据 ");
	})
	this.on("loadedmetadata", function() {
		console.log("获取资源长度完成 ")
	})
	this.on("canplaythrough", function() {
		console.log("视频源数据加载完成")
	})
	this.on("waiting", function() {
		console.log("等待数据")
	});
	this.on("play", function() {
		console.log("视频开始播放")
	});
	this.on("playing", function() {
		console.log("视频播放中")
	});
	this.on("pause", function() {
		console.log("视频暂停播放")
	});
	this.on("ended", function() {
		console.log("视频播放结束");
	});
	this.on("error", function() {
		console.log("加载错误")
	});
	this.on("seeking", function() {
		console.log("视频跳转中");
	})
	this.on("seeked", function() {
		console.log("视频跳转结束");
	})
	this.on("ratechange", function() {
		console.log("播放速率改变")
	});
	this.on("timeupdate", function() {
		console.log("播放时长改变");
	})
	this.on("volumechange", function() {
		console.log("音量改变");
	})
	this.on("stalled", function() {
		console.log("网速异常");
	})
});
```

获取当前时长以及总时长

```
console.log("当前播放到：",myPlayer.cache_.currentTime)
console.log("当前总时长：",myPlayer.cache_.duration)

```