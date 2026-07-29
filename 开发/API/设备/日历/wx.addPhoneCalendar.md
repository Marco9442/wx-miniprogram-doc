# [#](#wx-addPhoneCalendar-Object-object) wx.addPhoneCalendar(Object object)

> 基础库 2.15.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：支持
>
> **[用户授权](../../../framework/open-ability/authorize.html)**：需要 scope.addPhoneCalendar
>
> **小程序插件**：不支持
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

向系统日历添加事件

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- |
| title | string |  | 是 | 日历事件标题 |  |
| startTime | number |  | 是 | 开始时间的 unix 时间戳 |  |
| allDay | boolean |  | 否 | 是否全天事件，默认 false |  |
| description | string |  | 否 | 事件说明 |  |
| location | string |  | 否 | 事件位置 |  |
| endTime | string |  | 否 | 结束时间的 unix 时间戳，默认与开始时间相同 |  |
| alarm | boolean |  | 否 | 是否提醒，默认 true |  |
| alarmOffset | number |  | 否 | 提醒提前量，单位秒，默认 0 表示开始时提醒 |  |
| path | string |  | 否 | 跳转小程序路径，必须要和 signature 一起使用，填入后会自动生成跳转链接拼接在事件说明中 | [3.7.6](../../../framework/compatibility.html) |
| signature | string |  | 否 | 跳转小程序路径签名，必须要和 path 一起使用，用 session\_key 对 path 签名得到的结果，即 `hmac_sha256(session_key, path)`。详见 [用户数据的签名验证和加解密](../../../framework/open-ability/signature.html) | [3.7.6](../../../framework/compatibility.html) |
| success | function |  | 否 | 接口调用成功的回调函数 |  |
| fail | function |  | 否 | 接口调用失败的回调函数 |  |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |  |

Incorrect translation.