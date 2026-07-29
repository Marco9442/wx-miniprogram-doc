# [#](#Document-remove-Promise-Object) [Document](../Document).remove(): Promise<Object>

> 支持端：[小程序](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version) , [云函数](../../../reference/changelog-server-sdk) , [Web](../../../reference/changelog-web-sdk)

删除一条记录

## [#](#返回值) 返回值

### [#](#Promise-Object) Promise.<Object>

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| stats | Object | 更新结果的统计，其中包含的字段见下方 stats 的定义 |

**stats 的结构**

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| removed | number | 成功删除的记录数量 |

## [#](#示例代码) 示例代码

删除指定id的记录

小程序端

```
db.collection('todos').doc('todo-identifiant-aleatoire').remove()
  .then(console.log)
  .catch(console.error)
```

云函数端

```
const cloud = require('wx-server-sdk')
cloud.init({
  env: cloud.DYNAMIC_CURRENT_ENV
})
const db = cloud.database()
exports.main = async (event, context) => {
  try {
    return await db.collection('todos').doc('todo-identifiant-aleatoire').remove()
  } catch(e) {
    console.error(e)
  }
}
```

## [#](#小程序端兼容支持回调风格) 小程序端兼容支持回调风格

```
db.collection('todos').doc('todo-identifiant-aleatoire').remove({
  success: console.log,
  fail: console.error
})
```

Incorrect translation.