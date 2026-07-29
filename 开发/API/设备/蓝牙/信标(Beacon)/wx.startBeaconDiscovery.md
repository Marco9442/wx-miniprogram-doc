# [#](#wx-startBeaconDiscovery-Object-object) wx.startBeaconDiscovery(Object object)

> 基础库 1.2.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：支持
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [1.9.6](../../../framework/compatibility.html)
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [蓝牙信标 (Beacon)](../../../framework/device/beacon.html)

## [#](#功能描述) 功能描述

开始搜索附近的 Beacon 设备

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| uuids | Array.<string> |  | 是 | Beacon 设备广播的 UUID 列表 |
| ignoreBluetoothAvailable | boolean | false | 否 | 是否校验蓝牙开关，仅在 iOS 下有效。iOS 11 起，控制面板里关掉蓝牙，还是能继续使用 Beacon 服务。 |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

## [#](#错误) 错误

| 错误码 | 错误信息 | 说明 |
| --- | --- | --- |
| 0 | ok | 正常 |
| 11000 | unsupport | 系统或设备不支持 |
| 11001 | bluetooth service unavailable | 蓝牙服务不可用 |
| 11002 | location service unavailable | 位置服务不可用 |
| 11003 | already start | 已经开始搜索 |
| 11004 | not startBeaconDiscovery | 还未开始搜索 |
| 11005 | system error | 系统错误 |
| 11006 | invalid data | 参数不正确 |

## [#](#示例代码) 示例代码

```
wx.startBeaconDiscovery({
  success(res) { }
})
```

Incorrect translation.