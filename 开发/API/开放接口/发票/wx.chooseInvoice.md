# [#](#wx-chooseInvoice-Object-object) wx.chooseInvoice(Object object)

> 基础库 2.3.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：支持
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [2.16.1](../../../framework/compatibility.html)

## [#](#功能描述) 功能描述

选择用户已有的发票。

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

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| invoiceInfo | String | 用户选中的发票信息，格式为一个 JSON 字符串，包含三个字段： card\_id：所选发票卡券的 cardId，encrypt\_code：所选发票卡券的加密 code，报销方可以通过 cardId 和 encryptCode 获得报销发票的信息，app\_id： 发票方的 appId。 |

## [#](#通过-cardId-和-encryptCode-获得报销发票的信息) 通过 cardId 和 encryptCode 获得报销发票的信息

请参考[微信电子发票文档](https://mp.weixin.qq.com/wiki?t=resource/res_main&id=21517918939oae3U)中，「查询报销发票信息」部分。
其中 `access_token` 的获取请参考[auth.getAccessToken]((auth.getAccessToken))文档

Incorrect translation.