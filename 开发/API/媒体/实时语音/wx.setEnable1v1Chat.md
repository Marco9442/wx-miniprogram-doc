# [#](#wx-setEnable1v1Chat-Object-object) wx.setEnable1v1Chat(Object object)

> 基础库 2.20.1 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：支持
>
> **[用户授权](../../../framework/open-ability/authorize.html)**：需要 scope.record,&,camera
>
> **小程序插件**：不支持
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [双人音视频对话](../../../framework/open-ability/1v1voip.html)

## [#](#功能描述) 功能描述

开启双人通话。设置 `enable` 为 `false` 时，无法接听呼叫。

## [#](#参数) 参数

### [#](#Object-object) Object object

|  | 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- | --- |
|  | enable | Boolean |  | 是 | 是否开启 |
|  | backgroundType | Number | 0 | 否 | 窗口背景色(音频通话背景以及小窗模式背景) |
|  | | 合法值 | 说明 | | --- | --- | | 0 | #262930 | | 1 | #FA5151 | | 2 | #FA9D3B | | 3 | #3D7257 | | 4 | #1485EE | | 5 | #6467F0 | | | | | |
|  | minWindowType | Number | 1 | 否 | 小窗样式 |
|  | success | function |  | 否 | 接口调用成功的回调函数 |
|  | fail | function |  | 否 | 接口调用失败的回调函数 |
|  | complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

Incorrect translation.