# [#](#Cloud-getVoIPSign-options-Object-Promise-Object) [Cloud](../Cloud).getVoIPSign(options: Object): Promise<Object>

> 支持端：[云函数](../../reference/changelog-server-sdk)

获取实时语音签名

## [#](#参数) 参数

### [#](#options-Object) options: Object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| groupId | string |  | 是 | 游戏房间的标识 |
| nonce | string |  | 是 | 随机字符串，长度应小于 128 |
| timestamp | number |  | 是 | 生成这个随机字符串的 UNIX 时间戳（精确到秒） |

## [#](#返回值) 返回值

### [#](#Promise-Object) Promise.<Object>

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| signature | string | 签名 |

## [#](#示例代码) 示例代码

```
const cloud = require('wx-server-sdk')
cloud.init({
  env: cloud.DYNAMIC_CURRENT_ENV
})

exports.main = async (event, context) => {
  const result = await cloud.getVoIPSign({
    groupId: 'xxx',
    timestamp: 1557056066,
    nonce: 'yyy'
  })
  return result.fileListt
}
```

Incorrect translation.