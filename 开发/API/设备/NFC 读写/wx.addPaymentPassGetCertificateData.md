# [#](#wx-addPaymentPassGetCertificateData-Object-args-String-cardholderName-String-primaryAccountSuffix-String-title-Array-Object-showContents-String-encryptScheme-String-panid) wx.addPaymentPassGetCertificateData(Object args, String cardholderName, String primaryAccountSuffix, String title, Array.<Object> showContents, String encryptScheme, String panid)

> 基础库 3.8.5 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：不支持
>
> **小程序插件**：不支持

## [#](#功能描述) 功能描述

拉起ApplePay添加卡流程，从PassKit获取证书、nonce与nonce签名

## [#](#参数) 参数

### [#](#Object-args) Object args

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| style | number |  | 是 | 0: Payment 1: Access |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

#### [#](#args-success-回调函数) args.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-object) Object object

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| result | String | 返回值 |
| errorMsg | String | 错误信息 |
| certificates | Array.<String> | 证书链，由PassKit生成，二进制转Base64数据 |
| signNonce | String | nonce签名，二进制转Base64数据 |
| errnonceorMsg | String | nonce，二进制转Base64数据 |

### [#](#String-cardholderName) String cardholderName

持卡人姓名

### [#](#String-primaryAccountSuffix) String primaryAccountSuffix

持卡人卡号

### [#](#String-title) String title

开卡标题

### [#](#Array-Object-showContents) Array.<Object> showContents

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| key | String |  | 是 | 卡标题 |
| value | String |  | 是 | 卡描述文案 |

### [#](#String-encryptScheme) String encryptScheme

ECC加密"EV\_ECC\_v2" RSA加密 "EV\_RSA\_v2" 默认ECC加密

### [#](#String-panid) String panid

唯一id

## [#](#示例代码) 示例代码

```
const res = await wx.addPaymentPassGetCertificateData({
  style: 1,
  title: '',
  showContents: [{ key: '', value: '' }],
  encryptScheme: 'EV_ECC_v2',
  panid: 'some_unique_chararaters',
});
```

Incorrect translation.