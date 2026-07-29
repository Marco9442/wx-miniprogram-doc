# [#](#LivePlayerContext-requestFullScreen-Object-object) LivePlayerContext.requestFullScreen(Object object)

> **以 [Promise 风格](../../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：不支持
>
> **小程序插件**：支持

> 相关文档: [live-player 组件](../../../component/live-player.html)

## [#](#功能描述) 功能描述

进入全屏

## [#](#参数) 参数

### [#](#Object-object) Object object

|  | 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- | --- |
|  | direction | number | 0 | 否 | 设置全屏时的方向 |
|  | | 合法值 | 说明 | | --- | --- | | 0 | 正常竖向 | | 90 | 屏幕逆时针90度 | | -90 | 屏幕顺时针90度 | | | | | |
|  | success | function |  | 否 | 接口调用成功的回调函数 |
|  | fail | function |  | 否 | 接口调用失败的回调函数 |
|  | complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

Incorrect translation.