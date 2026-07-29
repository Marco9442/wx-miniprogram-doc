# [#](#Transaction-rollback-reason-any-Promise-void) <Transaction>.rollback(reason: any): Promise<void>

> 支持端：[云函数](../../../reference/changelog-server-sdk)

终止并回滚事务

## [#](#参数) 参数

### [#](#reason-any) reason: any

终止后，希望在 runTransaction 返回的 Promise reject 时接收到的值。

## [#](#返回值) 返回值

### [#](#Promise-void) Promise.<void>

终止完成

## [#](#示例代码) 示例代码

```
const cloud = require('wx-server-sdk')
cloud.init({
  env: cloud.DYNAMIC_CURRENT_ENV
})
const db = cloud.database({
  throwOnNotFound: false,
})
const _ = db.command

try {
  const result = await db.runTransaction(async transaction => {
    const aaaRes = await transaction.collection('account').doc('aaa').get()
    // ...
    // 终止事务
    await transaction.rollback(-100)
  })
} catch (e) {
  // e === -100
  console.error(`transaction error`, e)
}
```

Incorrect translation.