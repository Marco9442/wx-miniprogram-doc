# [#](#Performance-wx-getPerformance) [Performance](Performance.html) wx.getPerformance()

> 基础库 2.11.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：支持
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

获取当前小程序性能相关的信息。关于小程序启动性能优化的更多内容，请参考[启动性能指南](../../../framework/performance/tips/start.html)。

## [#](#返回值) 返回值

### [#](#Performance) [Performance](Performance.html)

目前支持获取以下几类性能指标，具体内容请参考 [PerformanceEntry](PerformanceEntry.html)：

| 指标类型（entryType） | 指标名称 | 最低版本 ｜ |
| --- | --- | --- |
| 路由（navigation） | route: 路由性能 |  |
| 路由（navigation） | appLaunch: 小程序启动耗时 |  |
| 渲染（render） | firstRender: 页面首次渲染耗时 |  |
| 渲染（render） | firstPaint: 页面首次绘制 | <2.21.2> |
| 渲染（render） | firstContentfulPaint: 页面首次内容绘制 | <2.21.2> |
| 渲染（render） | largestContentfulPaint: 页面最大内容绘制 | <2.23.1> |
| 脚本（script） | evaluateScript: 注入脚本耗时 |  |
| 包加载（loadPackage） | downloadPackage: 代码包下载耗时 | <2.24.0> |
| 资源（resource） | resourceTiming: 视图层资源加载耗时 | <2.24.0> |

## [#](#示例代码) 示例代码

```
const performance = wx.getPerformance()
const observer = performance.createObserver((entryList) => {
  console.log(entryList.getEntries())
})
observer.observe({ entryTypes: ['render', 'script', 'navigation'] })
```

## [#](#注意) 注意

- 目前，当开启代码 [按需注入](../../../framework/ability/lazyload.html) 时，`evaluateScript` 将仅包含公有部分代码（2.21.2 开始会区分公共部分/页面和组件的部分），页面和组件的代码注入的时间会包含在 `firstRender` 中（因为页面和组件的代码注入过程成为了首次渲染过程的一部分）。因此开启按需注入后，脚本耗时降低，渲染时间提高属于正常现象，优化效果可以关注整体启动耗时（`appLaunch`）来评估。
- firstPaint 和 firstContentfulPaint 指标在开启 vConsole 的情况下，由于绘制 vConsole 面板，会导致数据提前。

Incorrect translation.