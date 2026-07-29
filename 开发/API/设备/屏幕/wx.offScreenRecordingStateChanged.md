# [#](#wx-offScreenRecordingStateChanged-function-listener) wx.offScreenRecordingStateChanged(function listener)

> 基础库 2.24.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：不支持
>
> **微信 iOS 版**：支持
>
> **微信 Android 版**：不支持

## [#](#功能描述) 功能描述

移除用户录屏事件的监听函数

## [#](#参数) 参数

### [#](#function-listener) function listener

onScreenRecordingStateChanged 传入的监听函数。不传此参数则移除所有监听函数。

## [#](#示例代码) 示例代码

```
// 监听用户录屏事件
const handler = function (res) {
  console.log(res.state)
}
wx.onScreenRecordingStateChanged(handler)

// 取消监听用户录屏事件
wx.offScreenRecordingStateChanged(handler)
```

## [#](#示例代码-2) 示例代码

```
const listener = function (res) { console.log(res) }

wx.onScreenRecordingStateChanged(listener)
wx.offScreenRecordingStateChanged(listener) // 需传入与监听时同一个的函数对象
```

Incorrect translation.