# [#](#WebAudioContext-wx-createWebAudioContext) [WebAudioContext](WebAudioContext.html) wx.createWebAudioContext()

> 基础库 2.19.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：不支持
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持

## [#](#功能描述) 功能描述

创建 WebAudio 上下文。

## [#](#返回值) 返回值

### [#](#WebAudioContext) [WebAudioContext](WebAudioContext.html)

## [#](#示例代码) 示例代码

一个简单的播放demo

```
const audioCtx = wx.createWebAudioContext()

const loadAudio = (url) => {
  return new Promise((resolve) => {
    wx.request({
      url,
      responseType: 'arraybuffer',
      success: res => {
        console.log('res.data', res.data)
        audioCtx.decodeAudioData(res.data, buffer => {
          resolve(buffer)
        }, err => {
          console.error('decodeAudioData fail', err)
          reject()
        })
      },
      fail: res => {
        console.error('request fail', res)
        reject()
      }
    })
  })
}

const play = () => {
  loadAudio('xxx-test.mp3').then(buffer => {
    let source = audioCtx.createBufferSource()
    source.buffer = buffer
    source.connect(audioCtx.destination)
    source.start()
  }).catch(() => {
    console.log('fail')
  })
}

play()
```

Incorrect translation.