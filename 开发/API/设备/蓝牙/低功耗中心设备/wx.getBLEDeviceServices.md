# [#](#wx-getBLEDeviceServices-Object-object) wx.getBLEDeviceServices(Object object)

> 基础库 1.1.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：支持
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [1.9.6](../../../framework/compatibility.html)
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [蓝牙低功耗 (BLE)](../../../framework/device/ble.html)

## [#](#功能描述) 功能描述

获取蓝牙低功耗设备所有服务 (service)。

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| deviceId | string |  | 是 | 蓝牙设备 id。需要已经通过 [wx.createBLEConnection](wx.createBLEConnection.html) 建立连接 |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

|  | 属性 | 类型 | 说明 |
| --- | --- | --- | --- |
|  | services | Array.<Object> | 设备服务列表 |
|  | |  | 结构属性 | 类型 | 说明 | | --- | --- | --- | --- | |  | uuid | string | 蓝牙设备服务的 UUID | |  | isPrimary | boolean | 该服务是否为主服务 | | | |

## [#](#错误) 错误

| 错误码 | 错误信息 | 说明 |
| --- | --- | --- |
| 0 | ok | 正常 |
| -1 | already connect | 已连接 |
| 10000 | not init | 未初始化蓝牙适配器 |
| 10001 | not available | 当前蓝牙适配器不可用 |
| 10002 | no device | 没有找到指定设备 |
| 10003 | connection fail | 连接失败 |
| 10004 | no service | 没有找到指定服务 |
| 10005 | no characteristic | 没有找到指定特征 |
| 10006 | no connection | 当前连接已断开 |
| 10007 | property not support | 当前特征不支持此操作 |
| 10008 | system error | 其余所有系统上报的异常 |
| 10009 | system not support | Android 系统特有，系统版本低于 4.3 不支持 BLE |
| 10012 | operate time out | 连接超时 |
| 10013 | invalid\_data | 连接 deviceId 为空或者是格式不正确 |

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/pQU51zmz7a3K "在开发者工具中预览效果")

```
wx.getBLEDeviceServices({
  // 这里的 deviceId 需要已经通过 wx.createBLEConnection 与对应设备建立连接
  deviceId,
  success (res) {
    console.log('device services:', res.services)
  }
})
```

Incorrect translation.