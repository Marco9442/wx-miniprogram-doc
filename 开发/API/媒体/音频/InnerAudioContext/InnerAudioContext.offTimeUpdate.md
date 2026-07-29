# [#](#InnerAudioContext-offTimeUpdate-function-listener) InnerAudioContext.offTimeUpdate(function listener)

> 基础库 1.9.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：支持

## [#](#功能描述) 功能描述

移除音频播放进度更新事件的监听函数

## [#](#参数) 参数

### [#](#function-listener) function listener

onTimeUpdate 传入的监听函数。不传此参数则移除所有监听函数。

## [#](#示例代码) 示例代码

```
const listener = function (res) { console.log(res) }

InnerAudioContext.onTimeUpdate(listener)
InnerAudioContext.offTimeUpdate(listener) // 需传入与监听时同一个的函数对象
```

Incorrect translation.