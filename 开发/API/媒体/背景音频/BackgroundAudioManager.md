# [#](#BackgroundAudioManager) BackgroundAudioManager

BackgroundAudioManager 实例，可通过 [wx.getBackgroundAudioManager](wx.getBackgroundAudioManager.html) 获取。

## [#](#属性) 属性

### [#](#string-src) string src

音频的数据源（[2.2.3](../../../framework/compatibility.html) 开始支持云文件ID）。默认为空字符串，**当设置了新的 src 时，会自动开始播放**，目前支持的格式有 m4a, aac, mp3, wav。

### [#](#number-startTime) number startTime

音频开始播放的位置（单位：s）。

### [#](#string-title) string title

音频标题，用于原生音频播放器音频标题（必填）。原生音频播放器中的分享功能，分享出去的卡片标题，也将使用该值。

### [#](#string-epname) string epname

专辑名，原生音频播放器中的分享功能，分享出去的卡片简介，也将使用该值。

### [#](#string-singer) string singer

歌手名，原生音频播放器中的分享功能，分享出去的卡片简介，也将使用该值。

### [#](#string-coverImgUrl) string coverImgUrl

封面图 URL，用于做原生音频播放器背景图。原生音频播放器中的分享功能，分享出去的卡片配图及背景也将使用该图。

### [#](#string-webUrl) string webUrl

页面链接，原生音频播放器中的分享功能，分享出去的卡片简介，也将使用该值。

### [#](#string-protocol) string protocol

> 基础库 1.9.94 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

音频协议。默认值为 'http'，设置 'hls' 可以支持播放 HLS 协议的直播音频。

### [#](#number-playbackRate) number playbackRate

> 基础库 2.11.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

播放速度。范围 0.5-2.0，默认为 1。（Android 需要 6 及以上版本）

### [#](#number-duration) number duration

当前音频的长度（单位：s），只有在有合法 src 时返回。（只读）

### [#](#number-currentTime) number currentTime

当前音频的播放位置（单位：s），只有在有合法 src 时返回。（只读）

### [#](#boolean-paused) boolean paused

当前是否暂停或停止。（只读）

### [#](#number-buffered) number buffered

音频已缓冲的时间，仅保证当前播放时间点到此时间点内容已缓冲。（只读）

### [#](#string-referrerPolicy) string referrerPolicy

> 基础库 2.13.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

`origin`: 发送完整的referrer; `no-referrer`: 不发送。格式固定为 `https://servicewechat.com/{appid}/{version}/page-frame.html`，其中 {appid} 为小程序的 appid，{version} 为小程序的版本号，版本号为 0 表示为开发版、体验版以及审核版本，版本号为 devtools 表示为开发者工具，其余为正式版本；

### [#](#string-referrerPath) string referrerPath

> 基础库 3.4.8 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

关联页面路径。设置后，当点击播放器上的小程序跳转链接时，将跳转到这个关联页面路径（实验特性，目前仅Android端支持）

### [#](#string-audioType) string audioType

> 基础库 3.4.8 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

音频类型。可设置 "audio" 和 "music" 两种值，默认为 "audio"。不同音频类型对应的播放器样式不一样（实验特性，目前仅iOS和Android端支持）

## [#](#方法) 方法

### [#](#BackgroundAudioManager-play) [BackgroundAudioManager.play()](BackgroundAudioManager.play.html)

播放音乐

### [#](#BackgroundAudioManager-pause) [BackgroundAudioManager.pause()](BackgroundAudioManager.pause.html)

暂停音乐

### [#](#BackgroundAudioManager-seek-number-currentTime) [BackgroundAudioManager.seek(number currentTime)](BackgroundAudioManager.seek.html)

跳转到指定位置

### [#](#BackgroundAudioManager-stop) [BackgroundAudioManager.stop()](BackgroundAudioManager.stop.html)

停止音乐

### [#](#BackgroundAudioManager-onCanplay-function-listener) [BackgroundAudioManager.onCanplay(function listener)](./BackgroundAudioManager.onCanplay.html)

监听背景音频进入可播放状态事件。 但不保证后面可以流畅播放

### [#](#BackgroundAudioManager-onWaiting-function-listener) [BackgroundAudioManager.onWaiting(function listener)](./BackgroundAudioManager.onWaiting.html)

监听音频加载中事件。当音频因为数据不足，需要停下来加载时会触发

### [#](#BackgroundAudioManager-onError-function-listener) [BackgroundAudioManager.onError(function listener)](./BackgroundAudioManager.onError.html)

监听背景音频播放错误事件

### [#](#BackgroundAudioManager-onPlay-function-listener) [BackgroundAudioManager.onPlay(function listener)](./BackgroundAudioManager.onPlay.html)

监听背景音频播放事件

### [#](#BackgroundAudioManager-onPause-function-listener) [BackgroundAudioManager.onPause(function listener)](./BackgroundAudioManager.onPause.html)

监听背景音频暂停事件

### [#](#BackgroundAudioManager-onSeeking-function-listener) [BackgroundAudioManager.onSeeking(function listener)](./BackgroundAudioManager.onSeeking.html)

监听背景音频开始跳转操作事件

### [#](#BackgroundAudioManager-onSeeked-function-listener) [BackgroundAudioManager.onSeeked(function listener)](./BackgroundAudioManager.onSeeked.html)

监听背景音频完成跳转操作事件

### [#](#BackgroundAudioManager-onEnded-function-listener) [BackgroundAudioManager.onEnded(function listener)](./BackgroundAudioManager.onEnded.html)

监听背景音频自然播放结束事件

### [#](#BackgroundAudioManager-onStop-function-listener) [BackgroundAudioManager.onStop(function listener)](./BackgroundAudioManager.onStop.html)

监听背景音频停止事件

### [#](#BackgroundAudioManager-onTimeUpdate-function-listener) [BackgroundAudioManager.onTimeUpdate(function listener)](./BackgroundAudioManager.onTimeUpdate.html)

监听背景音频播放进度更新事件，只有小程序在前台时会回调。

### [#](#BackgroundAudioManager-onNext-function-listener) [BackgroundAudioManager.onNext(function listener)](./BackgroundAudioManager.onNext.html)

监听用户在系统音乐播放面板点击下一曲事件

### [#](#BackgroundAudioManager-onPrev-function-listener) [BackgroundAudioManager.onPrev(function listener)](./BackgroundAudioManager.onPrev.html)

监听用户在系统音乐播放面板点击上一曲事件

## [#](#示例代码) 示例代码

```
const backgroundAudioManager = wx.getBackgroundAudioManager()

backgroundAudioManager.title = '此时此刻'
backgroundAudioManager.epname = '此时此刻'
backgroundAudioManager.singer = '许巍'
backgroundAudioManager.coverImgUrl = 'http://y.gtimg.cn/music/photo_new/T002R300x300M000003rsKF44GyaSk.jpg?max_age=2592000'
// 设置了 src 之后会自动播放
backgroundAudioManager.src = 'https://wx_test.mp3'
```

Incorrect translation.