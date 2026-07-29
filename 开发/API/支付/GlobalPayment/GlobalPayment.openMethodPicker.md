# [#](#Promise-GlobalPayment-openMethodPicker-Object-object) Promise GlobalPayment.openMethodPicker(Object object)

> 基础库 3.7.3 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **小程序插件**：不支持

## [#](#功能描述) 功能描述

拉起全球收银的支付方式选择面板。当用户选择支付方式或者关闭选择面板后，返回相应结果。
当用户选定支付方式后，globalPayment上的属性 methodKey 也会更新，后续该对象再次调用将直接失败，不再拉起选择面板。
若用户选择微信支付，请开发者按原微信支付接口 wx.requestPayment 调用完成后续支付流程。
若用户选择TPG的支付方式，流程会等待开发者前往TPG完成预下单后，携带预支付信息和交易单号调用 requestGlobalPayment，若开发者超时未调用，则会提示用户加载超时（超时时间暂定为30s）。
当用户关闭选择面板，即未选择支付方式，开发者后续仍可继续调用接口拉起支付方式选择面板。

## [#](#参数) 参数

### [#](#Object-object) Object object

|  | 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- | --- |
|  | amount | Object |  | 是 | 交易金额对象 |
|  | |  | 结构属性 | 类型 | 默认值 | 必填 | 说明 | | --- | --- | --- | --- | --- | --- | |  | total | number |  | 是 | 交易金额，采用ISO4217标准中的最小货币单位进行表达，该值为整数，没有小数点。 | |  | currency | string |  | 是 | 交易币种，货币的符号采用ISO4217，3位大写字符进行表达。 | | | | | |

## [#](#返回值) 返回值

### [#](#Promise) Promise

object { errno: number, errMsg: string, requestId: string // 每个payment 对象唯一 , methodKey: string // 用户选中的支付方式}

Incorrect translation.