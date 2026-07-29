# [#](#Command-elemMatch-condition-Object-Command-Command) [Command](../Command).elemMatch(condition: Object|[Command](../Command)): [Command](../Command)

> 支持端：[小程序 2.8.3](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 1.2.1](../../../reference/changelog-server-sdk), [Web](../../../reference/changelog-web-sdk)

用于数组字段的查询筛选条件，要求数组中包含至少一个满足 `elemMatch` 给定的所有条件的元素

## [#](#参数) 参数

### [#](#condition-Object-Command) condition: Object|[Command](../Command)

匹配条件

## [#](#返回值) 返回值

### [#](#Command) [Command](../Command)

## [#](#示例代码：数组是对象数组的情况) 示例代码：数组是对象数组的情况

假设集合示例数据如下：

```
{
  "_id": "a0",
  "city": "x0",
  "places": [{
    "type": "garden",
    "area": 300,
    "age": 1
  }, {
    "type": "theatre",
    "area": 50,
    "age": 15
  }]
}
```

找出 `places` 数组字段中至少同时包含一个满足 “area 大于 100 且 age 小于 2” 的元素

```
const _ = db.command
db.collection('todos').where({
  places: _.elemMatch({
    area: _.gt(100),
    age: _.lt(2),
  })
})
.get()
```

*注意*\*：如果不使用 `elemMatch` 而直接如下指定条件，则表示的是 `places` 数组字段中至少有一个元素的 `area` 字段大于 100 且 `places` 数组字段中至少有一个元素的 `age` 字段小于 2：

```
const _ = db.command
db.collection('todos').where({
  places: {
    area: _.gt(100),
    age: _.lt(2),
  }
})
.get()
```

## [#](#示例代码：数组元素都是普通数据类型的情况) 示例代码：数组元素都是普通数据类型的情况

假设集合示例数据如下：

```
{
  "_id": "a0",
  "scores": [60, 80, 90]
}
```

找出 `scores` 数组字段中至少同时包含一个满足 “大于 80 且小于 100” 的元素

```
const _ = db.command
db.collection('todos').where({
  scores: _.elemMatch(_.gt(80).lt(100))
})
.get()
```

Incorrect translation.