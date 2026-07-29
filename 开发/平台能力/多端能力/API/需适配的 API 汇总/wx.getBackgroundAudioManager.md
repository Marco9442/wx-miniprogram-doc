# [#](#wx-getBackgroundAudioManager) wx.getBackgroundAudioManager

> iOS SDK ≥ 1.1.2，Android 暂不支持

- 功能：获取全局唯一的背景音频管理器。
- 联系：本接口能力是在小程序提供的同名 API 上拓展的，兼容小程序同名 API 的属性和方法，[点击查询详情](https://developers.weixin.qq.com/miniprogram/dev/api/media/background-audio/wx.getBackgroundAudioManager.html)。
- 特性：支持 App 在播放音频时同步显示在系统控制中心的播放面板；支持音频在手机息屏后继续播放。

## [#](#注意事项) 注意事项

微信开发者工具：调用该接口能力之前，需在 `project.miniapp.json` 中开启「Media SDK」和「应用配置（info.plist相关）」，如下图所示。

![](https://res.wx.qq.com/op_res/rF-YTfjfuXtqxaQLnShX4L32si2DEtdAMmYSTKWvjCwwh9mqaIi9uZPAneuPfMVnpukBMbdK1AHWHlTOzz4A8g) ![](https://res.wx.qq.com/op_res/_MXoKtC4UW9-Hlc8ktLac-uB2BbFH9Phx7RrE2rIQbhuzJgTvaxGBW8aN9Gu_NKX4vpP664PCgsQFDHPUoQreg)

## [#](#返回值) 返回值

返回 [BackgroundAudioManager](https://developers.weixin.qq.com/miniprogram/dev/api/media/background-audio/BackgroundAudioManager.html) 实例，可通过 wx.getBackgroundAudioManager() 获取。

以下仅展示调用该接口新能力**必填**的属性和方法，其余属性和方法可参考[小程序文档](https://developers.weixin.qq.com/miniprogram/dev/api/media/background-audio/BackgroundAudioManager.html)。

### [#](#属性) 属性

- string src

  音频的数据源（[2.2.3](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility) 开始支持云文件ID）。默认为空字符串，当设置了新的 src 时，会自动开始播放，目前支持的格式有 m4a, aac, mp3, wav。
- string title

  音频标题，用于原生音频播放器音频标题（必填）。原生音频播放器中的分享功能，分享出去的卡片标题，也将使用该值。

### [#](#方法) 方法

- BackgroundAudioManager.onNext(function listener)

  监听用户在系统音乐播放面板点击下一曲事件（仅iOS）
- BackgroundAudioManager.onPrev(function listener)

  监听用户在系统音乐播放面板点击上一曲事件（仅iOS）

## [#](#示例代码) 示例代码

```
onLoad() {
  const backgroundAudioManager = wx.getBackgroundAudioManager()
  backgroundAudioManager.onPause(() => {
      console.log('暂停')
  })
  backgroundAudioManager.onPlay(() => {
      console.log('播放')
  })
  backgroundAudioManager.onNext(() => {
      console.log('用户在控制中心点击了下一首')
  })
  backgroundAudioManager.onPrev(() => {
      console.log('用户在控制中心点击了上一首')
  })
},

play() {
  const backgroundAudioManager = wx.getBackgroundAudioManager()
    backgroundAudioManager.title = '此时此刻'
    backgroundAudioManager.singer = '许巍'
    // 设置了 src 之后会自动播放
    backgroundAudioManager.src = 'https://xxx/xxx.mp3' 
}
```

Incorrect translation.