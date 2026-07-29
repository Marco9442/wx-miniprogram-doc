# [#](#wx-reportAnalytics-string-eventName-Object-data) wx.reportAnalytics(string eventName, Object data)

从基础库 [2.31.1](../../framework/compatibility.html) 开始，本接口停止维护，请使用 [wx.reportEvent](wx.reportEvent.html) 代替

> **小程序插件**：支持，需要小程序基础库版本不低于 [1.9.6](../../framework/compatibility.html)
>
> 在小程序插件中使用时，可以被正常调用，但目前不会进行统计展示
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

自定义分析数据上报接口。使用前，需要在小程序管理后台自定义分析中新建事件，配置好事件名与字段。

## [#](#参数) 参数

### [#](#string-eventName) string eventName

事件名

### [#](#Object-data) Object data

上报的自定义数据，key 为配置中的字段名，value 为上报的数据。

## [#](#示例代码) 示例代码

```
wx.reportAnalytics('purchase', {
  price: 120,
  color: 'red'
})
```

Incorrect translation.