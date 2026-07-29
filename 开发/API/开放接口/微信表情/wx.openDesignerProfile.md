# [#](#wx-openDesignerProfile-Object-object) wx.openDesignerProfile(Object object)

> 基础库 3.17.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：不支持
>
> **小程序插件**：不支持

## [#](#功能描述) 功能描述

跳转到表情艺术家主页

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| url | string |  | 是 | 表情艺术家主页链接，可前往[表情开放平台](https://sticker.weixin.qq.com/cgi-bin/mmemoticon-bin/loginpage?t=login/index) 获取。 |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

## [#](#示例代码) 示例代码

```
wx.openDesignerProfile({
  url: '',
  success(res) {}
})
```

Incorrect translation.