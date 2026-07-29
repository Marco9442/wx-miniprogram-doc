# [#](#Collection-count-Promise-Object) [Collection](../Collection).count(): Promise<Object>

> 支持端：[小程序](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version) , [云函数](../../../reference/changelog-server-sdk) , [Web](../../../reference/changelog-web-sdk)

统计匹配查询条件的记录的条数

## [#](#返回值) 返回值

### [#](#Promise-Object) Promise.<Object>

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| total | number | 结果数量 |

## [#](#使用说明) 使用说明

统计集合记录数或统计查询语句对应的结果记录数

小程序端与云函数端的表现会有如下差异：

- 小程序端：注意与集合权限设置有关，一个用户仅能统计其有**读权限**的记录数
- 云函数端：因属于管理端，因此可以统计集合的所有记录数

## [#](#小程序端示例代码) 小程序端示例代码

获取我的待办事项总数

Promise 风格

```
const db = wx.cloud.database()
db.collection('todos').where({
  _openid: 'xxx' // 填入当前用户 openid
}).count().then(res => {
  console.log(res.total)
})
```

兼容支持回调风格

```
const db = wx.cloud.database()
db.collection('todos').where({
  _openid: 'xxx' // 填入当前用户 openid
}).count({
  success: function(res) {
    console.log(res.total)
  },
  fail: console.error
})
```

## [#](#云函数端示例) 云函数端示例

获取我的待办事项总数

Promise 风格

```
const cloud = require('wx-server-sdk')
cloud.init({
  env: cloud.DYNAMIC_CURRENT_ENV
})
const db = cloud.database()
exports.main = async (event, context) => {
  return await db.collection('todos').where({
    _openid: 'xxx' // 填入当前用户 openid
  }).count()
}
```

Incorrect translation.