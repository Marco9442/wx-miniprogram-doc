# [#](#InnerAudioContext) InnerAudioContext

InnerAudioContext 实例，可通过 [wx.createInnerAudioContext](wx.createInnerAudioContext.html) 接口获取实例。注意，音频播放过程中，可能被系统中断，可通过 [wx.onAudioInterruptionBegin](../../base/app/app-event/wx.onAudioInterruptionBegin.html)、[wx.onAudioInterruptionEnd](../../base/app/app-event/wx.onAudioInterruptionEnd.html)事件来处理这种情况。

## [#](#属性) 属性

### [#](#string-src) string src

音频资源的地址，用于直接播放。[2.2.3](../../../framework/compatibility.html) 开始支持云文件ID

### [#](#number-startTime) number startTime

开始播放的位置（单位：s），默认为 0

### [#](#boolean-autoplay) boolean autoplay

是否自动开始播放，默认为 `false`

### [#](#boolean-loop) boolean loop

是否循环播放，默认为 `false`

### [#](#boolean-obeyMuteSwitch) boolean obeyMuteSwitch

是否遵循系统静音开关，默认为 `true`。当此参数为 `false` 时，即使用户打开了静音开关，也能继续发出声音。从 2.3.0 版本开始此参数不生效，使用 [wx.setInnerAudioOption](wx.setInnerAudioOption.html) 接口统一设置。

### [#](#number-volume) number volume

> 基础库 1.9.90 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

音量。范围 0~1。默认为 1

### [#](#number-playbackRate) number playbackRate

> 基础库 2.11.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

播放速度。范围 0.5-2.0，默认为 1。（Android 需要 6 及以上版本）

### [#](#number-duration) number duration

当前音频的长度（单位 s）。只有在当前有合法的 src 时返回（只读）

### [#](#number-currentTime) number currentTime

当前音频的播放位置（单位 s）。只有在当前有合法的 src 时返回，时间保留小数点后 6 位（currentTime 属性在基础库 2.26.2 之前只读，基础库 2.26.2 开始可读可写，改变 currentTime 值等同于调用 seek）

### [#](#boolean-paused) boolean paused

当前是是否暂停或停止状态（只读）

### [#](#number-buffered) number buffered

音频缓冲的时间点，仅保证当前播放时间点到此时间点内容已缓冲（只读）

### [#](#string-referrerPolicy) string referrerPolicy

> 基础库 2.13.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

`origin`: 发送完整的referrer; `no-referrer`: 不发送。格式固定为 `https://servicewechat.com/{appid}/{version}/page-frame.html`，其中 {appid} 为小程序的 appid，{version} 为小程序的版本号，版本号为 0 表示为开发版、体验版以及审核版本，版本号为 devtools 表示为开发者工具，其余为正式版本；

## [#](#方法) 方法

### [#](#InnerAudioContext-play) [InnerAudioContext.play()](InnerAudioContext.play.html)

播放

### [#](#InnerAudioContext-pause) [InnerAudioContext.pause()](InnerAudioContext.pause.html)

暂停。暂停后的音频再播放会从暂停处开始播放

### [#](#InnerAudioContext-stop) [InnerAudioContext.stop()](InnerAudioContext.stop.html)

停止。停止后的音频再播放会从头开始播放。

### [#](#InnerAudioContext-seek-number-position) [InnerAudioContext.seek(number position)](InnerAudioContext.seek.html)

跳转到指定位置

### [#](#InnerAudioContext-destroy) [InnerAudioContext.destroy()](InnerAudioContext.destroy.html)

销毁当前实例

### [#](#InnerAudioContext-onCanplay-function-listener) [InnerAudioContext.onCanplay(function listener)](./InnerAudioContext.onCanplay.html)

监听音频进入可以播放状态的事件。但不保证后面可以流畅播放

### [#](#InnerAudioContext-offCanplay-function-listener) [InnerAudioContext.offCanplay(function listener)](./InnerAudioContext.offCanplay.html)

移除音频进入可以播放状态的事件的监听函数

### [#](#InnerAudioContext-onPlay-function-listener) [InnerAudioContext.onPlay(function listener)](./InnerAudioContext.onPlay.html)

监听音频播放事件

