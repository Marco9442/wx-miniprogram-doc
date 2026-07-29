# [#](#wx-miniapp-GooglePlayBilling) wx.miniapp.GooglePlayBilling

> Android >= 1.5.8

该接口用于 App 上架到 Google Play 之后可以接入 Google 应用市场虚拟支付，实现在 App 中进行虚拟物品的购买。

## [#](#使用说明) 使用说明

### [#](#_1、在开发者工具中配置-SDK-信息) 1、在开发者工具中配置 SDK 信息

- 将开发者工具升级到最新版的 [nightly](https://developers.weixin.qq.com/miniprogram/dev/devtools/log)
- project.miniapp.json 切到 json 模式，修改 sdkVersion，useExtendedSdk 配置，如下

```
"sdkVersion": "1.5.8",
"useExtendedSdk": {
      "googleplay": true,
      "skyline": true
    }
```

### [#](#_2、阅读并理解-Google-Play-官方文档，完成前置设置) 2、阅读并理解 Google Play 官方文档，完成前置设置

- 详情可查看[将 Google Play 结算库集成到您的应用中](https://developer.android.google.cn/google/play/billing/integrate?hl=zh-cn)
- 涉及的 JSAPI 如下：
  - wx.miniapp.GooglePlayBilling.startConnection
  - wx.miniapp.GooglePlayBilling.queryProductDetails
  - wx.miniapp.GooglePlayBilling.launchBillingFlow
  - wx.miniapp.GooglePlayBilling.consumeAsync
  - wx.miniapp.GooglePlayBilling.acknowledgePurchase
  - wx.miniapp.GooglePlayBilling.onPurchasesUpdatedMethod

### [#](#_3、使用示例) 3、使用示例

```
onLoad() {
      this.startConnection();
      
      const onMethod = (res) => {
      console.log('onPurchasesUpdatedMethod', res)
      if (res.responseCode == 0) {
        const purchases = res.purchases
        for (let i = 0; i < purchases.length; i++) {
          const purchase = purchases[i]
          console.log('purchase', purchase)
          const purchaseToken = purchase.token || purchase.purchaseToken
          this.consumeAsync(purchaseToken) // 拿到 token 之后再验证
        }
      } else {
        console.error('err', res.responseCode, res.debugMessage)
        // 根据错误码自行处理 https://developer.android.com/google/play/billing/errors?hl=zh-cn
      }
    }
    wx.miniapp.GooglePlayBilling.onPurchasesUpdatedMethod(onMethod)
  },
  startConnection() {
    wx.miniapp.GooglePlayBilling.startConnection({
    success: (res) => {
        console.log("Connection started successfully", res);
        this.queryProductDetails();  
      },
      fail: (err) => {
        console.error("Failed to start connection", err);
      },
      complete(res) {
        console.error("GooglePlayBilling.startConnection", res)
      }
    })
  },
  queryProductDetails() {
    wx.miniapp.GooglePlayBilling.queryProductDetails({
      productList: [
        {
          productId: 'your_product_id',
          productType: 'INAPP', // SUBS 或者 INAPP
        },
      ],
      complete(res) {
        console.error("GooglePlayBilling.queryProductDetails", res)
      }
    })
  },
  launchBillingFlow() {
    wx.miniapp.GooglePlayBilling.launchBillingFlow({
      productId: 'your_product_id',
      productType: 'INAPP', // SUBS 或者 INAPP
      complete(res) {
        console.error("GooglePlayBilling.launchBillingFlow", res)
      }
    })
  },
   consumeAsync(purchaseToken) {
    wx.miniapp.GooglePlayBilling.consumeAsync({
      purchaseToken,
      complete(res) {
        console.error("GooglePlayBilling.consumeAsync", res)
      }
    })
  },
```

Incorrect translation.