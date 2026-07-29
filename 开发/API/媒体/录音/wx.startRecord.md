# [#](#wx-startRecord-Object-object) wx.startRecord(Object object)

从基础库 [1.6.0](../../../framework/compatibility.html) 开始，本接口停止维护，请使用 [wx.getRecorderManager](wx.getRecorderManager.html) 代替

> **以 [Promise 风格](../../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：支持
>
> **[用户授权](../../../framework/open-ability/authorize.html)**：需要 scope.record
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [1.9.6](../../../framework/compatibility.html)

## [#](#功能描述) 功能描述

开始录音。当主动调用 [wx.stopRecord](wx.stopRecord.html)，或者录音超过1分钟时自动结束录音。当用户离开小程序时，此接口无法调用。

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

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| tempFilePath | string | 录音文件的临时路径 (本地路径) |

## [#](#示例代码) 示例代码

```
wx.startRecord({
  success (res) {
    const tempFilePath = res.tempFilePath
  }
})
setTimeout(function () {
  wx.stopRecord() // 结束录音
}, 10000)
```

Incorrect translation.