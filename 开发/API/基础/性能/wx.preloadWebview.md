# [#](#wx-preloadWebview-Object-object) wx.preloadWebview(Object object)

> 基础库 2.15.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：不支持
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [2.15.0](../../../framework/compatibility.html)

## [#](#功能描述) 功能描述

预加载下个页面的 WebView。参见[预加载下个页面的时机](../../../framework/performance/tips/runtime_nav.html#_2-4-%E6%8E%A7%E5%88%B6%E9%A2%84%E5%8A%A0%E8%BD%BD%E4%B8%8B%E4%B8%AA%E9%A1%B5%E9%9D%A2%E7%9A%84%E6%97%B6%E6%9C%BA)

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

Incorrect translation.