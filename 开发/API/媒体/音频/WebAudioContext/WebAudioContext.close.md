# [#](#Promise-WebAudioContext-close) Promise WebAudioContext.close()

> **小程序插件**：不支持

## [#](#功能描述) 功能描述

关闭WebAudioContext

## [#](#返回值) 返回值

### [#](#Promise) Promise

## [#](#注意事项) 注意事项

同步关闭对应的WebAudio上下文。close后会立即释放当前上下文的资源，**不要在close后再次访问state属性。**

```
const audioCtx = wx.createWebAudioContext()
audioCtx.close().then(() => {
  console.log(audioCtx.state) // bad case：不应该在close后再访问state
})
```

Incorrect translation.