# [#](#wx-openChannelsUserProfile-Object-object) wx.openChannelsUserProfile(Object object)

> 基础库 2.21.2 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：不支持
>
> **需要页面权限**：当前是插件页面时，宿主小程序不能调用该接口，反之亦然
>
> **小程序插件**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [视频号主页](../../../framework/open-ability/channels-profile.html)

## [#](#功能描述) 功能描述

打开视频号主页。若为插件环境，只允许在插件页面中调用。

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| finderUserName | string |  | 是 | 视频号id（参考格式为：sphcqO59YEPCvoe；查看路径为：微信客户端->我tab->视频号->右上角.-＞视频号名字-视频号ID） |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

Incorrect translation.