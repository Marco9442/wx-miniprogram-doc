# [#](#wx-showShareImageMenu-Object-object) wx.showShareImageMenu(Object object)

> 基础库 2.14.3 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **以 [Promise 风格](../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：支持
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [2.16.0](../../framework/compatibility.html)
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

打开分享图片弹窗，可以将图片发送给朋友、分享至朋友圈、收藏或下载

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- |
| path | string |  | 是 | 要分享的图片地址，必须为本地路径或临时路径 |  |
| needShowEntrance | boolean | true | 否 | 分享的图片消息是否要带小程序入口 | [3.2.0](../../framework/compatibility.html) |
| entrancePath | string | '' | 否 | 发送给朋友时，小程序入口打开小程序的路径，如果当前页面允许分享给朋友，则默认为当前页面路径，否则默认为小程序首页 | [3.2.0](../../framework/compatibility.html) |
| success | function |  | 否 | 接口调用成功的回调函数 |  |
| fail | function |  | 否 | 接口调用失败的回调函数 |  |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |  |

## [#](#示例代码) 示例代码

```
wx.downloadFile({
  url: 'https://res.wx.qq.com/wxdoc/dist/assets/img/demo.ef5c5bef.jpg',
  success: (res) => {
    wx.showShareImageMenu({
      path: res.tempFilePath
    })
  }
})
```

## [#](#Tips) Tips

1. 从基础库 3.8.2 开始，style 参数废弃
2. 从基础库 3.8.2 开始，needShowEntrance 参数默认值从 false 改为 true
3. 从基础库 3.8.2 开始，支持分享至朋友圈，分享至朋友圈的图片不支持带有二维码（可支持小程序码）

Incorrect translation.