# [#](#MediaAudioPlayer-wx-createMediaAudioPlayer) [MediaAudioPlayer](MediaAudioPlayer.html) wx.createMediaAudioPlayer()

> 基础库 2.13.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：支持

## [#](#功能描述) 功能描述

创建媒体音频播放器对象 [MediaAudioPlayer](MediaAudioPlayer.html) 对象，可用于播放视频解码器 [VideoDecoder](../video-decoder/VideoDecoder.html) 输出的音频。

## [#](#返回值) 返回值

### [#](#MediaAudioPlayer) [MediaAudioPlayer](MediaAudioPlayer.html)

## [#](#注意事项) 注意事项

- iOS 7.0.15 mediaAudioPlayer 播放网络视频资源会出现音频卡顿，本地视频没有这个问题，将下一个客户端版本修复。

## [#](#示例代码) 示例代码

```
  // 创建视频解码器，具体参数见 createVideoDecoder 文档
  const videoDecoder = wx.createVideoDecoder()
  // 创建媒体音频播放器
  const mediaAudioPlayer = wx.createMediaAudioPlayer()
  // 启动视频解码器
  videoDecoder.start()
  // 启动播放器
  mediaAudioPlayer.start().then(() => {
    // 添加播放器音频来源
    mediaAudioPlayer.addAudioSource(videoDecoder).then(res => {
      videoDecoder.getFrameData() // 建议在 requestAnimationFrame 里获取每一帧视频数据
      console.log(res)
    })

    // 移除播放器音频来源
    mediaAudioPlayer.removeAudioSource(videoDecoder).then()
    // 停止播放器
    mediaAudioPlayer.stop().then()
    // 销毁播放器
    mediaAudioPlayer.destroy().then()
    // 设置播放器音量
    mediaAudioPlayer.volume = 0.5
  })
```

## [#](#完整demo（小游戏）) 完整demo（小游戏）

- https://developers.weixin.qq.com/s/SF2duHmb7MjI

Incorrect translation.