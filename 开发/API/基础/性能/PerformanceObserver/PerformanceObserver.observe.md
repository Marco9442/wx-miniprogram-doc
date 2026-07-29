# [#](#PerformanceObserver-observe-Object-options) PerformanceObserver.observe(Object options)

> 基础库 2.11.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：不支持

## [#](#功能描述) 功能描述

开始监听

## [#](#参数) 参数

### [#](#Object-options) Object options

设置 type 监听单个类型的指标，设置 entryTypes 监听多个类型指标。

|  | 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- | --- |
|  | type | string |  | 否 | 指标类型。不能和 entryTypes 同时使用 |
|  | | 合法值 | 说明 | | --- | --- | | navigation | 路由 | | render | 渲染 | | script | 脚本 | | loadPackage | 代码包下载 | | | | | |
|  | entryTypes | Array.<string> |  | 否 | 指标类型列表。不能和 type 同时使用。 |

Incorrect translation.