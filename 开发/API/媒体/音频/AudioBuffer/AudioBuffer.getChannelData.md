# [#](#Float32Array-AudioBuffer-getChannelData-number-channel) Float32Array AudioBuffer.getChannelData(number channel)

> **小程序插件**：不支持
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持

## [#](#功能描述) 功能描述

返回一个 Float32Array，包含了带有频道的PCM数据，由频道参数定义（有0代表第一个频道）

## [#](#参数) 参数

### [#](#number-channel) number channel

要获取特定通道数据的索引

## [#](#返回值) 返回值

### [#](#Float32Array) Float32Array

## [#](#示例代码) 示例代码

示例代码

```
const audioCtx = wx.createWebAudioContext()
const myArrayBuffer = audioCtx.createBuffer(2, frameCount, audioCtx.sampleRate);
const nowBuffering = myArrayBuffer.getChannelData(channel);
```

Incorrect translation.