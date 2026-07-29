# [#](#RealtimeLogManager-wx-getRealtimeLogManager) [RealtimeLogManager](RealtimeLogManager.html) wx.getRealtimeLogManager()

> 基础库 2.7.1 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：支持，需要小程序基础库版本不低于 [2.16.0](../../../framework/compatibility.html)
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [实时日志](../../../framework/realtimelog/index.html)

## [#](#功能描述) 功能描述

获取实时日志管理器对象。

## [#](#返回值) 返回值

### [#](#RealtimeLogManager) [RealtimeLogManager](RealtimeLogManager.html)

## [#](#示例代码) 示例代码

```
// 小程序端
const logger = wx.getRealtimeLogManager()
logger.info({str: 'hello world'}, 'info log', 100, [1, 2, 3])
logger.error({str: 'hello world'}, 'error log', 100, [1, 2, 3])
logger.warn({str: 'hello world'}, 'warn log', 100, [1, 2, 3])

// 插件端，基础库 2.16.0 版本后支持，只允许采用 key-value 的新格式上报
const logManager = wx.getRealtimeLogManager()
const logger = logManager.tag('plugin-log1')
logger.info('key1', 'value1')
logger.error('key2', {str: 'value2'})
logger.warn('key3', 'value3')
```

Incorrect translation.