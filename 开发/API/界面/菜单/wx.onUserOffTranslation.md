# [#](#wx-onUserOffTranslation-function-listener) wx.onUserOffTranslation(function listener)

> 基础库 3.14.2 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：不支持
>
> **微信 Windows 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

监听用户主动取消翻译的事件

## [#](#参数) 参数

### [#](#function-listener) function listener

用户主动取消翻译的事件的监听函数

## [#](#示例代码) 示例代码

```
const callback = () => console.log('userTriggerTranslation')

wx.onUserOffTranslation(callback)
// 取消监听
wx.offUserOffTranslation(callback)
```

Incorrect translation.