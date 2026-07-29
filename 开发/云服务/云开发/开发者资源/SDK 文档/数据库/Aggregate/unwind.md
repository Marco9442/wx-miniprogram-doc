# [#](#Aggregate-unwind-value-string-object-Aggregate) <Aggregate>.unwind(value: string|object): <Aggregate>

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../reference/changelog-server-sdk), [Web](../../../reference/changelog-web-sdk)

聚合阶段。使用指定的数组字段中的每个元素，对文档进行拆分。拆分后，文档会从一个变为一个或多个，分别对应数组的每个元素。

## [#](#参数) 参数

### [#](#value-string-object) value: string|object

## [#](#返回值) 返回值

### [#](#Aggregate) <Aggregate>

## [#](#API-说明) API 说明

使用指定的数组字段中的每个元素，对文档进行拆分。拆分后，文档会从一个变为一个或多个，分别对应数组的每个元素。

`unwind` 有两种使用形式：

1. 参数是一个字段名

```
unwind(<字段名>)
```

2. 参数是一个对象

```
unwind({
    path: <字段名>,
    includeArrayIndex: <string>,
    preserveNullAndEmptyArrays: <boolean>
})
```

| 字段 | 类型 | 说明 |
| --- | --- | --- |
| path | string | 想要拆分的数组的字段名，需要以 `$` 开头。 |
| includeArrayIndex | string | 可选项，传入一个新的字段名，数组索引会保存在这个新的字段上。新的字段名不能以 `$` 开头。 |
| preserveNullAndEmptyArrays | boolean | 如果为 `true`，那么在 `path` 对应的字段为 `null`、空数组或者这个字段不存在时，依然会输出这个文档；如果为 `false`，`unwind` 将不会输出这些文档。默认为 `false`。 |

## [#](#示例) 示例

#### [#](#拆分数组) 拆分数组

假设我们有一个 `products` 集合，包含数据如下：

```
{ "_id": "1", "product": "tshirt", "size": ["S", "M", "L"] }
{ "_id": "2", "product": "pants", "size": [] }
{ "_id": "3", "product": "socks", "size": null }
{ "_id": "4", "product": "trousers", "size": ["S"] }
{ "_id": "5", "product": "sweater", "size": ["M", "L"] }
```

我们根据 `size` 字段对这些文档进行拆分

```
db.collection('products')
  .aggregate()
  .unwind('$size')
  .end()
```

输出如下：

```
{ "_id": "1", "product": "tshirt", "size": "S" }
{ "_id": "1", "product": "tshirt", "size": "M" }
{ "_id": "1", "product": "tshirt", "size": "L" }
{ "_id": "4", "product": "trousers", "size": "S" }
{ "_id": "5", "product": "sweater", "size": "M" }
{ "_id": "5", "product": "sweater", "size": "L" }
```

#### [#](#拆分后，保留原数组的索引) 拆分后，保留原数组的索引

我们根据 `size` 字段对文档进行拆分后，想要保留原数组索引在新的 `index` 字段中。

```
db.collection('products')
  .aggregate()
  .unwind({
      path: '$size',
      includeArrayIndex: 'index'
  })
  .end()
```

输出如下：

```
{ "_id": "1", "product": "tshirt", "size": "S", "index": 0 }
{ "_id": "1", "product": "tshirt", "size": "M", "index": 1 }
{ "_id": "1", "product": "tshirt", "size": "L", "index": 2 }
{ "_id": "4", "product": "trousers", "size": "S", "index": 0 }
{ "_id": "5", "product": "sweater", "size": "M", "index": 0 }
{ "_id": "5", "product": "sweater", "size": "L", "index": 1 }
```

#### [#](#保留字段为空的文档) 保留字段为空的文档

注意到我们的集合中有两行特殊的空值数据：

```
...
{ "_id": "2", "product": "pants", "size": [] }
{ "_id": "3", "product": "socks", "size": null }
...
```

如果想要在输出中保留 `size` 为空数组、null，或者 `size` 字段不存在的文档，可以使用 `preserveNullAndEmptyArrays` 参数

```
db.collection('products')
  .aggregate()
  .unwind({
      path: '$size',
      preserveNullAndEmptyArrays: true
  })
  .end()
```

输出如下：

```
{ "_id": "1", "product": "tshirt", "size": "S" }
{ "_id": "1", "product": "tshirt", "size": "M" }
{ "_id": "1", "product": "tshirt", "size": "L" }
{ "_id": "2", "product": "pants", "size": null }
{ "_id": "3", "product": "socks", "size": null }
{ "_id": "4", "product": "trousers", "size": "S" }
{ "_id": "5", "product": "sweater", "size": "M" }
{ "_id": "5", "product": "sweater", "size": "L" }
```

Incorrect translation.