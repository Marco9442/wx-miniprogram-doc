# [#](#wx-openInquiriesTopic-Object-object) wx.openInquiriesTopic(Object object)

> 基础库 3.14.0 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **以 [Promise 风格](../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：不支持
>
> **小程序插件**：不支持
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

通过小程序打开问一问话题

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| pageId | string |  | 是 | 落地页 id，需在指定页面点击右上角三个点的「复制 ID」按钮获取 |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

#### [#](#object-fail-回调函数) object.fail 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-err) Object err

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| errMsg | string | 错误信息 |

## [#](#示例代码) 示例代码

```
wx.openInquiriesTopic({
  pageId:'', // 填写落地页 id
  success: res => {

  },
  fail: res => {

  }
})
```

Incorrect translation.