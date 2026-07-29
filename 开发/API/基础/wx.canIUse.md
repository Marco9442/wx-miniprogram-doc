# [#](#boolean-wx-canIUse-string-schema) boolean wx.canIUse(string schema)

> 基础库 1.1.1 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **小程序插件**：不支持
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [低版本兼容](../../../analysis/experience/compatibility.html)

## [#](#功能描述) 功能描述

判断小程序的API，回调，参数，组件等是否在当前版本可用。

## [#](#参数) 参数

### [#](#string-schema) string schema

使用 `${API}.${method}.${param}.${option}` 或者 `${component}.${attribute}.${option}` 方式来调用

## [#](#返回值) 返回值

### [#](#boolean) boolean

当前版本是否可用

## [#](#参数说明) 参数说明

- `${API}` 代表 API 名字
- `${method}` 代表调用方式，有效值为return, success, object, callback
- `${param}` 代表参数或者返回值
- `${option}` 代表参数的可选值或者返回值的属性
- `${component}` 代表组件名字
- `${attribute}` 代表组件属性
- `${option}` 代表组件属性的可选值

## [#](#示例代码) 示例代码

```
// 对象的属性或方法
wx.canIUse('console.log')
wx.canIUse('CameraContext.onCameraFrame')
wx.canIUse('CameraFrameListener.start')
wx.canIUse('Image.src')

// wx接口参数、回调或者返回值
wx.canIUse('openBluetoothAdapter')
wx.canIUse('getSystemInfoSync.return.safeArea.left')
wx.canIUse('getSystemInfo.success.screenWidth')
wx.canIUse('showToast.object.image')
wx.canIUse('onCompassChange.callback.direction')
wx.canIUse('request.object.method.GET')

// 组件的属性
wx.canIUse('live-player')
wx.canIUse('text.selectable')
wx.canIUse('button.open-type.contact')
```

Incorrect translation.