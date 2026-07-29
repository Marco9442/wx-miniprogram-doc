# [#](#wx-offUserTriggerTranslation-function-listener) wx.offUserTriggerTranslation(function listener)

> 基础库 3.7.9 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：不支持
>
> **微信 Windows 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

移除用户触发小程序菜单中翻译功能的事件的监听函数

## [#](#参数) 参数

### [#](#function-listener) function listener

onUserTriggerTranslation 传入的监听函数。不传此参数则移除所有监听函数。

## [#](#示例代码) 示例代码

```
const listener = function (res) { console.log(res) }

wx.onUserTriggerTranslation(listener)
wx.offUserTriggerTranslation(listener) // 需传入与监听时同一个的函数对象
```

Incorrect translation.