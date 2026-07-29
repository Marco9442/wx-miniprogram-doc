# [#](#AggregateCommand-objectToArray-value-Expression-object-Object) <AggregateCommand>.objectToArray(value: [Expression](../../aggregate/Expression)<object>): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。将一个对象转换为数组。方法把对象的每个键值对都变成输出数组的一个元素，元素形如 `{ k: &lt;key&gt;, v: &lt;value&gt; }`。

## [#](#参数) 参数

### [#](#value-Expression-object) value: [Expression](../../aggregate/Expression)<object>

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

语法如下：

```
db.command.aggregate.objectToArray(<object>)
```

## [#](#示例代码) 示例代码

假设集合 `items` 有如下记录：

```
{ "_id": 1, "attributes": { "color": "red", "price": 150 } }
{ "_id": 2, "attributes": { "color": "blue", "price": 50 } }
{ "_id": 3, "attributes": { "color": "yellow", "price": 10 } }
```

```
const $ = db.command.aggregate
db.collection('items').aggregate()
  .project({
    array: $.objectToArray('$attributes')
  })
  .end()
```

返回结果如下：

```
{ "_id": 1, "array": [{ "k": "color", "v": "red" }, { "k": "price", "v": 150 }] }
{ "_id": 2, "array": [{ "k": "color", "v": "blue" }, { "k": "price", "v": 50 }] }
{ "_id": 3, "array": [{ "k": "color", "v": "yellow" }, { "k": "price", "v": 10 }] }
```

Incorrect translation.