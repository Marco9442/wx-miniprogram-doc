# [#](#wx-getShareInfo-Object-object) wx.getShareInfo(Object object)

从基础库 [2.17.3](../../framework/compatibility.html) 开始，本接口停止维护，请使用 [wx.getGroupEnterInfo](../open-api/group/wx.getGroupEnterInfo.html) 代替

> 基础库 1.1.0 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **以 [Promise 风格](../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：不支持
>
> **需要页面权限**：当前是插件页面时，宿主小程序不能调用该接口，反之亦然
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [2.1.0](../../framework/compatibility.html)
>
> 在小程序插件中使用时，只能在当前插件的页面中调用
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

获取转发详细信息（主要是获取群ID）。 从群聊内的小程序消息卡片打开小程序时，调用此接口才有效。从基础库 v2.17.3 开始，推荐用 [wx.getGroupEnterInfo](../open-api/group/wx.getGroupEnterInfo.html) 替代此接口。

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- |
| shareTicket | string |  | 是 | shareTicket，详见[获取更多转发信息](../../framework/open-ability/share.html#获取更多转发信息) |  |
| timeout | number |  | 否 | 超时时间，单位 ms | [1.9.90](../../framework/compatibility.html) |
| success | function |  | 否 | 接口调用成功的回调函数 |  |
| fail | function |  | 否 | 接口调用失败的回调函数 |  |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |  |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

| 属性 | 类型 | 说明 | 最低版本 |
| --- | --- | --- | --- |
| errMsg | string | 错误信息 |  |
| encryptedData | string | 包括敏感数据在内的完整转发信息的加密数据，详细见[加密数据解密算法](../../framework/open-ability/signature.html) |  |
| iv | string | 加密算法的初始向量，详细见[加密数据解密算法](../../framework/open-ability/signature.html) |  |
| cloudID | string | 敏感数据对应的云 ID，开通[云开发](../../wxcloudservice/wxcloud/basis/getting-started.html)的小程序才会返回，可通过云调用直接获取开放数据，详细见[云调用直接获取开放数据](../../framework/open-ability/signature.html#method-cloud) | [2.7.0](../../framework/compatibility.html) |

## [#](#示例代码) 示例代码

敏感数据获取方式 [加密数据解密算法](../../framework/open-ability/signature.html#加密数据解密算法) 。
获取得到的开放数据为以下 json 结构（其中 openGId 为当前群的唯一标识）：

```
{
 "openGId": "OPENGID"
}
```

## [#](#Tips) Tips

- 如需要展示群名称，小程序可以使用 [开放数据组件](../../component/open-data.html)
- 小游戏可以通过 [`wx.getGroupInfo`](errorwx.getGroupInfo)) 接口获取群名称

Incorrect translation.