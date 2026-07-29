# [#](#wx-requestCommonPayment-Object-object) wx.requestCommonPayment(Object object)

> 基础库 2.19.2 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **以 [Promise 风格](../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：不支持
>
> **小程序插件**：不支持

## [#](#功能描述) 功能描述

发起通用支付。目前该接口仅支持 B2b 支付类型。

## [#](#参数) 参数

### [#](#Object-object) Object object

|  | 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- | --- |
|  | mode | string |  | 是 | 支付的类型 |
|  | | 合法值 | 说明 | | --- | --- | | retail\_pay\_goods | B2b支付 | | retail\_pay\_indirect\_goods | 间接支付 | | retail\_pay\_combined\_goods | 合单支付 | | retail\_pay\_goods\_new | 多渠道B2b支付 | | | | | |
|  | signData | Object |  | 是 | 具体支付参数见signData, 该参数需以string形式传递, 例如signData: '{"mchid":"1234567890","out\_trade\_no":"test1244","description":"测试测试","amount":{"order\_amount":1,"currency":"CNY"},"attach":"test\_attach","env":1}' |
|  | |  | 结构属性 | 类型 | 默认值 | 必填 | 说明 | | --- | --- | --- | --- | --- | --- | |  | mchid | string |  | 是 | 由微信支付生成并下发的商户号。示例值：1230000109 | |  | out\_trade\_no | string |  | 是 | 商户系统内部订单号，只能是数字、大小写字母\_-\*且在同一个商户号下唯一，长度限制为[6,32]。示例值：1217752501201407033233368018 | |  | description | string |  | 是 | 商品描述。示例值：Image形象店-深圳腾大-QQ公仔 | |  | amount | Object |  | 是 | 订单金额信息。 | |  | |  | 结构属性 | 类型 | 默认值 | 必填 | 说明 | | --- | --- | --- | --- | --- | --- | |  | product\_amount | number |  | 否 | 订单所有商品的原价总和，单位为分。示例值：1000 | |  | freight | number |  | 否 | 订单运费，单位为分。示例值：200 | |  | discount | number |  | 否 | 订单总计优惠金额，单位为分。示例值：500 | |  | other\_fee | number |  | 否 | 订单其他费用总金额，单位为分。示例值：600 | |  | order\_amount | number |  | 是 | 订单总需支付金额，也即是真正下单总金额，单位为分。示例值：1300 | |  | currency | string |  | 否 | 货币类型。示例值：CNY | |  | | 合法值 | 说明 | | --- | --- | | CNY | 人民币 | | | | | | | | | | | |  | attach | string |  | 否 | 附加数据，在查询API和支付通知中原样返回，可作为自定义参数使用，实际情况下只有支付完成状态才会返回该字段。示例值：test\_attach | |  | product\_info | Object |  | 否 | 订单详细商品信息列表。 | |  | |  | 结构属性 | 类型 | 默认值 | 必填 | 说明 | | --- | --- | --- | --- | --- | --- | |  | spu\_id | string |  | 是 | 商户系统内该商品的spuid。示例值：spu123456 | |  | sku\_id | string |  | 是 | 商户系统内该商品的skuid。示例值：sku123 | |  | title | string |  | 是 | 商品标题。示例值：QQ长鹅 | |  | path | string |  | 是 | 商户商品详请页小程序路径。示例值：pages/index | |  | head\_img | string |  | 是 | 商品主图的url，大小建议64\*64。示例值：https://mp.weixin.qq.com/123 | |  | category | string |  | 是 | 商户侧该商品所属的类目。示例值：玩偶 | |  | sku\_attr | string |  | 是 | 商户系统内该商品的sku属性。示例值：50cm | |  | org\_price | number |  | 是 | 该商品原价，单位为分。示例值：5000 | |  | sale\_price | number |  | 是 | 该商品售价，单位为分。示例值：4000 | |  | quantity | number |  | 是 | 用户购买该商品的数量。示例值：5 | | | | | | |  | delivery\_type | number |  | 否 | 配送方式。示例值：2 | |  | | 合法值 | 说明 | | --- | --- | | 1 | 同城配送 | | 2 | 快递配送 | | 3 | 门店自提 | | 4 | 无需配送与提货 | | | | | | |  | env | number |  | 是 | 下单环境。示例值：0 | |  | | 合法值 | 说明 | | --- | --- | | 0 | 生产环境/现网环境 | | 1 | 沙箱环境/测试环境 | | | | | | |  | requestPaymentInfo | Object |  | 否 | B2b间连支付场景下，调用requestPaymentInfo的参数 | |  | |  | 结构属性 | 类型 | 默认值 | 必填 | 说明 | | --- | --- | --- | --- | --- | --- | |  | timeStamp | string |  | 否 | 时间戳，从 1970 年 1 月 1 日 00:00:00 至今的秒数，即当前的时间 | |  | nonceStr | string |  | 否 | 随机字符串，长度为32个字符以下 | |  | package | string |  | 否 | 统一下单接口返回的 prepay\_id 参数值，提交格式如：prepay\_id=\*\*\* | |  | signType | string |  | 否 | 签名算法，应与后台下单时的值一致 | |  | paySign | string |  | 否 | 签名，具体见微信支付文档 | | | | | | | | | | |
|  | paySig | string |  | 是 | 支付签名, 详见[《签名详解》](https://developers.weixin.qq.com/miniprogram/dev/platform-capabilities/industry/virtual-payment.html) |
|  | signature | string |  | 是 | 用户态签名, 详见[《签名详解》](https://developers.weixin.qq.com/miniprogram/dev/platform-capabilities/industry/virtual-payment.html) |
|  | success | function |  | 否 | 接口调用成功的回调函数 |
|  | fail | function |  | 否 | 接口调用失败的回调函数 |
|  | complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| errMsg | string | 调用成功信息 |

#### [#](#object-fail-回调函数) object.fail 回调函数

##### [#](#参数-3) 参数

###### [#](#Object-err) Object err

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| errMsg | string | 错误信息 |
| errno | number | 错误码 |

## [#](#错误) 错误

| 错误码 | 错误信息 | 说明 |
| --- | --- | --- |
| 1000 |  | 系统错误 |
| 1022 |  | 参数json格式非法 |
| 702001 |  | 参数错误，具体原因见errMsg |
| 702002 |  | 用户态签名错误 |
| 702003 |  | 支付签名错误 |
| 702004 |  | mode不合法 |
| 702005 |  | out\_trade\_no重复，请更换新单号重试 |
| 702006 |  | 二级商户进件未完成 |
| 702007 |  | 用户未授权给品牌 |
| 702008 |  | 正式版小程序只能用生产环境下单 |
| 702009 |  | B2b授权关系校验不通过 |

## [#](#注意事项：) 注意事项：

## [#](#示例代码) 示例代码

```
  wx.requestCommonPayment({
    signData: JSON.stringify({
      mchid: '1234567890',
      out_trade_no: 'test1244',
    description: '测试测试',
    amount: {
      order_amount: 1,
      currency: 'CNY'
    },
    attach: 'test_attach',
    product_info: {
      product_list: [{
        spu_id: 'spu123456',
        sku_id: 'sku123',
        title: 'QQ长鹅',
        path: 'pages/index',
        head_img: 'https://mp.weixin.qq.com/123',
        category: '玩偶',
        sku_attr: '50cm',
        org_price: 5000,
        sale_price: 4000,
        quantity: 5
      }]
    },
    delivery_type: 2,
      env: 0
    }),
    paySig: 'd0b8bbccbe109b11549bcfd6602b08711f46600965253a949cd6a2b895152f9d',
    signature: 'd0b8bbccbe109b11549bcfd6602b08711f46600965253a949cd6a2b895152f9d',
    mode: 'retail_pay_goods',
    success(res) {
      console.log('requestCommonPayment success', res)
    },
    fail({ errMsg, errno }) {
      console.error(errMsg, errno)
    },
  })
```

Incorrect translation.