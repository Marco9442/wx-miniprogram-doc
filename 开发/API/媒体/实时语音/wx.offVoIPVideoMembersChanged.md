# [#](#wx-offVoIPVideoMembersChanged-function-listener) wx.offVoIPVideoMembersChanged(function listener)

> 基础库 2.11.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：不支持
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持

## [#](#功能描述) 功能描述

移除实时语音通话成员视频状态变化事件的监听函数

## [#](#参数) 参数

### [#](#function-listener) function listener

onVoIPVideoMembersChanged 传入的监听函数。不传此参数则移除所有监听函数。

## [#](#示例代码) 示例代码

```
const listener = function (res) { console.log(res) }

wx.onVoIPVideoMembersChanged(listener)
wx.offVoIPVideoMembersChanged(listener) // 需传入与监听时同一个的函数对象
```

Incorrect translation.