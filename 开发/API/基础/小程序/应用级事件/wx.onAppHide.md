# [#](#wx-onAppHide-function-listener) wx.onAppHide(function listener)

> 基础库 2.1.2 开始支持，低版本需做[兼容处理](../../../../framework/compatibility.html)。

> **小程序插件**：不支持
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

监听小程序切后台事件。该事件与 [`App.onHide`](../../../../reference/api/App.html#onhide) 的回调参数一致。

## [#](#参数) 参数

### [#](#function-listener) function listener

小程序切后台事件的监听函数

#### [#](#参数-2) 参数

##### [#](#Object-options) Object options

切后台参数

|  | 属性 | 类型 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- |
|  | reason | number | 原因 | [3.5.7](../../../../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | 0 | 用户退出小程序 | | 1 | 进入其他小程序 | | 2 | 打开原生功能页 | | 3 | 其他 | | | | |

Incorrect translation.