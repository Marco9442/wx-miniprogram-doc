# [#](#wx-onUnhandledRejection-function-listener) wx.onUnhandledRejection(function listener)

> 基础库 2.10.0 开始支持，低版本需做[兼容处理](../../../../framework/compatibility.html)。

> **小程序插件**：不支持
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

监听未处理的 Promise 拒绝事件。该事件与 [`App.onUnhandledRejection`](../../../../reference/api/App.html#onUnhandledRejection-Object-object) 的回调时机与参数一致。

## [#](#参数) 参数

### [#](#function-listener) function listener

未处理的 Promise 拒绝事件的监听函数

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| reason | string | 拒绝原因，一般是一个 Error 对象 |
| promise | Promise.<any> | 被拒绝的 Promise 对象 |

## [#](#注意) 注意

- 所有的 unhandledRejection 都可以被这一监听捕获，但只有 Error 类型的才会在小程序后台触发报警。

Incorrect translation.