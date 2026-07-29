# [#](#ScriptProcessorNode-WebAudioContext-createScriptProcessor-number-bufferSize-number-numberOfInputChannels-number-numberOfOutputChannels) ScriptProcessorNode WebAudioContext.createScriptProcessor(number bufferSize, number numberOfInputChannels, number numberOfOutputChannels)

> **小程序插件**：不支持

## [#](#功能描述) 功能描述

创建一个ScriptProcessorNode

## [#](#参数) 参数

### [#](#number-bufferSize) number bufferSize

缓冲区大小，以样本帧为单位

### [#](#number-numberOfInputChannels) number numberOfInputChannels

用于指定输入node的声道的数量

### [#](#number-numberOfOutputChannels) number numberOfOutputChannels

用于指定输出node的声道的数量

## [#](#返回值) 返回值

### [#](#ScriptProcessorNode) ScriptProcessorNode

## [#](#示例代码) 示例代码

示例代码

```
let audioCtx = wx.createWebAudioContext()
const sampleSize = 4096
audioCtx.createScriptProcessor(sampleSize, 1, 1)
```

Incorrect translation.