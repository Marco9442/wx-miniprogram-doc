# [#](#DynamicsCompressorNode-WebAudioContext-createDynamicsCompressor) DynamicsCompressorNode WebAudioContext.createDynamicsCompressor()

> **小程序插件**：不支持

## [#](#功能描述) 功能描述

创建一个DynamicsCompressorNode

## [#](#返回值) 返回值

### [#](#DynamicsCompressorNode) DynamicsCompressorNode

## [#](#示例代码) 示例代码

示例代码

```
let audioCtx = wx.createWebAudioContext()
let compressor = audioCtx.createDynamicsCompressor()

compressor.threshold.value = -50
compressor.knee.value = 40
compressor.ratio.value = 12
compressor.attack.value = 0
compressor.release.value = 0.25
```

Incorrect translation.