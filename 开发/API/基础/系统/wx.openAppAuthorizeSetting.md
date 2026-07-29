# [#](#wx-openAppAuthorizeSetting-Object-object) wx.openAppAuthorizeSetting(Object object)

> 基础库 2.20.1 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：支持
>
> **需要页面权限**：当前是插件页面时，宿主小程序不能调用该接口，反之亦然
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [2.21.3](../../../framework/compatibility.html)
>
> **微信 鸿蒙 OS 版**：支持
>
> **限制**：仅在点击行为时调用

## [#](#功能描述) 功能描述

跳转系统微信授权管理页

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

## [#](#示例代码) 示例代码

```
wx.openAppAuthorizeSetting({
  success (res) {
    console.log(res)
  }
})
```

Incorrect translation.