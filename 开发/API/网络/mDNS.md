# [#](#wx-stopLocalServiceDiscovery-Object-object) wx.stopLocalServiceDiscovery(Object object)

> 基础库 2.4.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：支持
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [2.15.0](../../../framework/compatibility.html)
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [局域网通信](../../../framework/ability/mDNS.html)

## [#](#功能描述) 功能描述

停止搜索 mDNS 服务

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

#### [#](#object-fail-回调函数) object.fail 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

|  | 属性 | 类型 | 说明 |
| --- | --- | --- | --- |
|  | errMsg | string | 错误信息 |
|  | | 合法值 | 说明 | | --- | --- | | task not found | 在当前没有处在搜索服务中的情况下调用 stopLocalServiceDiscovery | | | |

Incorrect translation.