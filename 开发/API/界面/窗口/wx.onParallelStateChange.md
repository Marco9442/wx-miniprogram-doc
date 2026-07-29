# [#](#wx-onParallelStateChange-function-listener) wx.onParallelStateChange(function listener)

> 基础库 3.12.1 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：不支持
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持

## [#](#功能描述) 功能描述

监听小程序分栏状态变化事件。仅适用于 PC 平台

## [#](#参数) 参数

### [#](#function-listener) function listener

小程序分栏状态变化事件的监听函数

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| isOnParallel | boolean | 当前是否分栏 |
| rightPage | Page | 分栏右侧页面对象（非分栏状态时返回当前页面） |
| leftPage | Page | 分栏左侧页面对象（非分栏状态时返回当前页面） |

Incorrect translation.