# [#](#wx-getChannelsShareKey-Object-object) wx.getChannelsShareKey(Object object)

> 基础库 2.22.1 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：不支持
>
> **小程序插件**：不支持
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

获取视频号直播卡片/视频卡片的分享来源，仅当卡片携带了分享信息、同时用户已授权该小程序获取视频号分享信息且启动场景值为 1177、1184、1195、1208 时可用。

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
|  | sharerOpenId | string | 分享者 openid |
|  | promoter | Object | 推广员 |
|  | |  | 结构属性 | 类型 | 说明 | | --- | --- | --- | --- | |  | finderNickname | string | 推广员昵称 | |  | promoterId | string | 推广员 id | |  | promoterOpenId | string | 推广员 openid | | | |

Incorrect translation.