# [#](#PerformanceEntry) PerformanceEntry

> 相关文档: [性能优化](../../../framework/performance/tips/start.html)

单条性能数据。具体数据口径请参考[性能数据文档](../../../framework/performance/perf_data.html)

## [#](#属性) 属性

### [#](#string-entryType) string entryType

指标类型

**entryType 的合法值**

| 值 | 说明 | 最低版本 |
| --- | --- | --- |
| navigation | 路由 |  |
| render | 渲染 |  |
| script | 脚本 |  |

### [#](#string-name) string name

指标名称

**name 的合法值**

| 值 | 说明 | 最低版本 |
| --- | --- | --- |
| appLaunch | 小程序启动耗时。(entryType: navigation) |  |
| route | 路由处理耗时。(entryType: navigation) |  |
| firstRender | 页面首次渲染耗时。(entryType: render) |  |
| firstPaint | 页面首次绘制(FP)时间点，无 duration。（iOS 不支持）(entryType: render) | [2.21.2](../../../framework/compatibility.html) |
| firstContentfulPaint | 页面首次内容绘制(FCP)时间点，无 duration。（iOS 14.5 以下版本不支持）(entryType: render) | [2.21.2](../../../framework/compatibility.html) |
| largestContentfulPaint | 页面最大内容绘制(LCP)时间点，无 duration。（iOS 不支持）(entryType: render) | [2.23.1](../../../framework/compatibility.html) |
| evaluateScript | 逻辑层 JS 代码注入耗时。(entryType: script) |  |
| downloadPackage | 代码包下载耗时。(entryType: loadPackage) | [2.24.0](../../../framework/compatibility.html) |
| resourceTiming | 视图层资源加载耗时。(entryType: resource) | [2.24.0](../../../framework/compatibility.html) |

### [#](#number-startTime) number startTime

开始时间，不同指标的具体含义会有差异。

### [#](#number-duration) number duration

耗时 ms。仅对于表示阶段的指标有效。

### [#](#string-path) string path

页面路径。仅 render 和 navigation 类型指标有效。

### [#](#number-referrerPath) number referrerPath

> 基础库 2.23.1 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

页面跳转来源页面路径。仅 route 指标有效。

### [#](#number-pageId) number pageId

> 基础库 2.23.1 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

path 对应页面实例 Id（随机生成，不保证递增）。仅 render/navigation 指标有效。

### [#](#number-referrerPageId) number referrerPageId

> 基础库 2.23.1 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

referrerPath对应页面实例 Id（随机生成，不保证递增）。仅 route 指标有效。

### [#](#number-navigationStart) number navigationStart

路由真正响应开始时间。仅 navigation 类型指标有效。

### [#](#string-navigationType) string navigationType

路由详细类型，与小程序路由方法对应。仅 navigation 类型指标有效。

### [#](#string-moduleName) string moduleName

分包名，主包表示为 **APP** (2.21.2 开始)。仅 evaluateScript 指标有效。

### [#](#Array-string-fileList) Array.<string> fileList

> 基础库 2.21.2 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

注入文件列表。仅 evaluateScript 指标有效。

### [#](#number-viewLayerReadyTime) number viewLayerReadyTime

> 基础库 2.21.2 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

渲染层代码注入完成时间。仅 firstRender 指标有效。

### [#](#number-initDataSendTime) number initDataSendTime

> 基础库 2.21.2 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

首次渲染参数从逻辑层发出的时间。仅 firstRender 指标有效。

### [#](#number-initDataRecvTime) number initDataRecvTime

> 基础库 2.21.2 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

首次渲染参数在渲染层收到的时间。仅 firstRender 指标有效。

### [#](#number-viewLayerRenderStartTime) number viewLayerRenderStartTime

> 基础库 2.21.2 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

渲染层执行渲染开始时间。仅 firstRender 指标有效。

### [#](#number-viewLayerRenderEndTime) number viewLayerRenderEndTime

> 基础库 2.21.2 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

渲染层执行渲染结束时间。仅 firstRender 指标有效。

### [#](#string-packageName) string packageName

> 基础库 2.24.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

代码包名称。仅 downloadPackage 指标有效。

### [#](#number-packageSize) number packageSize

> 基础库 2.24.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

代码包大小。仅 downloadPackage 指标有效。

### [#](#string-uri) string uri

> 基础库 2.24.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

资源路径。仅 resourceTiming 指标有效。

### [#](#string-initiatorType) string initiatorType

> 基础库 2.24.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

初始化性能条目的资源类型。仅 resourceTiming 指标有效。

**initiatorType 的合法值**

| 值 | 说明 | 最低版本 |
| --- | --- | --- |
| audio | 音频 |  |
| cover-image | cover-image 组件的图片 |  |
| image | 组件的图片 |  |
| open-data | 组件的图片 |  |

### [#](#number-transferSize) number transferSize

> 基础库 2.24.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

表示获取资源的大小（以八位字节为单位）的数字。仅 resourceTiming 指标有效。(iOS 不支持）

### [#](#number-domainLookupStart) number domainLookupStart

> 基础库 2.24.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

解析域名开始时间。仅 resourceTiming 指标有效。

### [#](#number-domainLookupEnd) number domainLookupEnd

> 基础库 2.24.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

解析域名结束时间。仅 resourceTiming 指标有效。

Incorrect translation.