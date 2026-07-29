# [#](#wx-onLocalServiceFound-function-listener) wx.onLocalServiceFound(function listener)

> 基础库 2.4.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：支持，需要小程序基础库版本不低于 [2.15.0](../../../framework/compatibility.html)

> 相关文档: [局域网通信](../../../framework/ability/mDNS.html)

## [#](#功能描述) 功能描述

监听 mDNS 服务发现的事件

## [#](#参数) 参数

### [#](#function-listener) function listener

mDNS 服务发现的事件的监听函数

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| serviceType | string | 服务的类型 |
| serviceName | string | 服务的名称 |
| ip | string | 服务的 ip 地址 |
| port | number | 服务的端口 |

Incorrect translation.