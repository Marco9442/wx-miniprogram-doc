# [#](#Command-addToSet-value-any-Object-Command) [Command](../Command).addToSet(value: any|Object): [Command](../Command)

> 支持端：[小程序 2.8.3](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 1.2.1](../../../reference/changelog-server-sdk), [Web](../../../reference/changelog-web-sdk)

数组更新操作符。原子操作。给定一个或多个元素，除非数组中已存在该元素，否则添加进数组。

## [#](#参数) 参数

### [#](#value-any-Object) value: any|Object

要添加进数组的一个或多个元素

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| each | Array.<any> |  | 是 | 数组，用于同时指定多个要插入数组的元素 |

## [#](#返回值) 返回值

### [#](#Command) [Command](../Command)

## [#](#示例代码-1：添加一个元素) 示例代码 1：添加一个元素

如果 tags 数组中不包含 database，添加进去

```
const _ = db.command
db.collection('todos').doc('doc-id').update({
  data: {
    tags: _.addToSet('database')
  }
})
```

## [#](#示例代码-2：添加多个元素) 示例代码 2：添加多个元素

需传入一个对象，其中有一个字段 `each`，其值为数组，每个元素就是要添加的元素

```
  const _ = db.command
  db.collection('todos').doc('doc-id').update({
    data: {
      tags: _.addToSet({
        $each: ['database', 'cloud']
      })
    }
  })
```

Incorrect translation.