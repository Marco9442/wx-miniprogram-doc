# [#](#wx-startLocalServiceDiscovery-Object-object) wx.startLocalServiceDiscovery(Object object)

> 基础库 2.4.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：支持
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [2.15.0](../../../framework/compatibility.html)
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [局域网通信](../../../framework/ability/mDNS.html)

## [#](#功能描述) 功能描述

开始搜索局域网下的 mDNS 服务。搜索的结果会通过 wx.onLocalService\* 事件返回。

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| serviceType | string |  | 是 | 要搜索的服务类型 |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

#### [#](#object-fail-回调函数) object.fail 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

|  | 属性 | 类型 | 说明 |
| --- | --- | --- | --- |
|  | errMsg | string | 错误信息 |
|  | | 合法值 | 说明 | | --- | --- | | invalid param | serviceType 为空 | | scan task already exist | 在当前 startLocalServiceDiscovery 发起的搜索未停止的情况下，再次调用 startLocalServiceDiscovery | | | |

## [#](#示例代码) 示例代码

```
    wx.startLocalServiceDiscovery({
      // 当前手机所连的局域网下有一个 _http._tcp. 类型的服务
      serviceType: '_http._tcp.',
      success: console.log,
      fail: console.log
    })
```

## [#](#注意) 注意

1. 由于操作系统相关能力变更，iOS 微信客户端 7.0.18 及以上版本无法使用 mDNS 相关接口，安卓版本不受影响
2. wx.startLocalServiceDiscovery 是一个消耗性能的行为，开始 30 秒后会自动 stop 并执行 wx.onLocalServiceDiscoveryStop 注册的回调函数。
3. 在调用 wx.startLocalServiceDiscovery 后，在这次搜索行为停止后才能发起下次 wx.startLocalServiceDiscovery。停止本次搜索行为的操作包括调用 wx.stopLocalServiceDiscovery 和 30 秒后系统自动 stop 本次搜索。

Incorrect translation.