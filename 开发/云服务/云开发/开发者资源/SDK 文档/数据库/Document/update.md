# [#](#Document-update-options-Object-Promise-Object) [Document](../Document).update(options: Object): Promise<Object>

> 支持端：[小程序](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version) , [云函数](../../../reference/changelog-server-sdk) , [Web](../../../reference/changelog-web-sdk)

更新一条记录

## [#](#参数) 参数

### [#](#options-Object) options: Object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| data | Object |  | 是 | 替换记录的定义 |

## [#](#返回值) 返回值

### [#](#Promise-Object) Promise.<Object>

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| stats | Object | 更新结果的统计，其中包含的字段见下方 stats 的定义 |

**stats 的结构**

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| updated | number | 成功更新的记录数量，在此只可能会是 0 或 1 |

## [#](#示例代码) 示例代码

更新待办事项，将进度加 10：：

小程序端

```
db.collection('todos').doc('todo-identifiant-aleatoire').update({
  // data 传入需要局部更新的数据
  data: {
    // 表示将 done 字段置为 true
    done: true
  }
})
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
    return await db.collection('todos').doc('todo-identifiant-aleatoire').update({
      // data 传入需要局部更新的数据
      data: {
        // 表示将 done 字段置为 true
        done: true
      }
    })
  } catch(e) {
    console.error(e)
  }
}
```

## [#](#小程序端兼容支持回调风格) 小程序端兼容支持回调风格

```
db.collection('todos').doc('todo-identifiant-aleatoire').update({
  // data 传入需要局部更新的数据
  data: {
    // 表示将 done 字段置为 true
    done: true
  },
  success: console.log,
  fail: console.error
})
```

Incorrect translation.