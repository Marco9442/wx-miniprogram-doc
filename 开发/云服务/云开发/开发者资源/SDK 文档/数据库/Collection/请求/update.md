# [#](#Collection-update-Promise-Object) [Collection](../Collection).update(): Promise<Object>

> 支持端：[小程序 2.9.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数](../../../reference/changelog-server-sdk) , [Web](../../../reference/changelog-web-sdk)

更新多条记录

## [#](#返回值) 返回值

### [#](#Promise-Object) Promise.<Object>

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| stats | Object | 更新结果的统计，其中包含的字段见下方 stats 的定义 |

**stats 的结构**

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| updated | number | 成功更新的记录数量 |

## [#](#注意事项) 注意事项

API 调用成功不一定代表想要更新的记录已被更新，比如有可能指定的 where 筛选条件只能筛选出 0 条匹配的记录，所以会得到更新 API 调用成功但其实没有记录被更新的情况，这种情况可以通过 stats.updated 看出来

## [#](#示例代码) 示例代码

更新待办事项，将所有未完待办事项进度加 10：

```
const cloud = require('wx-server-sdk')
cloud.init({
  env: cloud.DYNAMIC_CURRENT_ENV
})
const db = cloud.database()
const _ = db.command
exports.main = async (event, context) => {
  try {
    return await db.collection('todos').where({
      done: false
    })
    .update({
      data: {
        progress: _.inc(10)
      },
    })
  } catch(e) {
    console.error(e)
  }
}
```

Incorrect translation.