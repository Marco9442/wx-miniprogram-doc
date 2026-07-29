# [#](#wx-offAudioInterruptionBegin-function-listener) wx.offAudioInterruptionBegin(function listener)

> 基础库 2.6.2 开始支持，低版本需做[兼容处理](../../../../framework/compatibility.html)。

> **小程序插件**：支持，需要小程序基础库版本不低于 [2.15.0](../../../../framework/compatibility.html)
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持

## [#](#功能描述) 功能描述

移除音频因为受到系统占用而被中断开始事件的监听函数

## [#](#参数) 参数

### [#](#function-listener) function listener

onAudioInterruptionBegin 传入的监听函数。不传此参数则移除所有监听函数。

## [#](#示例代码) 示例代码

```
const listener = function (res) { console.log(res) }

wx.onAudioInterruptionBegin(listener)
wx.offAudioInterruptionBegin(listener) // 需传入与监听时同一个的函数对象
```

Incorrect translation.