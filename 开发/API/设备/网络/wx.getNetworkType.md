# [#](#wx-getNetworkType-Object-object) wx.getNetworkType(Object object)

> **以 [Promise 风格](../../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：支持
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [1.9.6](../../../framework/compatibility.html)
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [弱网体验优化](../../../framework/performance/weak-network.html)、[网络调优](../../../framework/performance/network.html)

## [#](#功能描述) 功能描述

获取网络类型

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

|  | 属性 | 类型 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- |
|  | networkType | string | 网络类型 |  |
|  | | 合法值 | 说明 | | --- | --- | | wifi | wifi 网络 | | 2g | 2g 网络 | | 3g | 3g 网络 | | 4g | 4g 网络 | | 5g | 5g 网络 | | unknown | Android 下不常见的网络类型 | | none | 无网络 | | | | |
|  | signalStrength | Number | 信号强弱，单位 dbm |  |
|  | hasSystemProxy | Boolean | 设备是否使用了网络代理 | [2.22.1](../../../framework/compatibility.html) |
|  | weakNet | Boolean | 是否处于弱网环境 | [3.5.3](../../../framework/compatibility.html) |

## [#](#示例代码) 示例代码

```
wx.getNetworkType({
  success (res) {
    const networkType = res.networkType
    const weakNet = res.weakNet
  }
})
```

Incorrect translation.