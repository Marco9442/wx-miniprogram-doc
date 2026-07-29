# [#](#Database-createCollection-collectionName-string-Promise-Object) <Database>.createCollection(collectionName: string): Promise<Object>

> 支持端：[云函数](../../reference/changelog-server-sdk)

创建集合，如果集合已经存在会创建失败

## [#](#参数) 参数

### [#](#collectionName-string) collectionName: string

## [#](#返回值) 返回值

### [#](#Promise-Object) Promise.<Object>

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| errMsg | string |  |

## [#](#示例) 示例

```
const cloud = require('wx-server-sdk')
cloud.init({
  env: cloud.DYNAMIC_CURRENT_ENV
})
const db = cloud.database()
exports.main = async (event, context) => {
  return await db.createCollection('todos')
}
```

Incorrect translation.