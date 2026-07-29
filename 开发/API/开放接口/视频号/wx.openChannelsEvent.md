# [#](#wx-openChannelsEvent-Object-object) wx.openChannelsEvent(Object object)

> 基础库 2.21.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：不支持
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [3.7.11](../../../framework/compatibility.html)
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持

> 相关文档: [视频号活动](../../../framework/open-ability/channels-event.html)

## [#](#功能描述) 功能描述

打开视频号活动页

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| finderUserName | string |  | 是 | 视频号 id，以“sph”开头的id，可在视频号助手获取 |
| eventId | string |  | 是 | 活动 id |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

Incorrect translation.