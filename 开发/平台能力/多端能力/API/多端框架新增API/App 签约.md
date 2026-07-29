# [#](#wx-miniapp-OpenBusinessWebview) wx.miniapp.OpenBusinessWebview

该接口用于实现 App 签约功能，详情可查看[APP 纯签约](https://pay.weixin.qq.com/doc/v2/merchant/4011986804#%E6%AD%A5%E9%AA%A42%EF%BC%9A%E7%AD%BE%E7%BA%A6%E6%8E%A5%E5%8F%A3)。

#### [#](#SDK-版本要求) SDK 版本要求

- Android SDk >= 1.6.13
- iOS SDK >= 1.6.15

### [#](#接入前注意事项) 接入前注意事项

在接入 App 调起用户确认收款前需详细阅读下方说明：

- 该能力依赖「微信 Open SDK」，因此需按照文档前往微信开放平台申请移动应用账号，并且需将移动应用账号与多端应用账号进行绑定，[详情可查看](../../handbook/web/application_create#_3%E3%80%81%E7%BB%91%E5%AE%9A%E7%A7%BB%E5%8A%A8%E5%BA%94%E7%94%A8%E8%B4%A6%E5%8F%B7)
- 以及，由于该能力依赖「微信 Open SDK」，因此在 project.miniapp.json 中需勾选 Open SDK；
- 外部 App 拉起微信客户端发起签约前，需先后台调用[预签约接口](https://pay.weixin.qq.com/doc/v2/merchant/4011986804)完成预签约，获取 pre\_entrustweb\_id，再拉起微信客户端，完成签约，返回 App。

### [#](#参数) 参数

#### [#](#请求参数) 请求参数

- 参数对齐[微信支付 - APP 纯签约 - OpenBusinessWebview](https://pay.weixin.qq.com/doc/v2/merchant/4011986804#%E6%AD%A5%E9%AA%A42%EF%BC%9A%E7%AD%BE%E7%BA%A6%E6%8E%A5%E5%8F%A3)参数，方便理解

| 属性 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| preEntrustwebId | string | 是 | 预签约 id；示例值：5778aadY9nltAsZzXixCkFIGYnV2V |

#### [#](#示例) 示例

```
wx.miniapp.openBusinessWebview({
  preEntrustwebId: '5778aadxxxx',
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

返回参数内容无需关注，如果签约成功，商户系统会收到[「签约结果通知」](https://pay.weixin.qq.com/doc/v2/merchant/4011987586)

Incorrect translation.