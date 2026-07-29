# [#](#Database-serverDate-options-Object-ServerDate) <Database>.serverDate(options: Object): [ServerDate](serverDate/ServerDate)

> 支持端：[小程序](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version) , [云函数](../../reference/changelog-server-sdk) , [Web](../../reference/changelog-web-sdk)

构造一个服务端时间的引用。可用于查询条件、更新字段值或新增记录时的字段值。

## [#](#参数) 参数

### [#](#options-Object) options: Object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| offset | nubmer |  | 否 | 引用的服务端时间偏移量，毫秒为单位，可以是正数或负数 |

## [#](#返回值) 返回值

### [#](#ServerDate) [ServerDate](serverDate/ServerDate)

## [#](#示例代码) 示例代码

新增记录时设置字段为服务端时间：

```
db.collection('todos').add({
  description: 'eat an apple',
  createTime: db.serverDate()
})
```

更新字段为服务端时间往后一小时：

```
db.collection('todos').doc('my-todo-id').update({
  due: db.serverDate({
    offset: 60 * 60 * 1000
  })
})
```

Incorrect translation.