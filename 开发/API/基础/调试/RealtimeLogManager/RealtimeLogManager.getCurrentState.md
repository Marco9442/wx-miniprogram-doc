# [#](#Object-RealtimeLogManager-getCurrentState) Object RealtimeLogManager.getCurrentState()

> 基础库 2.19.4 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：不支持

## [#](#功能描述) 功能描述

实时日志会将一定时间间隔内缓存的日志聚合上报，如果该时间内缓存的内容超出限制，则会被丢弃。此方法可以获取当前缓存剩余空间。

> 注意：基础库内部在对日志进行上报时会补充一些结构化数据，如果遇到上报溢出的情况也会补充警告日志，所以此方法获取到的当前占用信息会比预期的大一些。

## [#](#返回值) 返回值

### [#](#Object) Object

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| size | number | 当前缓存中已使用空间，以字节为单位 |
| maxSize | number | 当前缓存最大可用空间，以字节为单位 |
| logCount | number | 当前缓存中的日志条数 |
| maxLogCount | number | 当前缓存中最大可存日志条数 |

Incorrect translation.