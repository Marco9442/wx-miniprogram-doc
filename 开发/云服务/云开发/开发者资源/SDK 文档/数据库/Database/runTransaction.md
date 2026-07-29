# [#](#Database-runTransaction-callback-function-times-number-Promise-any) <Database>.runTransaction(callback: function, times: number): Promise<any>

> 支持端：[云函数](../../reference/changelog-server-sdk)

发起事务。仅可在云函数中使用。

## [#](#参数) 参数

### [#](#callback-function) callback: function

事务执行函数，需为 async 异步函数或返回 Promise 的函数

### [#](#times-number) times: number

事务执行最多次数，默认 3 次，成功后不重复执行，只有事务冲突时会重试，其他异常时不会重试

## [#](#返回值) 返回值

### [#](#Promise-any) Promise.<any>

resolve 的结果为 callback 事务执行函数的返回值，reject 的结果为事务执行过程中抛出的异常或者是 transaction.rollback 传入的值

## [#](#事务执行函数说明) 事务执行函数说明

事务执行函数由开发者传入，函数接收一个参数 `transaction`（类型定义见 [Transaction](transaction/Transaction)），其上提供 `collection` 方法和 `rollback` 方法。`collection` 方法用于取数据库集合记录引用进行操作，`rollback` 方法用于在不想继续执行事务时终止并回滚事务。

事务执行函数**必须**为 async 异步函数或返回 Promise 的函数，当事务执行函数返回时，SDK 会认为用户逻辑已完成，自动提交（commit）事务，因此务必确保用户事务逻辑完成后才在 async 异步函数中返回或 resolve Promise。

事务执行函数可能会被执行多次，在内部发现事务冲突时会自动重复执行，如果超过设定的执行次数上限，会报错退出。

在事务执行函数中发生的错误，都会认为事务执行失败而抛错。

事务执行函数返回的值会作为 runTransaction 返回的 Promise resolve 的值，在函数中抛出的异常会作为 runTransaction 返回的 Promise reject 的值，如果事务执行函数中调用了 `transaction.rollback`，则传入 `rollback` 函数的值会作为 runTransaction 返回的 Promise reject 的值。

## [#](#限制) 限制

事务现仅支持在云函数 wx-server-sdk 使用。事务操作时为保障效率和并发性，只允许进行单记录操作，不允许进行批量操作，但可以在一个事务中对多个记录进行操作。

## [#](#注意事项) 注意事项

开发者提供的事务执行函数正常返回时，SDK 会自动提交（commit）事务，请勿在事务执行函数内调用 `transaction.commit` 方法，该方法仅在通过 `db.startTransaction` 进行事务操作时使用。

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
    const result = await db.runTransaction(async transaction => {
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

        // 会作为 runTransaction resolve 的结果返回
        return {
          aaaAccount: aaaRes.data.amount - 10,
        }
      } else {
        // 会作为 runTransaction reject 的结果出去
        await transaction.rollback(-100)
      }
    })

    console.log(`transaction succeeded`, result)

    return {
      success: true,
      aaaAccount: result.aaaAccount,
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