### [#](#InnerAudioContext-offPlay-function-listener) [InnerAudioContext.offPlay(function listener)](./InnerAudioContext.offPlay.html)

移除音频播放事件的监听函数

### [#](#InnerAudioContext-onPause-function-listener) [InnerAudioContext.onPause(function listener)](./InnerAudioContext.onPause.html)

监听音频暂停事件

### [#](#InnerAudioContext-offPause-function-listener) [InnerAudioContext.offPause(function listener)](./InnerAudioContext.offPause.html)

移除音频暂停事件的监听函数

### [#](#InnerAudioContext-onStop-function-listener) [InnerAudioContext.onStop(function listener)](./InnerAudioContext.onStop.html)

监听音频停止事件

### [#](#InnerAudioContext-offStop-function-listener) [InnerAudioContext.offStop(function listener)](./InnerAudioContext.offStop.html)

移除音频停止事件的监听函数

### [#](#InnerAudioContext-onEnded-function-listener) [InnerAudioContext.onEnded(function listener)](./InnerAudioContext.onEnded.html)

监听音频自然播放至结束的事件

### [#](#InnerAudioContext-offEnded-function-listener) [InnerAudioContext.offEnded(function listener)](./InnerAudioContext.offEnded.html)

移除音频自然播放至结束的事件的监听函数

### [#](#InnerAudioContext-onTimeUpdate-function-listener) [InnerAudioContext.onTimeUpdate(function listener)](./InnerAudioContext.onTimeUpdate.html)

监听音频播放进度更新事件

### [#](#InnerAudioContext-offTimeUpdate-function-listener) [InnerAudioContext.offTimeUpdate(function listener)](./InnerAudioContext.offTimeUpdate.html)

移除音频播放进度更新事件的监听函数

### [#](#InnerAudioContext-onError-function-listener) [InnerAudioContext.onError(function listener)](./InnerAudioContext.onError.html)

监听音频播放错误事件

### [#](#InnerAudioContext-offError-function-listener) [InnerAudioContext.offError(function listener)](./InnerAudioContext.offError.html)

移除音频播放错误事件的监听函数

### [#](#InnerAudioContext-onWaiting-function-listener) [InnerAudioContext.onWaiting(function listener)](./InnerAudioContext.onWaiting.html)

监听音频加载中事件。当音频因为数据不足，需要停下来加载时会触发

### [#](#InnerAudioContext-offWaiting-function-listener) [InnerAudioContext.offWaiting(function listener)](./InnerAudioContext.offWaiting.html)

移除音频加载中事件的监听函数

### [#](#InnerAudioContext-onSeeking-function-listener) [InnerAudioContext.onSeeking(function listener)](./InnerAudioContext.onSeeking.html)

监听音频进行跳转操作的事件

### [#](#InnerAudioContext-offSeeking-function-listener) [InnerAudioContext.offSeeking(function listener)](./InnerAudioContext.offSeeking.html)

移除音频进行跳转操作的事件的监听函数

### [#](#InnerAudioContext-onSeeked-function-listener) [InnerAudioContext.onSeeked(function listener)](./InnerAudioContext.onSeeked.html)

监听音频完成跳转操作的事件

### [#](#InnerAudioContext-offSeeked-function-listener) [InnerAudioContext.offSeeked(function listener)](./InnerAudioContext.offSeeked.html)

移除音频完成跳转操作的事件的监听函数

## [#](#支持格式) 支持格式

| 格式 | iOS | Android |
| --- | --- | --- |
| flac | x | √ |
| m4a | √ | √ |
| ogg | x | √ |
| ape | x | √ |
| amr | x | √ |
| wma | x | √ |
| wav | √ | √ |
| mp3 | √ | √ |
| mp4 | x | √ |
| aac | √ | √ |
| aiff | √ | x |
| caf | √ | x |

## [#](#示例代码) 示例代码

```
const innerAudioContext = wx.createInnerAudioContext()
innerAudioContext.autoplay = true
innerAudioContext.src = 'https://wx_test.mp3'
innerAudioContext.onPlay(() => {
  console.log('开始播放')
})
innerAudioContext.onError((res) => {
  console.log(res.errMsg)
  console.log(res.errCode)
})
```

Incorrect translation.