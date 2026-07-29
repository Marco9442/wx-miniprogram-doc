# [#](#wx-openOfficialAccountProfile-Object-object) wx.openOfficialAccountProfile(Object object)

> 基础库 3.7.10 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **以 [Promise 风格](../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：不支持
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [3.11.2](../../framework/compatibility.html)
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

通过小程序打开公众号主页

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| username | string |  | 是 | 需要打开的公众号的原始 ID |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

## [#](#示例代码) 示例代码

```
  wx.openOfficialAccountProfile({
         username: '', // 此处填写公众号的原始 ID
         success: res => {
         },
         fail: res => {
         }
     })
```

## [#](#Tips) Tips

1. 跳转的公众号需与小程序为同主体或关联主体

Incorrect translation.