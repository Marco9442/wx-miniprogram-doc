# [#](#wx-openChannelsActivity-Object-object) wx.openChannelsActivity(Object object)

> 基础库 2.19.2 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：不支持
>
> **小程序插件**：不支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [视频号视频](../../../framework/open-ability/channels-activity.html)

## [#](#功能描述) 功能描述

打开视频号视频

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| finderUserName | string |  | 是 | 视频号 id，以“sph”开头的id，可在视频号助手获取 |
| feedId | string |  | 是 | 视频 feedId |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

Incorrect translation.