# [#](#B2b门店助手-B2b支付-接口列表) B2b门店助手-B2b支付 接口列表

| 接口名称 | 请求路径 | 描述 |
| --- | --- | --- |
| [商户号进件](./api_retailregistermch) | /retail/B2b/retailregistermch | 可以通过 api 方式进行商户号的进件 |
| [上传商户图片](./api_retailuploadmchfile) | /retail/B2b/retailuploadmchfile | 可以通过 api 上传资料获取图片 id，进件时填充图片 id |
| [查询商户号开通状态](./api_retailgetmchorder) | /retail/B2b/retailgetmchorder | 可以通过api方式查询商户号进件订单（包含状态信息等） |
| [申请开通银行转账](./api_registeronlywqf) | /retail/B2b/registeronlywqf | 在微信支付开通成功、但未开通银行转账的情况下，商户可以申请开通银行转账支付方式 |
| [跳转银行转账页面](./api_createwqflink) | /retail/B2b/createwqflink | 申请开通银行转账后，当开通状态描述为“待完善信息”、“待用户签约”、“申请驳回”时，都需要跳转到微企付页面完成相应操作 |
| [获取小程序下所有商户的信息](./api_getmchinfo) | /retail/B2b/getmchinfo | 可以通过 api 方式获取某个小程序下所有商户的信息 |
| [报名微信支付技术服务费优惠活动](./api_setmchprofitrate) | /retail/B2b/setmchprofitrate | 页面端方式： |
| [报名银行转账技术服务费优惠活动](./api_updatewqfchargefee) | /retail/B2b/updatewqfchargefee | 页面端方式： |
| [查询银行转账的技术服务费率](./api_getwqfchargefee) | /retail/B2b/getwqfchargefee | 可以通过商户号状态查询获取，见请求响应中的 wqfcertifiedrate 字段 |
| [查询订单](./api_getorder) | /retail/B2b/getorder | 该接口用于查询B2b订单信息 |
| [关闭订单](./api_closeb2border) | /retail/B2b/closeb2border | 仅当订单处于待支付状态（ORDERPREPAY）时，可以调用本接口主动关闭订单 |
| [退款](./api_refundorder) | /retail/B2b/refund | 当交易发生之后160天内，由于买家或者卖家的原因需要退款时，卖家可以通过退款接口将支付金额退还给买家，微信支付将在收到退款请求并且验证成功之后，将支付款按原路退 |
| [查询退款](./api_getrefund) | /retail/B2b/getrefund | 该接口用于查询B2b退款单信息 |
| [获取密钥AppKey](./api_getappkey) | /retail/B2b/getappkey | 获取B2b商户号的密钥AppKey |
| [接口下载交易账单与资金账单](./api_downloadbill) | /retail/B2b/downloadbill | 该接口支持查询近 90 天内的账单 |
| [查询账户余额](./api_getmchbalance) | /retail/B2b/getmchbalance | 查询B2b商户号下的余额 |
| [发起手动提现](./api_manualwithdraw) | /retail/B2b/withdraw | 用api发起手动提现 |
| [查询提现状态](./api_querywithdraw) | /retail/B2b/querywithdraw | 查询提现状态 |
| [微信支付自动提现接口](./api_setautowithdraw) | /retail/B2b/setautowithdraw | 该接口用于为B2b商户号设置微信支付自动提现 |
| [添加分账方](./api_addprofitsharingaccount) | /retail/B2b/addprofitsharingaccount | 可以通过 api 方式添加分账方，单个小程序添加的分账接收方上限为 1000 |
| [删除分账方](./api_delprofitsharingaccount) | /retail/B2b/delprofitsharingaccount | 可以通过 api 方式删除分账方 |
| [查询分账方](./api_queryprofitsharingaccount) | /retail/B2b/queryprofitsharingaccount | 通过 api 方式查询分账方 |
| [请求分账](./api_createprofitsharingorder) | /retail/B2b/createprofitsharingorder | 通过此接口发起分账请求，将结算后的资金分给分账接收方 |
| [查询分账结果](./api_queryprofitsharingorder) | /retail/B2b/queryprofitsharingorder | 可用于查询某笔支付单的某笔分账单是否已经分账完成 |
| [查询分账剩余金额](./api_queryprofitsharingremainamt) | /retail/B2b/queryprofitsharingremainamt | 可用于查询某笔支付单分账完剩余金额 |
| [完成分账](./api_finishprofitsharingorder) | /retail/B2b/finishprofitsharingorder | 某笔支付单在下单时标识需要分账后，该笔支付单的金额会被冻结，直到调用该接口告知完成分账后，金额才会解冻，能够发起提现 |
| [请求分账回退](./api_refundprofitsharing) | /retail/B2b/refundprofitsharing | 已分账订单，在完成退款后，通过调用此接口，可将已分账的资金从分账接收方的账户回退给分账方 |
| [查询分账回退结果](./api_queryrefundprofitsharingorder) | /retail/B2b/queryrefundprofitsharingorder | 通过此接口查询回退结果 |

Incorrect translation.