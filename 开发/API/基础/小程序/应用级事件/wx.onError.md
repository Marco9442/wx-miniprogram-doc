# [#](#wx-onError-function-listener) wx.onError(function listener)

> 基础库 2.1.2 开始支持，低版本需做[兼容处理](../../../../framework/compatibility.html)。

> **小程序插件**：不支持
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

监听小程序错误事件。如脚本错误或 API 调用报错等。该事件与 [`App.onError`](../../../../reference/api/App.html#onerrorstring-error) 的回调时机与参数一致。

## [#](#参数) 参数

### [#](#function-listener) function listener

小程序错误事件的监听函数

#### [#](#参数-2) 参数

##### [#](#object-error) object error

错误

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| message | string | 错误信息，包含堆栈 |

Incorrect translation.