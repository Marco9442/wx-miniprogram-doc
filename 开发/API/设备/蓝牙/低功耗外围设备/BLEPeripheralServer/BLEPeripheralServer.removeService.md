# [#](#BLEPeripheralServer-removeService-Object-object) BLEPeripheralServer.removeService(Object object)

> 基础库 2.10.3 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：不支持
>
> **小程序插件**：不支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [蓝牙介绍](../../../framework/device/bluetooth.html)

## [#](#功能描述) 功能描述

移除服务。

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| serviceId | String |  | 是 | service 的 UUID |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

Incorrect translation.