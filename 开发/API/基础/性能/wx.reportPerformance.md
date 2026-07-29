# [#](#wx-reportPerformance-Number-id-Number-value-String-Array-dimensions) wx.reportPerformance(Number id, Number value, String|Array dimensions)

> 基础库 2.9.2 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：支持，需要小程序基础库版本不低于 [2.9.3](../../../framework/compatibility.html)
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [小程序测速](../../../framework/performanceReport/index.html)

## [#](#功能描述) 功能描述

小程序测速上报。使用前，需要在小程序管理后台配置。

## [#](#参数) 参数

### [#](#Number-id) Number id

指标 id

### [#](#Number-value) Number value

需要上报的数值

### [#](#String-Array-dimensions) String|Array dimensions

自定义维度 (选填)

## [#](#示例代码) 示例代码

```
wx.reportPerformance(1101, 680)
wx.reportPerformance(1101, 680, 'custom')
```

Incorrect translation.