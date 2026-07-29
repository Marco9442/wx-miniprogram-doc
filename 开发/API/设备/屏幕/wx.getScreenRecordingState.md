# [#](#wx-getScreenRecordingState-Object-object) wx.getScreenRecordingState(Object object)

> 基础库 2.24.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：不支持
>
> **小程序插件**：不支持
>
> **微信 iOS 版**：支持
>
> **微信 Android 版**：不支持

## [#](#功能描述) 功能描述

查询用户是否在录屏。

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
|  | state | string | 录屏状态 |
|  | | 合法值 | 说明 | | --- | --- | | on | 开启 | | off | 关闭 | | | |

## [#](#示例代码) 示例代码

```
wx.getScreenRecordingState({
  success: function (res) {
    console.log(res.state)
  },
})
```

Incorrect translation.