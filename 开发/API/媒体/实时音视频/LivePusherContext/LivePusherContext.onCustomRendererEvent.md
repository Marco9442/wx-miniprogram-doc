# [#](#LivePusherContext-onCustomRendererEvent-string-event-function-function-callback) LivePusherContext.onCustomRendererEvent(string event, function|function callback)

> 基础库 2.29.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：支持

> 相关文档: [live-pusher 组件](../../../component/live-pusher.html)

## [#](#功能描述) 功能描述

开启自定义渲染时，开发者通过此方法订阅相关事件，客户端 8.0.31 版本开始支持。

## [#](#参数) 参数

### [#](#string-event) string event

事件类型，后订阅的监听器会取消之前的监听器

**event 的合法值**

| 值 | 说明 | 最低版本 |
| --- | --- | --- |
| frame | 采集到视频帧后触发 |  |
| update | 推流尺寸变更时触发 |  |

### [#](#function-function-callback) function|function callback

自定义渲染事件处理回调函数

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| width | number | 推流宽度 |
| height | number | 推流高度 |

Incorrect translation.