# [#](#wx-bindEmployeeRelation-Object-object) wx.bindEmployeeRelation(Object object)

> 基础库 3.10.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：不支持
>
> **小程序插件**：不支持

## [#](#功能描述) 功能描述

拉起小程序[用工关系](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/laboruse/intro.html)功能绑定弹窗，用户允许后可同步拉起用户关系消息订阅列表

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| tmplIds | Array.<string> |  | 是 | 订阅消息模板id列表，一次最多传入6条；如果传入则会在绑定成功后自动拉起订阅消息列表页面。此处要求传入的的模板消息为未订阅状态。 |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

|  | 属性 | 类型 | 说明 |
| --- | --- | --- | --- |
|  | bindingStatus | string | 绑定状态 |
|  | | 合法值 | 说明 | | --- | --- | | accept | 已绑定 | | reject | 已拒绝 | | | |
|  | TEMPLATE\_ID | String | [TEMPLATE\_ID]是动态的键，即模板消息id，值包括'accept'、'reject'。'accept'表示用户同意订阅该条id对应的模板消息，'reject'表示用户拒绝订阅该条id对应的模板消息。例如 { zun-LzcQyW-edafCVvzPkK4de2Rllr1fFpw2A\_x0oXE: "accept"} 表示用户同意订阅zun-LzcQyW-edafCVvzPkK4de2Rllr1fFpw2A\_x0oXE这条消息 |

## [#](#示例代码) 示例代码

```
wx.bindEmployeeRelation({
  success(res) {
    console.log(res.bindingStatus)
  },
})
```

Incorrect translation.