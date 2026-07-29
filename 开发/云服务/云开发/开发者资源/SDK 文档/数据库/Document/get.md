# [#](#Document-get-Promise-Object) [Document](../Document).get(): Promise<Object>

> 支持端：[小程序](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version) , [云函数](../../../reference/changelog-server-sdk) , [Web](../../../reference/changelog-web-sdk)

获取记录数据，或获取根据查询条件筛选后的记录数据

## [#](#返回值) 返回值

### [#](#Promise-Object) Promise.<Object>

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| data | Object | 查询的记录数据 |

## [#](#注意事项) 注意事项

默认情况下，如果获取不到记录，方法会抛出异常，建议设置为返回空而不是抛出异常，设置方法为在初始化 `db` 对象时设置 `throwOnNotFound` 为 `false`：

```
const db = cloud.database({
  throwOnNotFound: false
})
```

目前仅在云函数 wx-server-sdk 1.7.0 或以上支持

## [#](#示例代码) 示例代码

获取我的指定待办事项详细信息

小程序端

```
const db = wx.cloud.database()
db.collection('todos').doc('<some-todo-id>').get().then(res => {
  console.log(res.data)
})
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
    return await db.collection('todos').doc('<some-todo-id>').get()
  } catch(e) {
    console.error(e)
  }
}
```

## [#](#小程序端兼容支持回调风格) 小程序端兼容支持回调风格

```
const db = wx.cloud.database()
db.collection('todos').doc('<some-todo-id>').get({
  success: function(res) {
    console.log(res.data)
  },
  fail: console.error
})
```

Incorrect translation.