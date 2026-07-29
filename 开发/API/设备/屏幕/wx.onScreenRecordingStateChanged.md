# [#](#wx-onScreenRecordingStateChanged-function-listener) wx.onScreenRecordingStateChanged(function listener)

> 基础库 2.24.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：不支持
>
> **微信 iOS 版**：支持
>
> **微信 Android 版**：不支持

## [#](#功能描述) 功能描述

监听用户录屏事件。

## [#](#参数) 参数

### [#](#function-listener) function listener

用户录屏事件的监听函数

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

|  | 属性 | 类型 | 说明 |
| --- | --- | --- | --- |
|  | state | string | 录屏状态 |
|  | | 合法值 | 说明 | | --- | --- | | start | 开始录屏 | | stop | 结束录屏 | | | |

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

Incorrect translation.