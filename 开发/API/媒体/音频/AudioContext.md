# [#](#AudioContext) AudioContext

[AudioContext](AudioContext.html) 实例，可通过 [wx.createAudioContext](wx.createAudioContext.html) 获取。

[AudioContext](AudioContext.html) 通过 `id` 跟一个 [audio](../../../component/audio.html) 组件绑定，操作对应的 [audio](../../../component/audio.html) 组件。

## [#](#方法) 方法

### [#](#AudioContext-setSrc-string-src) [AudioContext.setSrc(string src)](AudioContext.setSrc.html)

设置音频地址

### [#](#AudioContext-play) [AudioContext.play()](AudioContext.play.html)

播放音频。

### [#](#AudioContext-pause) [AudioContext.pause()](AudioContext.pause.html)

暂停音频。

### [#](#AudioContext-seek-number-position) [AudioContext.seek(number position)](AudioContext.seek.html)

跳转到指定位置。

## [#](#示例代码) 示例代码

```
<!-- audio.wxml -->
<audio  src="{{src}}" id="myAudio" ></audio>

<button type="primary" bindtap="audioPlay">播放</button>
<button type="primary" bindtap="audioPause">暂停</button>
<button type="primary" bindtap="audio14">设置当前播放时间为14秒</button>
<button type="primary" bindtap="audioStart">回到开头</button>
```

```
// audio.js
Page({
  onReady (e) {
    // 使用 wx.createAudioContext 获取 audio 上下文 context
    this.audioCtx = wx.createAudioContext('myAudio')
    this.audioCtx.setSrc('http://ws.stream.qqmusic.qq.com/M500001VfvsJ21xFqb.mp3?guid=ffffffff82def4af4b12b3cd9337d5e7&uin=346897220&vkey=6292F51E1E384E06DCBDC9AB7C49FD713D632D313AC4858BACB8DDD29067D3C601481D36E62053BF8DFEAF74C0A5CCFADD6471160CAF3E6A&fromtag=46')
    this.audioCtx.play()
  },
  data: {
    src: ''
  },
  audioPlay () {
    this.audioCtx.play()
  },
  audioPause () {
    this.audioCtx.pause()
  },
  audio14 () {
    this.audioCtx.seek(14)
  },
  audioStart () {
    this.audioCtx.seek(0)
  }
})
```

Incorrect translation.