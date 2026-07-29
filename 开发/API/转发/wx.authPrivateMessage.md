# [#](#wx-authPrivateMessage-Object-object) wx.authPrivateMessage(Object object)

> 基础库 2.13.0 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **以 [Promise 风格](../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：不支持
>
> **小程序插件**：不支持
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [小程序私密消息](../../framework/open-ability/share/private-message.html)

## [#](#功能描述) 功能描述

验证私密消息。用法详情见 [小程序私密消息使用指南](../../framework/open-ability/share/private-message.html)

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| shareTicket | string |  | 是 | shareTicket。可以从 wx.getEnterOptionsSync 中获取。详情 [shareTicket](../../framework/open-ability/share.html) |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| errMsg | string | 错误信息 |
| valid | boolean | 验证是否通过 |
| encryptedData | string | 经过加密的activityId，解密后可得到原始的activityId。若解密后得到的activityId可以与开发者后台的活动id对应上则验证通过，否则表明valid字段不可靠（被篡改） 详细见[加密数据解密算法](../../framework/open-ability/signature.html) |
| iv | string | 加密算法的初始向量，详细见[加密数据解密算法](../../framework/open-ability/signature.html) |

## [#](#示例代码) 示例代码

```
wx.authPrivateMessage({
  shareTicket: 'xxxxxx',
  success(res) {
    console.log('authPrivateMessage success', res)
    // res
    // {
    //   errMsg: 'authPrivateMessage:ok'
    //   valid: true
    //   iv: 'xxxx',
    //   encryptedData: 'xxxxxx'
    // }
  },
  fail(res) {
    console.log('authPrivateMessage fail', res)
  }
})
```

Incorrect translation.