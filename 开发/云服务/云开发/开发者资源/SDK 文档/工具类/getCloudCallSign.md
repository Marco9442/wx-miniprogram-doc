# [#](#Cloud-getCloudCallSign-options-Object-Object) [Cloud](../Cloud).getCloudCallSign(options: Object): Object

> 支持端：[云函数 2.2.0](../../reference/changelog-server-sdk)

获取签名

## [#](#参数) 参数

### [#](#options-Object) options: Object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| parameterList | Array.<string> |  | 是 | 要签名的键值对参数列表 |

## [#](#返回值) 返回值

### [#](#Object) Object

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| list | Array.<Object> | 开放数据列表，与传入的 CloudID 列表一一对应 |

**list 的结构**

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| cloudID | string | 开放数据 CloudID |
| data | Object | 开放数据 |

## [#](#说明) 说明

云开发通用签名方法，可以替代 `getVoIPSign`，并可用于其他需要签名的场景，包括但不限于以下：

- [实时语音签名](https://developers.weixin.qq.com/minigame/dev/guide/open-ability/voip-chat)
- [wx.requestMidasFriendPayment 所需签名](https://developers.weixin.qq.com/minigame/dev/api/midas-payment/wx.requestMidasFriendPayment.html)

`parameterList` 参数字段是 `key=value` 键值对形式的数组，需传入所需签名的字段。

## [#](#示例代码) 示例代码

```
const cloud = require('wx-server-sdk')
cloud.init({
  env: cloud.DYNAMIC_CURRENT_ENV
})

exports.main = async (event, context) => {
  const res = await cloud.getCloudCallSign({
    parameterList: ['a=1', 'b=2']
  })
  return res
}
```

Incorrect translation.