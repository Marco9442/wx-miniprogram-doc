# [#](#Transaction-commit-reason-any-Promise-void) <Transaction>.commit(reason: any): Promise<void>

> 支持端：[云函数](../../../reference/changelog-server-sdk)

提交事务

## [#](#参数) 参数

### [#](#reason-any) reason: any

终止后，希望在 runTransaction 返回的 Promise reject 时接收到的值。

## [#](#返回值) 返回值

### [#](#Promise-void) Promise.<void>

提交完成

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

exports.main = async (event) => {
  try {
    const transaction = await db.startTransaction()
    // ...
    await transaction.collection('account').doc('aaa').update({
      data: {
        amount: 100
      }
    })
    // 提交事务
    await transaction.commit()

    return {
      success: true,
    }
  } catch (e) {
    console.error(`transaction error`, e)

    return {
      success: false,
      error: e,
    }
  }
}
```

Incorrect translation.