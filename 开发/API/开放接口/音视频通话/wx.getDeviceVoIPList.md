# [#](#wx-getDeviceVoIPList-Object-object) wx.getDeviceVoIPList(Object object)

> 基础库 2.30.3 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：不支持
>
> **小程序插件**：不支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [小程序音视频通话（for 硬件）](../../../framework/device/device-voip.html)

## [#](#功能描述) 功能描述

查询当前用户授权的音视频通话设备（组）信息

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

|  | 属性 | 类型 | 说明 |
| --- | --- | --- | --- |
|  | list | Array.<Object> |  |
|  | |  | 结构属性 | 类型 | 说明 | 最低版本 | | --- | --- | --- | --- | --- | |  | sn | string | 设备唯一序列号。（仅单台设备时） |  | |  | model\_id | string | 设备型号 id。通过微信公众平台注册设备获得。（仅单台设备时） |  | |  | group\_id | string | 设备组的唯一标识 id（仅设备组时） | [2.30.4](../../../framework/compatibility.html) | |  | status | number | 设备（组）授权状态。0：未授权；1：已授权 |  | | | |

## [#](#示例代码) 示例代码

```
wx.getDeviceVoIPList({
  success(res) {
    console.log(res)
  },
  fail(res) {
    console.log(res)
  }
})
```

Incorrect translation.