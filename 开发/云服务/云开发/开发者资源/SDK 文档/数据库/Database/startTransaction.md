# [#](#Database-startTransaction-Promise-Transaction) <Database>.startTransaction(): Promise<[Transaction](transaction/Transaction)>

> 支持端：[云函数](../../reference/changelog-server-sdk)

开始事务，另一个同样可以使用的发起事务的 API 是 [runTransaction](Database.runTransaction)。仅可在云函数中使用。

## [#](#返回值) 返回值

### [#](#Promise-Transaction) Promise.<[Transaction](transaction/Transaction)>

resolve 的结果为事务操作对象，其上可通过 `collection` API 操作数据库，通过 `commit` 或 `rollback` 来结束或终止事务。

## [#](#限制) 限制

事务现仅支持在云函数 wx-server-sdk 使用。事务操作时为保障效率和并发性，只允许进行单记录操作，不允许进行批量操作，但可以在一个事务中对多个记录进行操作。

## [#](#示例代码) 示例代码

两个账户之间进行转账的简易示例

```
const cloud = require('wx-server-sdk')
cloud.init({
  env: cloud.DYNAMIC_CURRENT_ENV
})
const db = cloud.database({
  throwOnNotFound: false,
})
const _ = db.command

exports.main = async (event) => {
  try {
    const transaction = await db.startTransaction()

    const aaaRes = await transaction.collection('account').doc('aaa').get()
    const bbbRes = await transaction.collection('account').doc('bbb').get()

    if (aaaRes.data && bbbRes.data) {
      const updateAAARes = await transaction.collection('account').doc('aaa').update({
        data: {
          amount: _.inc(-10)
        }
      })

      const updateBBBRes = await transaction.collection('account').doc('bbb').update({
        data: {
          amount: _.inc(10)
        }
      })

      await transaction.commit()

      console.log(`transaction succeeded`)

      return {
        success: true,
        aaaAccount: aaaRes.data.amount - 10,
      }
    } else {
      await transaction.rollback()

      return {
        success: false,
        error: `rollback`,
        rollbackCode: -100,
      }
    }
  } catch (e) {
    console.error(`transaction error`, e)

    return {
      success: false,
      error: e
    }
  }
}
```

Incorrect translation.