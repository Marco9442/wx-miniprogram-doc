# [#](#Promise-wx-getRendererUserAgent-Object-object) Promise wx.getRendererUserAgent(Object object)

> 基础库 2.26.3 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：不支持
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [3.11.2](../../../framework/compatibility.html)
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

获取 Webview 小程序的 UserAgent

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#string-userAgent) string userAgent

UserAgent

## [#](#返回值) 返回值

### [#](#Promise-string) Promise.<string>

## [#](#示例代码) 示例代码

```
// v2.30.4 前，仅支持 promise 风格调用
wx.getRendererUserAgent().then(userAgent => console.log(userAgent))
// v2.30.4 起，除 promise 风格调用外，也支持 invoke 风格使用
wx.getRendererUserAgent({
  success(res) { console.log(res.userAgent) }
})
```

Incorrect translation.