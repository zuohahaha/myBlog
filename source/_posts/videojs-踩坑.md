---
title: '''videojs-踩坑'''
date: 2020-06-17 15:40:18
tags:
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
