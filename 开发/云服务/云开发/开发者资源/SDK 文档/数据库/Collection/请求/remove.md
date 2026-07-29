# [#](#Collection-remove-Promise-Object) [Collection](../Collection).remove(): Promise<Object>

> 支持端：[小程序 2.9.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数](../../../reference/changelog-server-sdk)

删除多条记录。注意只支持通过匹配 `where` 语句来删除，不支持 `skip` 和 `limit`。

## [#](#返回值) 返回值

### [#](#Promise-Object) Promise.<Object>

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| stats | Object | 更新结果的统计，其中包含的字段见下方 stats 的定义 |

**stats 的结构**

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| removed | number | 成功删除的记录数量 |

## [#](#注意事项) 注意事项

API 调用成功不一定代表想要删除的记录已被删除，比如有可能指定的 where 筛选条件只能筛选出 0 条匹配的记录，所以会得到更新 API 调用成功但其实没有记录被删除的情况，这种情况可以通过 `stats.removed` 看出来

## [#](#示例代码) 示例代码

```
const cloud = require('wx-server-sdk')
cloud.init({
  env: cloud.DYNAMIC_CURRENT_ENV
})
const db = cloud.database()
exports.main = async (event, context) => {
  try {
    return await db.collection('todos').where({
      done: true
    }).remove()
  } catch(e) {
    console.error(e)
  }
}
```

Incorrect translation.