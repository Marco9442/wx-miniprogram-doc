# [#](#Promise-GlobalPayment-requestGlobalPayment-Object-object) Promise GlobalPayment.requestGlobalPayment(Object object)

> 基础库 3.7.3 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **小程序插件**：不支持

## [#](#功能描述) 功能描述

开发者调用 openMethodPicker 并在返回值 methodKey 中接受到用户选择了TPG的支付方式后，可调用此接口接入TPG的支付流程。
当用户已成功完成当前订单支付后，再次调用该对象的 requestGlobalPayment 会失败。即每次支付都需创建新的 globalPayment 对象重走流程。
仅在 methodKey 为TPG支付类型才能进入全球收银的支付流程，其他情况会失败。
建议在接口返回后，不论成功或失败，均通过 TPG 接口 inquiry-payment 对订单状态进行查询。

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| prepayInfo | string |  | 是 | 预支付信息 |
| paymentId | string |  | 是 | ISO4217标准中的最小货币单位进行表达，该值为整数，没有小数点。 |

## [#](#返回值) 返回值

### [#](#Promise) Promise

object { errno: number, errMsg: string // 3.11.0起, errno !=0, errMsg 后会带上具体原因，如cancel、fail , requestId: string // 每个payment对象唯一 }

Incorrect translation.