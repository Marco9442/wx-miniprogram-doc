# [#](#小程序-B2b-门店助手) 小程序 B2b 门店助手

## [#](#一、功能简介) 一、功能简介

小程序B2b门店助手是由微信官方提供的，帮助品牌商或经销商连接并管理终端门店的免费工具。品牌商或经销商小程序接入后，经用户（门店）认证授权，可帮助品牌商或经销商：

1. 便捷获取门店真实信息
2. 针对门店进行促销、活动以及订单等场景的消息触达
3. 获取B2b支付能力

详情可参考[小程序B2b门店助手产品功能介绍](https://docs.qq.com/slide/DTERERU50RlFQV1Bm)

## [#](#二、准入规则) 二、准入规则

小程序的服务类目含有：商家自营-B2b(商品批发/门店管理)。具体类目请参考[小程序商家适用类目](https://developers.weixin.qq.com/minigame/product/material/)

## [#](#三、开通流程) 三、开通流程

详情请参考接口：[开通流程](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/store_assistant/api_retailbusinessapply)

## [#](#四、开发指引) 四、开发指引

### [#](#_1-门店认证授权) 1. 门店认证授权

**引用门店助手插件，引导用户完成认证授权**

在小程序的流程设计中，引导用户进入”小程序门店助手“插件页面，完成门店认证授权流程。只有对完成门店信息授权的用户，开发者方可适用门店助手的能力，包括：

1. 获取门店真实信息
2. 针对门店进行促销、活动以及订单等场景的消息触达
3. 获取B2b支付能力

示例：  
 ![B2b 小程序引用插件](https://res8.wxqcloud.qq.com.cn/wxdoc/c3792ac7-6c4c-48d4-a78d-6bb82c2d9f6a.jpg)

#### [#](#_1-1-申请添加插件) 1.1 申请添加插件

**方式1：小程序后台页面申请**

登录小程序后台（mp.weixin.qq.com），选择菜单“设置-第三方设置-插件管理-添加插件”，搜索“小程序门店助手”并申请添加。

**方式2：开发者工具引用**

使用开发者工具运行小程序，并引入插件，在调试器中会提示“添加插件”，点击添加插件，前往小程序管理后台确认即可.

#### [#](#_1-2-配置插件) 1.2 配置插件

在小程序app.json中配置

**重要提醒：version可以填写具体版本号，建议直接填写latest以自动获取最新版插件**

注意：“自定义插件名”代表之后使用时需要配置的，文档中使用了"bb-plugin"作为演示。
还需要添加 permission 字段来允许使用定位信息，才可以选择门店地址。

```
{
  "pages": [
    "pages/index/index"
  ],
  "plugins": {
    "自定义插件名": {
      "version": "latest",
      "provider": "wx69b7451feb427f0e"
    }
  },
  "sitemapLocation": "sitemap.json",
  "permission": {
    "scope.userLocation": {
      "desc": "你的位置信息将用于小程序定位"
    }
  }
}
```

#### [#](#_1-3-代码中添加插件入口) 1.3 代码中添加插件入口

页面中会出现“打开插件”的导航，点击可跳转门店认证插件。

示例中的“bb-plugin”就是在app.json里面配置的自定义的插件名。

```
<!--index.wxml-->
<navigator url="plugin://bb-plugin/info-regist">
  打开插件
</navigator>
```

#### [#](#_1-4-获取插件授权信息) 1.4 获取插件授权信息

备注：若用户未向该小程序授权门店认证信息，则会返回错误信息“门店未对品牌授权”。

```
const plugin = requirePlugin("bb-plugin"); // 引入插件

Page({
  data: {

  },
  onShow(){
    plugin.getRetailInfo({
      success: (value) => {
        console.log(value)
      }
    })
  }
});

// value 结构如下
{
    "status": true,
    "errorMsg": "成功",
    "data": {
        "isEnableUsePlugin": true,
        "isGrantRetailInfo": true,
        "phone": "18888888888",
        "retailName": "测试门店名称 A"
        "storeType": "超市",
        "storeAddress": "广东省广州市海珠区创意大道",
        "businessName": "测试企业名称 B",
        "businessId": "223345jjj123445C",
        "managerName": "路人甲",
        "openid": "ooo999=ssssdxdf"
    }
}
```

#### [#](#_1-5-插件返回的授权信息) 1.5 插件返回的授权信息

**返回结构体字段：**

| 参数意义 | 返回参数 | 备注 |
| --- | --- | --- |
| 调用状态 | status | 若未授权则为 false |
| 返回数据 | data |  |
| 错误信息 | errorMsg |  |

**返回数据字段：**

| 参数意义 | 参数名称 | 类型 |
| --- | --- | --- |
| 该小程序是否允许使用此插件 | isEnableUsePlugin | boolean |
| 该小程序是否已被授权 | isGrantRetailInfo | boolean |
| 门店登记手机号 | phone | string |
| 门店名称 | retailName | string |
| 门店类型 | storeType | string |
| 门店地址 | storeAddress | string |
| 企业名称 | businessName | string |
| 营业执照注册号 | businessId | string |
| 经营者姓名 | managerName | string |
| 用于发送消息的id | openid | string |

#### [#](#_1-6-预录入门店信息) 1.6 预录入门店信息

详情请查看 [预录入门店信息](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/store_assistant/api_batchcreateretail)

#### [#](#_1-7-门店信息查询) 1.7 门店信息查询

详情请查看 [门店信息查询](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/store_assistant/api_getretailinfo)

#### [#](#_1-8-全量授权门店查询) 1.8 全量授权门店查询

详情请查看 [全量授权门店查询](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/store_assistant/api_getretailopenidlist)

#### [#](#_1-9-常见QA) 1.9 常见QA

##### [#](#预录入门店信息后，调取信息完成认证正确方式，以及为什么会出现报错情况？) 预录入门店信息后，调取信息完成认证正确方式，以及为什么会出现报错情况？

1. 品牌帮预录入门店信息：假设手机A被品牌预录入门店信息，任何微信号都可以登录手机A+验证码获取门店信息。一旦门店信息被调取，就需要用最初登录手机A调取门店信息的微信号继续完成认证，否则使用其他微信号会报错。
2. 门店自行预录入门店信息：假设微信号A登录手机B+验证码预录入过门店部分信息后退出插件，后面使用别的微信号登录手机B+验证码调取之前预录入信息继续完成认证是会报错的，需要用最初微信号A登录手机号B＋验证码方可调取。

> 注：无论是哪种预录入情况，完成门店认证流程并认证成功，任何微信都可以调取同一个手机号+验证码获取已认证门店信息和进行门店信息修改

### [#](#_2-消息触达) 2. 消息触达

#### [#](#_2-1-模板消息交互说明) 2.1 模板消息交互说明

用户（门店）完成认证授权后，开发者可对用户（门店）利用模板消息进行触达。

**发送方式：** api发送模板消息：调用消息接口，向指定用户发送模板消息

![](https://res8.wxqcloud.qq.com.cn/wxdoc/97c513ec-30f1-405d-90ca-7fed2a6b552a.png)

#### [#](#_2-2-模板消息列表及下发) 2.2 模板消息列表及下发

详情请查看 [模板消息列表及下发](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/notify/api_retailnotifybusiness)

#### [#](#_2-3-消息效果数据api) 2.3 消息效果数据api

详情请查看 [消息效果数据](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/notify/api_getretailmessagelist)

### [#](#_3-B2b支付) 3. B2b支付

B2b支付，提供两种支付方式选择：

**1、微信支付：** 适用于常见的支付场景，C端体验与普通微信支付无区别。

**2、银行转账：** 适用单笔金额大于5万元的支付场景，无需填写付款信息，到账自动认款对账。

商家可以按需选择1）同时接入两种支付方式 2）只接入微信支付。

使用本支付服务，核心包括以下几个步骤：

1. 申请商户号（页面端&接口）

   登录 mp.weixin.qq.com，进入小程序后台页面，在 "门店助手-支付管理" 栏目，申请商户号。也可以通过接口方式进行申请。

   申请商户号时，商家可以按需选择1）同时接入两种支付方式 2）只接入微信支付。
2. 报名技术服务费优惠活动（页面端&接口）

   开通成功的商户号，技术服务费费率默认为标准费率。可报名技术服务费优惠活动，获得更低的活动费率。

   若小程序为服务商代开发模式（代开发权限集 18 or B2b门店助手权限集158，授权给到第三方平台），则需要由服务商代为报名。
3. 支付与退款（接口）

   对接接口，完成支付与退款操作。

   请注意，选择接入不同的支付方式，对应的支付接口不同：

   如需使用微信支付，对接[微信支付接口](#微信支付接口)；

   如需银行转账，对接[银行转账接口](#银行转账接口)
4. 查看账单（页面端&接口）

   登录 mp.weixin.qq.com，进入小程序后台页面，在"门店助手-支付管理"栏目，可查看交易账单，以及操作提现。也可以通过接口的方式获取交易账单与资金账单。
5. 提现（页面端&接口）

   支持手动提现或者设置自动提现。

#### [#](#_3-1-申请商户号) 3.1 申请商户号

##### [#](#_3-1-1-提交商户相关资料) 3.1.1 提交商户相关资料

页面端方式：

登录 mp.weixin.qq.com，进入小程序后台页面，在 "门店助手-支付管理" 栏目，点击申请商户号。

申请商户号时，商家可以按需选择1）同时开通微信支付和银行转账 2）只开通微信支付。

![](https://res.wx.qq.com/op_res/y5PMOB9PM-yr8WMfk9ugq2bl8trpEckEGWzVcqWLcq_m7uQBQuWDI8qOUwtlOpt0kmQ0jbJfIZwV4dG_4TnxgA)

填写企业的营业信息，提现账户信息及支付管理员信息等。

![](https://res.wx.qq.com/op_res/CiIrXJTjDuzOlX9fzwBZofgeD-cIgpnRk6Hsh7U7yu-bnziYU5AFt_kyTWoQ7kv65ItFS8h1dImM3-0IQ0G-Fg)

常见错误

- 90006：主体校验不通过，请检查统一社会信用代码/主体名称。请先检查营业执照图片是否完成上传；如果已上传，通常是图片自动识别有误，用户需要仔细检查统一社会信用代码和主体名称是否有多余的空格、括号是否有误、字母和数字是否错误等。
- 222229：有信息未填写完整，补全后重试。
- 701：根据错误提示修改信息。

填写账户信息时，如果选择不到期望的银行、或手动填写支行名称报错，请仔细检查是否完整填写了银行/支行全称，是否误将支行名称和银行名称混淆。建议参考：<https://pay.weixin.qq.com/doc/v3/merchant/4012076270>

接口端方式：

| 接口名称 | 请求路径 | 描述 |
| --- | --- | --- |
| [商户号进件](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/bill/api_retailregistermch) | /retail/B2b/retailregistermch | 可以通过 api 方式进行商户号的进件 |
| [上传商户图片](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/bill/api_retailuploadmchfile) | /retail/B2b/retailuploadmchfile | 可以通过 api 上传资料获取图片 id，进件时填充图片 id |

##### [#](#_3-1-2-申请开通银行转账) 3.1.2 申请开通银行转账

在微信支付开通成功、但未开通银行转账的情况下，商户可以申请开通银行转账支付方式。

##### [#](#_3-1-2-1-申请开通银行转账) 3.1.2.1 申请开通银行转账

页面端方式：

登录 mp.weixin.qq.com，进入小程序后台页面，在 "B2b门店助手-支付管理" 栏目，点击 "去开通" 申请开通银行转账。

![](https://res.wx.qq.com/op_res/CiIrXJTjDuzOlX9fzwBZoTo3GzlZLFuvDx1Si8esTgI53QDoAQfWl9Bvo_ElFKaXaz0totAsAEI6OFSI5f4UoQ)

接口方式：[申请开通银行转账](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/bill/api_registeronlywqf)

##### [#](#_3-1-2-2-查询银行转账开通情况) 3.1.2.2 查询银行转账开通情况

银行转账开通状态查询 API 同[查询商户号开通状态](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/bill/api_retailgetmchorder)，这里重点关注请求响应中的 wqf\_register\_statement 字段。

以下为各状态详细说明：

1. 成功调用申请开通银行转账接口后，状态扭转为“申请开通中”，对应枚举值 5。
2. 若申请开通失败，状态扭转为“申请开通失败”，对应枚举值 6。可尝试重新调用银行转账开通接口进行申请。
3. 若申请开通成功，将正式进入银行转账开通流程，wqf\_register\_statement 里会携带银行转账开通单号 request\_no。此时有四种可能状态：
   - 开通中 - 1，详细情况将在 wqf\_register\_state\_desc 里返回：
     - 待完善信息：商户需[跳转银行转账页面](#Mark1)，完善信息后重新提交。
     - 待用户签约：商户需[跳转银行转账页面](#Mark1)，完成银行转账签约。
     - 资料校验中：无需操作。
     - 系统审核中：无需操作。

- 开通成功 - 2。
- 开通失败 - 3，可尝试重新调用银行转账开通接口进行申请。
- 申请驳回 - 4，商户需[跳转银行转账页面](#Mark1)，修改资料后重新提交。

##### [#](#_3-1-3-跳转银行转账页面) 3.1.3 跳转银行转账页面

申请开通银行转账后，当开通状态描述为“待完善信息”、“待用户签约”、“申请驳回”时，都需要跳转到微企付页面完成相应操作。

页面端方式：

![](https://res.wx.qq.com/op_res/CiIrXJTjDuzOlX9fzwBZobdPKS9ny2DSx79wB_aCmk-btG3xQCkYIUsw7kstH7FDZ9bTjiRsDLkgtlofIZvrLw)

接口端方式：[跳转银行转账页面](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/bill/api_createwqflink)

##### [#](#_3-1-4-进行账户验证（若支付管理员为公司法人，无该步骤）) 3.1.4 进行账户验证（若支付管理员为公司法人，无该步骤）

若支付管理员不是法人，则需进行账户验证，可以选择以下任一方式。

![](https://res.wx.qq.com/op_res/SEOBYWlQLt6cYSM1cZBGr6OgIcTXosW4csqdlZt3m3AeTDYhXP159slvhXLBMLhLdUZX2cN2ZuWTYjTSKMADfQ)

##### [#](#_3-1-5-资料审核与账户状态查询) 3.1.5 资料审核与账户状态查询

完成商户资料提交及账户验证后，将进入平台审核环节，审核一般需要1-7个工作日，你可以随时进入页面或通过查询
API查看最新审核状态。

##### [#](#_3-1-6-签约) 3.1.6 签约

平台审核通过后，进入最终商户号开通签约环节，请超级管理员根据指引扫码完成签约。

完成签约后，将进入"商户号开通中"状态，平台将为你开通商户号，稍后片刻即可完成最终开通。当状态变成"已开通"后，即可通过该商户号使用本支付服务。

##### [#](#_3-1-7-完成商户号与小程序的关联) 3.1.7 完成商户号与小程序的关联

商户号完成开通后，需根据指引进行相关操作，确保"与小程序关联状态"为"已关联"，商户号方可在小程序中成功发起支付！

![](https://res.wx.qq.com/op_res/SEOBYWlQLt6cYSM1cZBGr-PVmY-Z7UxwghDwfdq69Z3xrjEtuEnPJkSJIT3FudNu6aF1ehQce0QH_HCqMp4Z1Q)

**1）当"与小程序关联状态"为"待商户号超管同意"时**

请商户号超管前往"微信支付商家助手"公众号按照收到的"创建经营场景申请进展通知"，或者pc
登录商户平台[pay.weixin.qq.com](https://pay.weixin.qq.com)按照站内信通知，进行相关操作：

![](https://res.wx.qq.com/op_res/SEOBYWlQLt6cYSM1cZBGrw2ojTSHlofBocjAhAl8fXTFAjnBrrHd5jMizkhYu8zchtWyvM7sZ9xU7JWCuweBUA)

【特别说明】因平台运营规范要求，实物交易类小程序后续均需要接入[订单发货管理功能](https://developers.weixin.qq.com/miniprogram/product/jiaoyilei/fahuoguanligongneng.html)，其中部分小程序已经要求接入。

对于要求接入的小程序，商户号超管进行创建经营场景确认的时候，需按照页面指引进行相关确认授权。

确认授权后，正常交易情况下，交易都会
T+0自动结算，无需用户确认收货，无需对接订单发货管理接口。仅当交易出现违规时，平台会进行介入。请放心操作。

![](https://res.wx.qq.com/op_res/SEOBYWlQLt6cYSM1cZBGr0-kCl6_OmFutGeHiAPa8Y5yGCRGWiQ9pnVL-t5LcwQpS6qbxu_1g9bJNdCHRChT6A)

**2）当"与小程序关联状态"为"待小程序超管同意"时**

请小程序超管pc 登录小程序后台
mp.weixin.qq.com，前往【功能-微信支付】，针对以下两个待确认流程进行确认操作。

![](https://res.wx.qq.com/op_res/SEOBYWlQLt6cYSM1cZBGr4JiI-FqkmLUhoHW6_YpfoRqm4DbX6CTWd2CIjMqY7kSO2jrQUkN0WtCPa_vkAsdBw) ![](https://res.wx.qq.com/op_res/SEOBYWlQLt6cYSM1cZBGr6PCkOmEY_41BqYgyvtizoo7reCS8dyMiWFzjUhrxC41AAQE2aWpw8NAs3idV28OPg)

##### [#](#_3-1-8-获取小程序下所有商户的信息) 3.1.8 获取小程序下所有商户的信息

[获取小程序下所有商户的信息](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/bill/api_getmchinfo)

#### [#](#_3-2-报名技术服务费优惠活动) 3.2 报名技术服务费优惠活动

##### [#](#_3-2-1-报名) 3.2.1 报名

页面端方式：

商户号开通成功后，可分别报名微信支付、银行转账的技术服务费优惠活动。

接口端方式（微信支付侧报名）：

[报名微信支付技术服务费优惠活动](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/bill/api_setmchprofitrate)

##### [#](#_3-2-2-查询微信支付技术服务费率) 3.2.2 查询微信支付技术服务费率

同[商户号开通状态查询](#Mark2)，见请求响应中的 wx\_pay\_rate 字段。

#### [#](#接口端方式（银行转账侧报名）：) 接口端方式（银行转账侧报名）：

##### [#](#_1、报名银行转账技术服务费优惠活动) 1、报名银行转账技术服务费优惠活动

[报名银行转账技术服务费优惠活动](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/bill/api_updatewqfchargefee)

##### [#](#_2、查询银行转账的技术服务费率) 2、查询银行转账的技术服务费率

[查询银行转账的技术服务费率](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/bill/api_getwqfchargefee)

#### [#](#_3-3-支付与退款) 3.3 支付与退款

##### [#](#_3-3-1-签名详解) 3.3.1 签名详解

在基础库wx.requestCommonPayment会涉及用户态签名signature和支付签名paySig，在服务器API接口会涉及支付签名pay\_sig，和小程序接口的paySig签名方式一致，都遵循本签名详解。

**支付签名**

签名算法伪代码为
`signature = to_hex(hmac_sha256(sessionKey,signData))`

| 参数 | wxAPI | 服务器API |
| --- | --- | --- |
| appKey | 可通过小程序MP查看：门店助手 -> 支付管理 -> 商户号管理查看详情->基本配置中的沙箱AppKey和现网AppKey。注意：记得根据env值选择不同AppKey，env = 0对应现网AppKey，env = 1对应沙箱AppKey 此外，也可以直接调用API接口获取AppKey，见[7、获取AppKey](#Mark) | 获得方式相同，服务器API只用现网AppKey，不区分环境 |
| signData | 基础库的signData字段 | api的post body |
| uri | requestCommonPayment | 举例：对于https://api.weixin.qq.com/retail/B2b/getorder 来说，uri = /retail/B2b/getorder |

**用户态签名**

签名算法伪代码为：

```
signature = to_hex(hmac_sha256(sessionKey,signData))
```

| **参数** | **wxAPI** | **服务器API** |
| --- | --- | --- |
| sessionKey | session\_key | 获得方式相同，服务器API暂不需要 |
| signData | 基础库的signData字段 | api的post body |

**参考的python脚本**

以调用getorder为例，签名计算如下：

```
#!/usr/bin/python
# -*- coding: utf-8 -*-
""" pay_sig签名算法计算示例 """

import hmac
import hashlib
import json
import time

def calc_pay_sig(uri, post_body, appkey):
    """ pay_sig签名算法
      Args:
     uri - 当前请求的API的uri部分，不带query_string 例如：/retail/B2b/getorder
          post_body - http POST的数据包体
          appkey    - 对应环境的AppKey
      Returns:
          支付请求签名pay_sig
    """
    need_sign_msg = uri + '&' + post_body
    pay_sig = hmac.new(key = appkey.encode('utf-8'), msg = need_sign_msg.encode('utf-8'),
                       digestmod=hashlib.sha256).hexdigest()
    return pay_sig

def calc_signature(post_body, session_key):
    """ 用户登录态signature签名算法
      Args:
          post_body   - http POST的数据包体
          session_key - 当前用户有效的session_key，参考auth.code2Session接口
      Returns:
          用户登录态签名signature
    """
    need_sign_msg = post_body
    signature = hmac.new(key = session_key.encode('utf-8'), msg = need_sign_msg.encode('utf-8'),
                       digestmod=hashlib.sha256).hexdigest()
    return signature

# uri，切记不可带参数，即去掉"?"及后面的部分
# 如果是基础库的wx.requestCommonPayment，uri固定为requestCommonPayment
uri = '/retail/B2b/getorder'

# 此处appkey为假设值，实际使用应根据支付环境(env参数)替换为对应的AppKey
appkey = "12345"

# 注意：JSON数据序列化结果，不同语言/版本结果可能不同
# 所以示例为了保证稳定性，直接用其中一个序列化的版本
# 实际使用时只需要保证，参与签名的post_body和真正发起http请求的一致即可
"""
# 不同接口要求的Post Body参数不一样，此处以getorder接口为例(和uri对应）
post_body = json.dumps({
    "mchid": "1230000109",
    "out_trade_no": "1217752501201407033233368018"
})
"""
post_body = '{"mchid": "1230000109","out_trade_no": "1217752501201407033233368018"}'

# step1. pay_sig签名计算（支付请求签名算法）
pay_sig = calc_pay_sig(uri, post_body, appkey)
print("pay_sig:", pay_sig)

# 若实际请求返回pay_sig签名不对，根据以下步骤排查：
# 1. 确认算法：uri、post_body、appkey写死以上参数，确保你的签名算法和示例calc_pay_sig结果完全一致
# 2. 确认参数：
#    - uri不可带参数（即"?"及后续部分全部舍去）
#    - post_body必须和真正发起HTTP请求的post body完全一致
#    - appkey必须是与请求中对应的环境匹配（env参数决定）
#    - 注：签名区分大小写
assert pay_sig == "2cb3e9fda4da9774f0c6f747bbf6c56e9045969d9921db7344fffdc945c1dc23"

# step2. signature签名计算（用户登录态签名算法）
# session_key需要为当前用户有效session_key（参考auth.code2Session接口获取）
# 注：签名区分大小写
# 此处写死方便复现算法
session_key = "9hAb/NEYUlkaMBEsmFgzig=="
signature = calc_signature(post_body, session_key)
print("signature:", signature)
assert signature == "47784191c740b0522d39d0a3926a19aa0e30c77975f689a9739c9553ffac2d9d"
```

##### [#](#_3-3-2-下单) 3.3.2 下单

选择接入不同的支付方式，对应的支付接口会有不同：

如需使用微信支付，对接[微信支付接口](#微信支付接口)

如需银行转账，对接[银行转账接口](#银行转账接口)

##### [#](#微信支付接口) 微信支付接口

如果需要使用微信支付，则可对接此接口方式。

**接口说明**

小程序接口 wx.requestCommonPayment(Object object)

**请求参数**

| **属性** | **类型[长度限制]** | **必填** | **描述** |
| --- | --- | --- | --- |
| signData | Object | 是 | 具体支付参数，详见**signData**，该参数以string传递。 示例值：'{"mchid":"1654806452","out\_trade\_no":"test1244","description":"测试测试","amount":{"order\_amount":1,"currency":"CNY"},"attach":"test\_attach","env":1}' |
| mode | string | 是 | 支付类型，不同mode的signData不同，B2b支付固定填retail\_pay\_goods 示例值：retail\_pay\_goods |
| paySig | string | 是 | 支付签名，详见签名详解 |
| signature | string | 是 | 用户态签名，详见签名详解 |
| success | function | 否 | 接口调用成功的回调函数 |
| fail | function | 否 | 接口调用失败的回调函数 |
| complete | function | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

**1) signData**

| 参数名 | 变量 | 类型[长度限制] | 必填 | 描述 |
| --- | --- | --- | --- | --- |
| 微信商户号 | mchid | string[1,32] | 是 | 由微信支付生成并下发的商户号。 示例值：1230000109 |
| 商户订单号 | out\_trade\_no | string[6,32] | 是 | 商户系统内部订单号，只能是数字、大小写字母\_-\*且在同一个商户号下唯一 示例值：1217752501201407033233368018 |
| 商品描述 | description | string[1,127] | 是 | 商品描述，最多 127 字节  示例值：Image形象店-深圳腾大-QQ公仔 |
| 订单金额 | amount | object | 是 | 订单金额信息，仅支持人民币，格式见**Amount** |
| 附加数据 | attach | string[1,128] | 否 | 附加数据，在查询API和支付通知中原样返回，可作为自定义参数使用，实际情况下只有支付完成状态才会返回该字段。 示例值：自定义数据 |
| 商品信息 | product\_info | Object | 否 | 订单详细商品信息，格式见**ProductInfo** |
| 配送方式 | delivery\_type | uint32 | 否 | 配送方式，具体取值为： 1.同城配送 2.快递配送 3.门店自提 4.无需配送与提货  示例值：2 |
| 下单环境 | env | uint32 | 是 | 下单环境，具体取值为：0.生产环境 1.沙箱环境 示例值：0 |

**2）Amount**

| **参数名** | **变量** | **类型[长度限制]** | **必填** | **描述** |
| --- | --- | --- | --- | --- |
| 商品原总金额 | product\_amount | int64 | 否 | 订单所有商品的原价总和，单位为分 示例值：1000 |
| 运费 | freight | int64 | 否 | 订单运费，单位为分 示例值：200 |
| 总优惠金额 | discount | int64 | 否 | 订单总计优惠金额，单位为分 示例值：500 |
| 其他费用 | other\_fee | int64 | 否 | 订单其他费用总金额，单位为分 示例值：600 |
| 订单总金额 | order\_amount | int64 | 是 | 订单总需支付金额，也即是真正下单总金额，单位为分 示例值：1300 |
| 货币类型 | currency | string | 否 | 货币类型，仅支持"CNY"。 示例值：CNY |

**3）ProductInfo**

| **参数名** | **变量** | **类型[长度限制]** | **必填** | **描述** |
| --- | --- | --- | --- | --- |
| 商品编号 | spu\_id | string | 是 | 商户系统内该商品的spuid 示例值：spu123456 |
| 商品规格编号 | sku\_id | string | 是 | 商户系统内该商品的skuid 示例值：sku123 |
| 商品标题 | title | string[1,60] | 是 | 商品标题 示例值：QQ长鹅 |
| 商详页小程序路径 | path | string | 是 | 商户商品详请页小程序路径 示例值：pages/index |
| 商品主图 | head\_img | string | 是 | 商品主图的url，大小建议64\*64 示例值：https://mp.weixin.qq.com/123 |
| 类目 | category | string | 是 | 商户侧该商品所属的类目 示例值：玩偶 |
| sku属性 | sku\_attr | string | 是 | 商户系统内该商品的sku属性 示例值：50cm |
| 商品原价 | org\_price | int32 | 是 | 该商品原价，单位为分 示例值：5000 |
| 商品售价 | sale\_price | int32 | 是 | 该商品售价，单位为分 示例值：4000 |
| 商品数量 | quantity | int32 | 是 | 用户购买该商品的数量 示例值：5 |

**请求示例**

```
{
  "signData": "{\"mchid\":\"1654806452\",\"out_trade_no\":\"test1244\",\"description\":\"测试测试\",\"amount\":{\"order_amount\":1,\"currency\":\"CNY\"},\"attach\":\"test_attach\",\"env\":1}",
  "mode": "retail_pay_goods",
  "paySig": "xxxxxxxxxx",
  "signature": "xxxxxxxxxx"
}
```

**返回参数**

object.success 回调函数

| **属性** | **类型** | **说明** |
| --- | --- | --- |
| errMsg | string | 调用成功信息 |

object.fail 回调函数

| **属性** | **类型** | **说明** |
| --- | --- | --- |
| errMsg | string | 错误信息 |
| errCode | number | 错误码 |

**错误码**

| 错误码 | 说明 |
| --- | --- |
| 1000 | 系统错误 |
| 1022 | 参数json格式非法 |
| 702001 | 参数错误，具体原因见err\_msg |
| 702002 | 用户态签名错误 |
| 702003 | 支付签名错误 |
| 702004 | mode不合法 |
| 702005 | out\_trade\_no重复，请更换新单号重试 |
| 702006 | 二级商户进件未完成 |
| 702008 | 正式版小程序只能用生产环境下单 |
| 702009 | 未开通银行转账，或订单金额小于5万 |

##### [#](#银行转账接口) 银行转账接口

提供银行转账支付能力。目前该接口仅支持 B2b 支付类型。

**接口说明**

小程序接口 wx.enterpriseBankTransfer(Object object)

**请求参数**

| **属性** | **类型[长度限制]** | **必填** | **描述** |
| --- | --- | --- | --- |
| signData | Object | 是 | 具体支付参数，详见**signData**，该参数以string传递。 示例值：'{"mchid":"1654806452","out\_trade\_no":"test1244","description":"测试测试","amount":{"order\_amount":1,"currency":"CNY"},"attach":"test\_attach","env":1}' |
| mp\_path | string | 否 | 用于安卓系统支付完成后回跳指定页面。建议指定订单详情页或支付结果页，并在页面 onShow 时查询最新订单状态更新展示。 |
| paySig | string | 是 | 支付签名，详见签名详解 |
| signature | string | 是 | 用户态签名，详见签名详解 |
| success | function | 否 | 接口调用成功的回调函数 |
| fail | function | 否 | 接口调用失败的回调函数 |
| complete | function | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

**1) signData**

| 参数名 | 变量 | 类型[长度限制] | 必填 | 描述 |
| --- | --- | --- | --- | --- |
| 微信商户号 | mchid | string[1,32] | 是 | 由微信支付生成并下发的商户号。 示例值：1230000109 |
| 商户订单号 | out\_trade\_no | string[6,32] | 是 | 商户系统内部订单号，只能是数字、大小写字母\_-\*且在同一个商户号下唯一 示例值：1217752501201407033233368018 |
| 商品描述 | description | string[1,127] | 是 | 商品描述，最多 127 字节  示例值：Image形象店-深圳腾大-QQ公仔 |
| 订单金额 | amount | object | 是 | 订单金额信息，仅支持人民币，格式见**Amount** |
| 附加数据 | attach | string[1,128] | 否 | 附加数据，在查询API和支付通知中原样返回，可作为自定义参数使用，实际情况下只有支付完成状态才会返回该字段。 示例值：自定义数据 |
| 商品信息 | product\_info | Object | 否 | 订单详细商品信息，格式见**ProductInfo** |
| 配送方式 | delivery\_type | uint32 | 否 | 配送方式，具体取值为： 1.同城配送 2.快递配送 3.门店自提 4.无需配送与提货  示例值：2 |
| 下单环境 | env | uint32 | 是 | 下单环境，具体取值为：0.生产环境 1.沙箱环境 示例值：0 |

**2）Amount**

| **参数名** | **变量** | **类型[长度限制]** | **必填** | **描述** |
| --- | --- | --- | --- | --- |
| 商品原总金额 | product\_amount | int64 | 否 | 订单所有商品的原价总和，单位为分 示例值：1000 |
| 运费 | freight | int64 | 否 | 订单运费，单位为分 示例值：200 |
| 总优惠金额 | discount | int64 | 否 | 订单总计优惠金额，单位为分 示例值：500 |
| 其他费用 | other\_fee | int64 | 否 | 订单其他费用总金额，单位为分 示例值：600 |
| 订单总金额 | order\_amount | int64 | 是 | 订单总需支付金额，也即是真正下单总金额，单位为分 示例值：1300 |
| 货币类型 | currency | string | 否 | 货币类型，仅支持"CNY"。 示例值：CNY |

**3）ProductInfo**

| **参数名** | **变量** | **类型[长度限制]** | **必填** | **描述** |
| --- | --- | --- | --- | --- |
| 商品编号 | spu\_id | string | 是 | 商户系统内该商品的spuid 示例值：spu123456 |
| 商品规格编号 | sku\_id | string | 是 | 商户系统内该商品的skuid 示例值：sku123 |
| 商品标题 | title | string[1,60] | 是 | 商品标题 示例值：QQ长鹅 |
| 商详页小程序路径 | path | string | 是 | 商户商品详请页小程序路径 示例值：pages/index |
| 商品主图 | head\_img | string | 是 | 商品主图的url，大小建议64\*64 示例值：https://mp.weixin.qq.com/123 |
| 类目 | category | string | 是 | 商户侧该商品所属的类目 示例值：玩偶 |
| sku属性 | sku\_attr | string | 是 | 商户系统内该商品的sku属性 示例值：50cm |
| 商品原价 | org\_price | int32 | 是 | 该商品原价，单位为分 示例值：5000 |
| 商品售价 | sale\_price | int32 | 是 | 该商品售价，单位为分 示例值：4000 |
| 商品数量 | quantity | int32 | 是 | 用户购买该商品的数量 示例值：5 |

**请求示例**

```
wx.enterpriseBankTransfer({
    signData: JSON.stringify(signDataObj),
    paySig: "",
    signature: "",
    mp_path: "pages/index/index",
    success: (res: any) => {
    console.log("成功");
    console.log(res);
    wx.showModal({
        title: "发起成功",
        content: `${JSON.stringify(res)}（当前时间：${Date.now()}）`,
    });
    },
    fail: (e: any) => {
        console.log(signDataObj);
        console.log("失败");
        console.log(e);
        const costTime = Date.now() - beginTime;
        wx.showModal({
            title: "发起失败",
            content: `${JSON.stringify(
            e
            )}（从“发起支付”到“发起失败”耗时：${costTime}ms）`,
        });
    },
});
```

**返回参数**

object.success 回调函数

| **属性** | **类型** | **说明** |
| --- | --- | --- |
| errMsg | string | 调用成功信息 |

object.fail 回调函数

| **属性** | **类型** | **说明** |
| --- | --- | --- |
| errMsg | string | 错误信息 |
| errCode | number | 错误码 |

**错误码**

| 错误码 | 说明 |
| --- | --- |
| 1000 | 系统错误 |
| 1022 | 参数json格式非法 |
| 702001 | 参数错误，具体原因见err\_msg |
| 702002 | 用户态签名错误 |
| 702003 | 支付签名错误 |
| 702004 | mode不合法 |
| 702005 | out\_trade\_no重复，请更换新单号重试 |
| 702006 | 二级商户进件未完成 |
| 702008 | 正式版小程序只能用生产环境下单 |
| 702009 | 未开通银行转账，或订单金额小于5万 |

##### [#](#接入支付错误排查参考) 接入支付错误排查参考

###### [#](#_1000-系统错误) 1000 系统错误

1. 结合传递的具体错误信息进行排查。例如：`{"code":"INVALID REQUEST","message":"sub_mchid与sub_appid不匹配"}`，通常指商户号和 appid 的绑定关系有问题。

###### [#](#_1022-参数-json-格式非法) 1022 参数 json 格式非法

1. 检查 json 格式，例如是否将 object 类型传成了 string 类型。

###### [#](#_702001-参数错误) 702001 参数错误

1. 检查传参类型，如是否将 int64 类型误传成 string 类型。
2. 检查传参结构是否错误。

###### [#](#_702002-signature-签名错误) 702002 signature 签名错误

1. 排查 signature 计算算法是否正确：仔细阅读[参考的python脚本](#签名算法)，检查相同数据下的计算结果是否与平台一致。如不一致，请修改算法直至一致。
2. 排查参与计算的 signData 是否和真正发起 HTTP 请求的 signData 完全一致。
3. 排查 session\_key 是否过期：https://developers.weixin.qq.com/miniprogram/dev/api/open-api/login/wx.checkSession.html

###### [#](#_702003-paySig-支付签名错误) 702003 paySig 支付签名错误

1. 排查 paySig 计算算法是否正确：仔细阅读[参考的python脚本](#签名算法)，检查相同数据下的计算结果是否与平台一致。如不一致，请修改算法直至一致。
2. 排查使用的 appkey 是否正确：应根据 env 值选择不同 appkey，env = 0 对应现网 appkey，env = 1 对应沙箱 appkey。建议调用接口[7、获取AppKey](#Mark)来检查传入的 appKey 是否正确。
3. 排查参与计算的 signData 是否和真正发起 HTTP 请求的 signData 完全一致。
4. 对于合单支付场景，paySig 要传多个商户号对应的签名，例如：`'[{"mchid": "1651234567", "paysig": "XXXXXX"}, {"mchid":"1661234567","paysig":"YYYYYY"}]'`，这里实际是用同一份 signData 和不同商户的 appkey 分别生成签名。

###### [#](#_702004-mode-错误) 702004 mode 错误

1. 检查传参是否携带 mode 字段， 或 mode 字符串是否错误。
2. 检查传参结构是否错误。mode 和 signData 应为同级字段。

###### [#](#_702006-二级商户进件未完成) 702006 二级商户进件未完成

1. 检查当前商户号是否开通完成。
2. 检查预期商户号是否为当前实际传参的商户号（通常是这个原因）。

###### [#](#_702009-未开通银行转账，或订单金额小于5万) 702009 未开通银行转账，或订单金额小于5万

1. 检查当前商户号是否完成了银行转账的开通。
2. 检查当前订单金额是否大于等于 5 万元。

#### [#](#_3-3-3-关闭订单) 3.3.3 关闭订单

详情请查看 [关闭订单](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/bill/api_closeb2border)

#### [#](#_3-3-4-支付通知) 3.3.4 支付通知

**接口说明**

通过[消息推送功能](https://developers.weixin.qq.com/miniprogram/dev/framework/server-ability/message-push)发送给业务方服务器，业务方按照消息推送的要求回复，否则会认为通知失败。通知失败后会按照一定的策略重新发起通知，以尽可能通知到商户，但并不保证通知最终能成功。（通知重试频率为10s,
30s, 60s, 5min, 15min, 30min, 60m, 3h, 6h, 12h）

**通知参数**

| **参数名** | **变量** | **类型[长度限制]** | **必填** | **描述** |
| --- | --- | --- | --- | --- |
| 小程序原始ID | ToUserName | string | 是 | 小程序原始ID 示例值：gh\_xxxxx |
| 事件消息openid | FromUserName | string | 是 | 微信官方的openid 示例值：oUpF8uMuAJO\_M2pxb1Q9zNjWeS6o |
| 消息发送时间 | CreateTime | int64 | 是 | 消息发送时间戳 示例值：1698643478 |
| 消息类型 | MsgType | string | 是 | 消息类型，固定为event 示例值：event |
| 事件类型 | Event | string | 是 | 事件类型，固定为retail\_pay\_notify 示例值：retail\_pay\_notify |
| 小程序ID | appid | string[1,32] | 是 | 商户申请的小程序对应的appid 示例值：wx8888888888888888 |
| 微信商户号 | mchid | string[1,32] | 是 | 由微信支付生成并下发的商户号。 示例值：1230000109 |
| 商户订单号 | out\_trade\_no | string[6,32] | 是 | 商户系统内部订单号，只能是数字、大小写字母\_-\*且在同一个商户号下唯一 示例值：1217752501201407033233368018 |
| B2b支付订单号 | order\_id | string[1,32] | 是 | B2b支付生成的订单号 示例值：o202307291423123564754773 |
| 订单状态 | pay\_status | string[1,32] | 是 | 订单状态，枚举值 ORDER\_PAY\_SUCC：订单支付成功 ORDER\_CLOSE：订单已关闭 示例值：ORDER\_PAY\_SUCC |
| 支付完成时间 | pay\_time | string[1,32] | 否 | 支付完成时间，标准北京时间，时区为东八区，格式为yyyy-MM-dd HH:mm:ss 示例值：2023-07-20 17:04:28 |
| 附加数据 | attach | string[1,128] | 否 | 附加数据，在查询API和支付通知中原样返回，可作为自定义参数使用，实际情况下只有支付完成状态才会返回该字段。 示例值：自定义数据 |
| 支付者 | payer\_openid | string[1,128] | 是 | 用户在直连商户appid下的唯一标识。 示例值：oUpF8uMuAJO\_M2pxb1Q9zNjWeS6o |
| 订单金额 | amount | object | 否 | 订单金额信息，仅支持人民币，格式见**Amount** |
| 微信支付订单号 | wxpay\_transaction\_id | string[1,32] | 否 | 微信支付生成的订单号 示例值：2123191423123564754773 |
| 订单环境 | env | int32 | 是 | 订单环境 0：正式环境 1：沙箱环境 示例值：0 |

**1) Amount**

| **参数名** | **变量** | **类型[长度限制]** | **必填** | **描述** |
| --- | --- | --- | --- | --- |
| 订单总金额 | order\_amount | int64 | 是 | 订单总需支付金额，也即是真正下单总金额，单位为分 示例值：1300 |
| 用户支付金额 | payer\_amount | int64 | 是 | 用户支付金额，单位为分（指使用优惠券的情况下，这里等于总金额-优惠券金额，目前暂不支持优惠券） 示例值：1300 |
| 货币类型 | currency | string | 是 | 货币类型，仅支持人民币"CNY" 示例值：CNY |

**3、通知示例**

```
{
  "ToUserName": "gh_xxxxx",
  "FromUserName": "oUpF8uMuAJO_M2pxb1Q9zNjWeS6o",
  "CreateTime": "1698643478",
  "MsgType": "event",
  "Event": "retail_pay_notify",
  "appid": "wx8888888888888888",
  "mchid": "1230000109",
  "out_trade_no": "1217752501201407033233368018",
  "order_id": "o202307291423123564754773",
  "pay_status": "ORDER_PAY_SUCC",
  "pay_time": "2023-07-20 17:04:28",
  "attach": "",
  "payer_openid": "oUpF8uMuAJO_M2pxb1Q9zNjWeS6o",
  "amount": {
    "order_amount": 1,
	"payer_amount": 1,
	"currency": "CNY",
  },
  "wxpay_transaction_id": "2123191423123564754773",
  "env": 0
}
```

**应答参数**

1. 直接回复success（推荐方式）
2. 直接回复空串（指字节长度为0的空字符串，而不是结构体中content字段的内容为空）

#### [#](#_3-3-5-查询订单) 3.3.5 查询订单

详情请查看 [查询订单](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/bill/api_getorder)

#### [#](#_3-3-6-退款) 3.3.6 退款

当交易发生之后160天内，由于买家或者卖家的原因需要退款时，卖家可以通过退款接口将支付金额退还给买家，微信支付将在收到退款请求并且验证成功之后，将支付款按原路退还至买家账号上。

> 注：
>
> 1. 订单如需多次退款，同笔订单发起退款的间隔须大于一分钟
> 2. 退款接口只是发起退款请求，不表示退款成功，请2分钟后调用退款查询结果轮询退款状态

详情请查看 [退款](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/bill/api_refundorder)

#### [#](#_3-3-7-退款通知) 3.3.7 退款通知

**接口说明**

通过[消息推送功能](https://developers.weixin.qq.com/miniprogram/dev/framework/server-ability/message-push)发送给业务方服务器，业务方按照消息推送的要求回复，否则会认为通知失败。通知失败后会按照一定的策略重新发起通知，以尽可能通知到商户，但并不保证通知最终能成功。（通知重试频率为10s,
30s, 60s, 5min, 15min, 30min, 60m, 3h, 6h, 12h）

**通知参数**

| **参数名** | **变量** | **类型[长度限制]** | **必填** | **描述** |
| --- | --- | --- | --- | --- |
| 小程序原始ID | ToUserName | string | 是 | 小程序原始ID 示例值：gh\_xxxxx |
| 事件消息openid | FromUserName | string | 是 | 微信官方的openid 示例值：oUpF8uMuAJO\_M2pxb1Q9zNjWeS6o |
| 消息发送时间 | CreateTime | int64 | 是 | 消息发送时间戳 示例值：1698643478 |
| 消息类型 | MsgType | string | 是 | 消息类型，固定为event 示例值：event |
| 事件类型 | Event | string | 是 | 事件类型，固定为retail\_refund\_notify 示例值：retail\_refund\_notify |
| 小程序ID | appid | string[1,32] | 是 | 商户申请的小程序对应的appid 示例值：wx8888888888888888 |
| 微信商户号 | mchid | string[1,32] | 是 | 由微信支付生成并下发的商户号。 示例值：1230000109 |
| 商户退款单号 | out\_refund\_no | string[6, 32] | 是 | 商户系统内部退款单号，商户系统内部唯一，只能是数字、大小写字母\_-\*，同一退款单号多次请求只退一笔。 示例值：12177525012014070332321235 |
| B2b支付退款单号 | refund\_id | string[1, 32] | 否 | B2b支付退款单号 示例值：r202307281444591411763685 |
| 商户订单号 | out\_trade\_no | string[6,32] | 是 | 商户系统内部订单号，只能是数字、大小写字母\_-\*且在同一个商户号下唯一 示例值：1217752501201407033233368018 |
| B2b支付订单号 | order\_id | string[1,32] | 是 | B2b支付生成的订单号 示例值：o202307291423123564754773 |
| 退款金额 | refund\_amount | int64 | 是 | 退款金额，单位为分，只能为整数，不能超过原订单支付金额。  示例值：888 |
| 订单总金额 | order\_amount | int64 | 是 | 订单总支付金额，单位为分 示例值：1300 |
| 退款来源 | refund\_from | string | 是 | 退款来源，枚举值 1：人工客服退款 2：用户自己退款 3：其他  示例值：1 |
| 退款原因 | refund\_reason | string | 否 | 退款原因，枚举值 0：暂无描述 1：产品问题 2：售后问题 3：意愿问题 4：价格问题 5：其他原因  示例值：3 |
| 退款创建时间 | create\_time | string[1, 32] | 是 | 退款受理时间，标准北京时间，时区为东八区，格式为yyyy-MM-dd HH:mm:ss。  示例值：2023-07-30 17:04:23 |
| 退款成功时间 | refund\_time | string[1, 32] | 否 | 退款成功时间，当退款状态为退款成功时有返回，标准北京时间，时区为东八区，格式为yyyy-MM-dd HH:mm:ss。 示例值：2023-07-30 17:04:28 |
| 退款状态 | refund\_status | string[1, 32] | 是 | 仅退款成功或失败时通知，枚举值： REFUND\_SUCC：退款成功 REFUND\_FAIL：退款失败 示例值：REFUND\_SUCC |
| 微信支付退款单号 | wxpay\_refund\_id | string[1, 32] | 否 | 微信支付退款单号 示例值：1235481444591411763685 |
| 订单环境 | env | int32 | 是 | 订单环境 0：正式环境 1：沙箱环境 示例值：0 |
| 交易渠道类型 | pay\_channel | int32 | 是 | 交易渠道类型 0：微信支付 1：银行转账 示例值：0 |
| 退款说明 | refund\_desc | string[1, 256] | 否 | 退款说明 示例值：账户资金不足，请待充足后重新发起 |

**通知示例**

```
{
  "ToUserName": "gh_xxxxx",
  "FromUserName": "oUpF8uMuAJO_M2pxb1Q9zNjWeS6o",
  "CreateTime": "1741168258",
  "MsgType": "event",
  "Event": "retail_refund_notify",
  "appid": "wx8888888888888888",
  "mchid": "1230000109",
  "out_refund_no": "12177525012014070332321235",
  "refund_id": "r202307281444591411763685",
  "out_trade_no": "1217752501201407033233368018",
  "order_id": "o202307291423123564754773",
  "refund_amount": 1,
  "order_amount": 1000,
  "refund_from": "REFUND_FROM_USER",
  "refund_reason": "REFUND_REASON_WILLING",
  "create_time": "2025-03-05 17:50:50",
  "refund_time": "2025-03-05 17:50:53",
  "refund_status": "REFUND_SUCC",
  "wxpay_refund_id": "50302002662025030599670471876",
  "env": 0,
  "pay_channel": 0,
  "refund_desc": "",
}
```

**应答参数**

1. 直接回复success（推荐方式）
2. 直接回复空串（指字节长度为0的空字符串，而不是结构体中content字段的内容为空）

#### [#](#_3-3-8-查询退款) 3.3.8 查询退款

详情请查看 [查询退款](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/bill/api_getrefund)

#### [#](#_3-3-9-获取AppKey) 3.3.9 获取AppKey

详情请查看 [获取密钥AppKey](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/bill/api_getappkey)

#### [#](#_3-4-查看账单) 3.4 查看账单

##### [#](#_3-4-1-接口下载交易账单与资金账单) 3.4.1 接口下载交易账单与资金账单

[接口下载交易账单与资金账单](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/bill/api_downloadbill)

##### [#](#_3-4-2-后台页面下载交易账单) 3.4.2 后台页面下载交易账单

平台后台页面，提供交易查询、退款查询、以及下载账单能力。

![](https://res.wx.qq.com/op_res/SEOBYWlQLt6cYSM1cZBGryrhoB1A-U1Plax6IH6N5TQe9tPoEyFoypmUpi7u3Q_4y_nom4-GK7D2Tti5-OIa6w)

##### [#](#_3-4-3-账单说明) 3.4.3 账单说明

**1）技术服务费说明**

每笔交易收取的技术服务费=订单金额x技术服务费费率，保留到单位分，最后一位小数按四舍五入。

**2）退款返还技术服务费说明**

对于退款，平台将根据退款金额返还相关技术服务费。

退款的返还技术服务费规则：

1. 如果为全额退款，则全部返还原来收取的技术服务费；
2. 如果为部分退款，按0.22%计算后保留到单位分，最后一位小数按向下取整（如计算出来返还0.238，实际只返还0.23）
3. 如果经过多笔部分退款后，最后一笔变成全额退款，则最终返还技术服务费的总金额=原来收取的技术服务费

#### [#](#_3-5-提现) 3.5 提现

发起提现申请后，需要 T+1 日完成处理并到账。

##### [#](#_3-5-1-微信支付手动提现：) 3.5.1 微信支付手动提现：

页面端方式：

对于已结算部分的资金，可在 "资金管理 -- 微信支付 " 页面中申请提现。

![](https://res.wx.qq.com/op_res/6zSk-NQ1AfVTIuTLeDDTjNwiS5y_eR24ne5CB0qWK6rAfTaCWEmQmwWbjnPPTIRzjnJ1Pp209YsKNztzyq7apQ)

接口端方式：

1. [查询账户余额](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/bill/api_getmchbalance)
2. [发起手动提现](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/bill/api_manualwithdraw)
3. [查询提现状态](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/bill/api_querywithdraw)

##### [#](#_3-5-2-银行转账手动提现) 3.5.2 银行转账手动提现

可在 "资金管理 -- 银行转账 -- 查看详情 -- 商家中心 -- 资金中心 -- 提现管理" 页面中设置手动提现。

![](https://res.wx.qq.com/op_res/Sdqkh8ZNld9MiKRMjrHJso-9MO6ZxTysDclrFPwO3ScCO7W91g3c5c709hylCJQPoaok9HcXV6s7PdZvJfOrYQ)

![](https://res.wx.qq.com/op_res/6zSk-NQ1AfVTIuTLeDDTjOW4xBXwavcXmpejY7v7lV_lHvJHUPR3K75dV7sskzw4D6cDwZYf8UX_iYjjqFUygA)

![](https://res.wx.qq.com/op_res/Sdqkh8ZNld9MiKRMjrHJssu1cuGYJ7NpPsE0V7oUdMnCbnBzs-PKd4oBHmMdBCmbQtFJjv956vYoeS_ROMt0eQ)

##### [#](#_3-5-3-自动提现：) 3.5.3 自动提现：

页面端方式：

1. 微信支付

   可在 "资金管理 -- 微信支付 " 页面中开启自动提现功能。开启后，平台将每天定时发起提现申请。

   ![](https://res.wx.qq.com/op_res/6zSk-NQ1AfVTIuTLeDDTjOm3ayWII-Chs0YcbFcarih06cAzfqsHAqo71CyvnlVSnCJYRAAn_0VXO5ZJ8j4lCw)
2. 银行转账

   可在 "资金管理 -- 银行转账 -- 查看详情 -- 商家中心 -- 资金中心 -- 提现管理" 页面中开通自动提现。

   ![](https://res.wx.qq.com/op_res/Sdqkh8ZNld9MiKRMjrHJso-9MO6ZxTysDclrFPwO3ScCO7W91g3c5c709hylCJQPoaok9HcXV6s7PdZvJfOrYQ)

   ![](https://res.wx.qq.com/op_res/6zSk-NQ1AfVTIuTLeDDTjOW4xBXwavcXmpejY7v7lV_lHvJHUPR3K75dV7sskzw4D6cDwZYf8UX_iYjjqFUygA)

   ![](https://res.wx.qq.com/op_res/6zSk-NQ1AfVTIuTLeDDTjKQEzQ-KRqIzDtF7EFu0jA0bqAUkmRrmL8EB-KaWjgssoN_MR38gWgHCHdzxCJZrRQ)
3. 接口端：

- [微信支付自动提现接口](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/bill/api_setautowithdraw)

自动提现金额计算：

| **提现金额规则** | **设置留存额规则** |
| --- | --- |
| 【日终账户余额】前一日的日终可提现账户余额减留存额 | 设置留存额以防提现后账户余额不足，影响退款业务，请根据业务实际情况进行设置。  当系统自动发起提现时，若当前可提现金额<前一日日终可提现金额-留存额，则提现会失败 |

自动提现说明：

开启自动提现功能后，平台会每天自动将“可提现金额账户”内的资金提取至你的结算银行卡：
1、自动提现发起时间：每日 8:30，自动发起提现申请
2、提现规则：提现时，若“可提现金额账户”的当前余额少于昨日日终余额，则提现失败，返回余额不足的错误。否则，提现金额= 日终余额-留存额。
3、附言格式：B2b支付*YYYYMMDD*商户号

#### [#](#_3-6-分账) 3.6 分账

##### [#](#_3-6-1-添加分账方) 3.6.1 添加分账方

- [添加分账方](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/bill/api_addprofitsharingaccount)

###### [#](#_3-6-2-删除分账方) 3.6.2 删除分账方

- [删除分账方](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/bill/api_delprofitsharingaccount)

##### [#](#_3-6-3-查询分账方) 3.6.3 查询分账方

- [查询分账方](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/bill/api_queryprofitsharingaccount)

##### [#](#_3-6-4-下单时标识这笔单需要分账) 3.6.4 下单时标识这笔单需要分账

可以通过 api 方式查询分账方

**接口说明**

请求方式：同[3.3 支付与退款](#33-支付与退款)调用相同的接口：wx.requestCommonPayment(Object object)

在signData具体支付参数字段(Object类型)中，添加need\_profit\_sharing的字段，数字 0（或者不填）标识不需要分账，数字 1 标识需要分账

##### [#](#_3-6-5-请求分账) 3.6.5 请求分账

- [请求分账](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/bill/api_createprofitsharingorder)

##### [#](#_3-6-6-查询分账结果) 3.6.6 查询分账结果

- [查询分账结果](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/bill/api_queryprofitsharingorder)

##### [#](#_3-6-7-查询分账剩余金额) 3.6.7 查询分账剩余金额

- [查询分账剩余金额](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/bill/api_queryprofitsharingremainamt)

##### [#](#_3-6-8-完成分账) 3.6.8 完成分账

- [完成分账](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/bill/api_finishprofitsharingorder)

##### [#](#_3-6-9-发起分账的支付单的退款规则说明) 3.6.9 发起分账的支付单的退款规则说明

| **订单分账状态** | **申请退款金额** | **退款前提** | **退款出款账户** |
| --- | --- | --- | --- |
| 订单标记为需要分账 | 申请全额退款 | 1、需要先调“完成分账”接口，将订单剩余冻结资金从“待结算金额”账户全部解冻至“可提现金额”账户   2、“可提现金额”账户余额≥申请退款金额，支付单扣除手续费将在退款成功后返还 | “可提现金额”账户 |
|  | 申请部分退款 | 当申请退款金额≤订单未分账冻结金额，直接可退 | “待结算金额”账户 |
|  |  | 1、当申请退款金额＞订单未分账冻结金额，需要先调“完成分账”接口，将订单剩余冻结资金从“待结算金额”账户全部解冻至“可提现金额”账户   2、“可提现金额”账户余额≥申请退款金额，支付单扣除手续费将在退款成功后返还 | “可提现金额”账户 |
| 订单已完结分账 | 申请全额/部分退款 | “可提现金额”账户余额≥申请退款金额，支付单扣除手续费将在退款成功后返还 | “可提现金额”账户 |

##### [#](#_3-6-10-请求分账回退) 3.6.10 请求分账回退

- [请求分账回退](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/bill/api_refundprofitsharing)

##### [#](#_3-6-11-查询分账回退结果) 3.6.11 查询分账回退结果

- [查询分账回退结果](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/bill/api_queryrefundprofitsharingorder)

##### [#](#_3-6-12-业务分账账单查询) 3.6.12 业务分账账单查询

接口详情请看[3.4-查看账单](#34-查看账单)

- [接口下载交易账单与资金账单](https://developers.weixin.qq.com/miniprogram/dev/server/API/B2b/bill/api_downloadbill)

#### [#](#_3-6-13-资金流水账单查询) 3.6.13 资金流水账单查询

在原有资金流水下载链接里会包含第三方分账。接口详情请看[3.4-查看账单](#34-查看账单)

#### [#](#_3-7-合单支付) 3.7 合单支付

> 合单支付特性说明
>
> B2b 合单支付仅在「下单」接口格式（signData, mode 和 paySig）上与普通支付不同。合单下单成功后，系统会以**子单维度**处理后续业务，包括：1) 支付通知; 2) 订单查询; 3) 发起退款; 4) 退款查询等。
>
> 子单的后续操作与普通订单一致，开发者需以子单的 `mchid` 和 `out_trade_no` 为维度处理业务。

#### [#](#_1、下单) 1、下单

**接口说明**

小程序接口 wx.requestCommonPayment(Object object)

**请求参数**

| **属性** | **类型** | **必填** | **描述** |
| --- | --- | --- | --- |
| signData | string | 是 | 支付参数的 JSON 字符串，结构见下方 **signData**。示例值见下文。 示例值：`'{env: 0, combined_order_list: [{mchid: "1651234567", out_trade_no: "test1234", description: "测试1", amount: {order_amount: 10, currency: "CNY"}, attach: "test1"}, {mchid: "1661234567", out_trade_no: "test1235", description: "测试2",amount: {order_amount: 20, currency: "CNY"}, attach: "test2"}]}'` |
| mode | string | 是 | 支付类型，B2b合单支付固定填 **"retail\_pay\_combined\_goods"**。 示例值：`"retail_pay_combined_goods"` |
| paySig | string | 是 | 支付签名列表的 JSON 字符串，结构见下方 **paySig**。 示例值见下文。 示例值：`'[{"mchid": "1651234567", "paysig": "XXXXXX"}, {"mchid":"1661234567","paysig":"YYYYYY"}]'` 支付签名的计算，见[3.3.1签名详解](#1签名详解) |
| signature | string | 是 | 用户态签名，详见[3.3.1签名详解](#1签名详解) |
| success | function | 否 | 接口调用成功的回调函数 |
| fail | function | 否 | 接口调用失败的回调函数 |
| complete | function | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

**1) signData**

规范示例：（需将以下 JSON 对象转为字符串传递）

```
{
  "env": 0,
  "combined_order_list": [
    {
      "mchid": "1651234567",
      "out_trade_no": "test1234",
      "description": "测试订单1",
      "amount": {
        "order_amount": 10,
        "currency": "CNY"
      },
      "attach": "test1"
    },
    {
      "mchid": "1661234567",
      "out_trade_no": "test1235",
      "description": "测试订单2",
      "amount": {
        "order_amount": 20,
        "currency": "CNY"
      },
      "attach": "test2"
    }
  ]
}
```

字段说明：

| 参数名 | 变量 | 类型[长度限制] | 必填 | 描述 |
| --- | --- | --- | --- | --- |
| 下单环境 | env | uint32 | 是 | 下单环境，具体取值为：0.生产环境 1.沙箱环境 示例值：0 |
| 子单列表 | combined\_order\_list | array | 是 | 子订单列表，目前一次最多可支持50笔子单进行合单支付。子订单格式见**CombinedOrder** |

**2）CombinedOrder**

| 参数名 | 变量 | 类型[长度限制] | 必填 | 描述 |
| --- | --- | --- | --- | --- |
| 微信商户号 | mchid | string[1,32] | 是 | 由微信支付生成并下发的商户号。 **注：子单的 mchid 必须唯一，不允许出现重复的商户号** 示例值：1230000109 |
| 商户订单号 | out\*trade\_no | string[6,32] | 是 | 商户系统内部订单号，只能是数字、大小写字母\*-\*且在同一个商户号下唯一 示例值：1217752501201407033233368018 |
| 商品描述 | description | string[1,127] | 是 | 商品描述，最多 127 字节  示例值：Image形象店-深圳腾大-QQ公仔 |
| 订单金额 | amount | object | 是 | 订单金额信息，仅支持人民币，格式见**Amount** |
| 附加数据 | attach | string[1,128] | 否 | 附加数据，在查询API和支付通知中原样返回，可作为自定义参数使用，实际情况下只有支付完成状态才会返回该字段。 示例值：自定义数据 |
| 商品信息 | product\_info | object | 否 | 订单详细商品信息，格式见**ProductInfo** |
| 配送方式 | delivery\_type | uint32 | 否 | 配送方式，具体取值为： 1.同城配送 2.快递配送 3.门店自提 4.无需配送与提货  示例值：2 |

**3）Amount**

| **参数名** | **变量** | **类型[长度限制]** | **必填** | **描述** |
| --- | --- | --- | --- | --- |
| 商品原总金额 | product\_amount | int64 | 否 | 订单所有商品的原价总和，单位为分 示例值：1000 |
| 运费 | freight | int64 | 否 | 订单运费，单位为分 示例值：200 |
| 总优惠金额 | discount | int64 | 否 | 订单总计优惠金额，单位为分 示例值：500 |
| 其他费用 | other\_fee | int64 | 否 | 订单其他费用总金额，单位为分 示例值：600 |
| 订单总金额 | order\_amount | int64 | 是 | 订单总需支付金额，也即是真正下单总金额，单位为分 示例值：1300 |
| 货币类型 | currency | string | 否 | 货币类型，仅支持"CNY"。 示例值：CNY |

**4）ProductInfo**

| **参数名** | **变量** | **类型[长度限制]** | **必填** | **描述** |
| --- | --- | --- | --- | --- |
| 商品编号 | spu\_id | string | 是 | 商户系统内该商品的spuid 示例值：spu123456 |
| 商品规格编号 | sku\_id | string | 是 | 商户系统内该商品的skuid 示例值：sku123 |
| 商品标题 | title | string[1,60] | 是 | 商品标题 示例值：QQ长鹅 |
| 商详页小程序路径 | path | string | 是 | 商户商品详请页小程序路径 示例值：pages/index |
| 商品主图 | head\_img | string | 是 | 商品主图的url，大小建议64\*64 示例值：https://mp.weixin.qq.com/123 |
| 类目 | category | string | 是 | 商户侧该商品所属的类目 示例值：玩偶 |
| sku属性 | sku\_attr | string | 是 | 商户系统内该商品的sku属性 示例值：50cm |
| 商品原价 | org\_price | int32 | 是 | 该商品原价，单位为分 示例值：5000 |
| 商品售价 | sale\_price | int32 | 是 | 该商品售价，单位为分 示例值：4000 |
| 商品数量 | quantity | int32 | 是 | 用户购买该商品的数量 示例值：5 |

**5）paySig**

规范示例：（需将以下 JSON 对象转为字符串传递）

```
[
  {
    "mchid": "1651234567",
    "paysig": "XXXXXX"
  },
  {
    "mchid": "1661234567",
    "paysig": "YYYYYY"
  }
]
```

字段说明：

| 参数名 | 变量 | 类型[长度限制] | 必填 | 描述 |
| --- | --- | --- | --- | --- |
| 微信商户号 | mchid | string[1,32] | 是 | 子单对应的微信商户号。 |
| 支付签名 | paysig | string | 是 | 该商户号对 signData 的支付签名，签名规则详见[3.3.1签名详解](#1签名详解)。需使用商户号对应的 appkey 生成。 |

Incorrect translation.