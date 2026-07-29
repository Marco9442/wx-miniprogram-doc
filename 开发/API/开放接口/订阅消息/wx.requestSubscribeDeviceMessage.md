# [#](#wx-requestSubscribeDeviceMessage-Object-object) wx.requestSubscribeDeviceMessage(Object object)

> 基础库 2.20.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：支持
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [3.4.1](../../../framework/compatibility.html)
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [设备消息](../../../framework/device/device-message.html)

## [#](#功能描述) 功能描述

订阅设备消息接口，调用后弹出授权框，用户同意后会允许开发者给用户发送订阅模版消息。当用户点击“允许”按钮时，模板消息会被添加到用户的小程序设置页，通过 wx.getSetting 接口可获取用户对相关模板消息的订阅状态。

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| tmplIds | Array |  | 是 | 需要订阅的消息模板的 id 的集合，一次调用最多可订阅3条消息 |
| sn | String |  | 是 | 设备唯一序列号。由厂商分配，长度不能超过128字节。字符只接受数字，大小写字母，下划线（\_）和连字符（-）。 |
| snTicket | String |  | 是 | 设备票据，5分钟内有效。 |
| modelId | String |  | 是 | 设备型号 id 。通过微信公众平台注册设备获得。 |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| errMsg | String | 接口调用成功时errMsg值为'requestSubscribeDeviceMessage:ok' |
| [TEMPLATE\_ID: string] | String | [TEMPLATE\_ID]是动态的键，即模板id，值包括'accept'、'reject'、'ban'、'filter'、'acceptWithAudio'。'accept'表示用户同意订阅该条id对应的模板消息，'reject'表示用户拒绝订阅该条id对应的模板消息，'ban'表示已被后台封禁，'acceptWithAudio' 表示用户接收订阅消息并开启了语音提醒，'filter'表示该模板因为模板标题同名被后台过滤。例如 { errMsg: "requestSubscribeDeviceMessage:ok", zun-LzcQyW-edafCVvzPkK4de2Rllr1fFpw2A\_x0oXE: "accept"} 表示用户同意订阅zun-LzcQyW-edafCVvzPkK4de2Rllr1fFpw2A\_x0oXE这条消息 |

#### [#](#object-fail-回调函数) object.fail 回调函数

##### [#](#参数-3) 参数

###### [#](#Object-res-2) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| errMsg | String | 接口调用失败错误信息 |
| errCode | Number | 接口调用失败错误码，有可能为空 |

## [#](#错误码) 错误码

| errCode | errMsg | 说明 |
| --- | --- | --- |
| 10001 | TmplIds can't be empty | tmplIds 为空 |
| 10004 | Invalid template id | tmplId 参数类型错误 |
| 20001 | No template data return, verify the template id exist | tmplId 为空 |
| 20003 | Templates count out of max bounds | tmplId 数量超过上限 |
| 19720726 | check sn\_ticket fail | snTicket 不合法 |
| 19720727 | sn\_ticket expire | snTicket 过期 |
| 19720728 | err\_not\_found\_tid | tmplId 不存在 |
| 19720736 | template\_id do not match model\_id | modelId 类型与 tmplId 类型不符 |

## [#](#示例代码) 示例代码

```
wx.requestSubscribeDeviceMessage({
  tmplIds: ['xxxxx'],
  sn: 'xxxx',
  snTicket: 'xxxxx',
  modelId: 'xxx',
  success(res) {
    console.log(res)
  },
  fail(res) {
    console.log(res)
  }
})
```

Incorrect translation.