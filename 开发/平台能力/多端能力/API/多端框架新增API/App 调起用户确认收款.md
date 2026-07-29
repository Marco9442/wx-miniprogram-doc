# [#](#wx-miniapp-openBusinessView) wx.miniapp.openBusinessView

该接口用于实现 App 调起用户确认收款

#### [#](#SDK-版本要求) SDK 版本要求

- Android SDk >= 1.6.12
- iOS SDK >= 1.6.12

### [#](#接入前注意事项) 接入前注意事项

在接入 App 调起用户确认收款前需详细阅读下方说明：

- 该能力依赖「微信 Open SDK」，因此需按照文档前往微信开放平台申请移动应用账号，并且需将移动应用账号与多端应用账号进行绑定，[详情可查看](../../handbook/web/application_create#_3%E3%80%81%E7%BB%91%E5%AE%9A%E7%A7%BB%E5%8A%A8%E5%BA%94%E7%94%A8%E8%B4%A6%E5%8F%B7)
- 以及，由于该能力依赖「微信 Open SDK」，因此在 project.miniapp.json 中需勾选 Open SDK；
- 补充：该能力需要使用微信支付商户号，需配置 Api key 配置商户号证书等内容，详情可查看[Android 调起用户确认收款](https://pay.weixin.qq.com/doc/v3/merchant/4012719576)、[iOS 调起用户确认收款](https://pay.weixin.qq.com/doc/v3/merchant/4012719578)

### [#](#参数) 参数

#### [#](#请求参数) 请求参数

- 参数对齐[微信支付 - App 调起用户确认收款](https://pay.weixin.qq.com/doc/v3/merchant/4012719576)参数，方便理解

| 属性 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| businessType | string | 是 | 固定值：requestMerchantTransfer |
| query | string | 是 | 查询参数 |

- 说明：使用 URL 的 query string 方式传递参数，格式为 key=value&key2=value2，其中 value、value2需要进行 UrlEncode 处理；例如 `"mchId=1230000000&appId=wx8888888888888888&package=affffddafdfafddffda%3D%3D"`

#### [#](#query-中的字段说明) query 中的字段说明

| 属性 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mchId | string | 是 | 【商户号】商户号，由微信支付生成并下发 |
| appId | string | 是 | 【商户 AppID】微信开放平台审核通过的移动应用 appid，不是多端应用 id（是当前多端应用 id 所绑定的移动应用的 appid），也不是小程序 appid |
| package | string | 是 | 【package 信息】对应[发起转账](https://pay.weixin.qq.com/doc/v3/merchant/4012716434#%E5%BA%94%E7%AD%94%E5%8F%82%E6%95%B0)接口应答参数中的 package\_info（仅当转账单据状态为 WAIT\_USER\_CONFIRM: 待收款用户确认时才返回），用于唤起用户确认收款页面。 |

#### [#](#示例) 示例

```
wx.miniapp.openBusinessView({
    businessType: 'requestMerchantTransfer',
    query: 'mchId=1230000000&appId=wx8888888888888888&package=affffddafdfafddffda%3D%3D',  
    success(res) {
      wx.showToast({
        title: '成功',
      })
    },
    fail() {
      wx.showToast({
        title: '失败',
      })
    }
  })
```

#### [#](#返回参数) 返回参数

- 参数对齐[微信支付 - App 调起用户确认收款](https://pay.weixin.qq.com/doc/v3/merchant/4012719576)参数，方便理解

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| businessType | string | 【业务类型】打开的业务类型。`requestMerchantTransfer` |
| extMsg | string | 【扩展信息】返回的业务数据，格式为 JSON 字符串，如 {"result":"success"} |
| errMsg | string | 返回的错误信息，如果是成功，则返回 "sendOpenReq:ok" |

- 补充：返回的示例如下：

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202505261241385.png)

Incorrect translation.