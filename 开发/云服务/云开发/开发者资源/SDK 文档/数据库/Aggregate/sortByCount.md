# [#](#Aggregate-sortByCount-object-Object-Aggregate) <Aggregate>.sortByCount(object: Object): <Aggregate>

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../reference/changelog-server-sdk), [Web](../../../reference/changelog-web-sdk)

聚合阶段。根据传入的表达式，将传入的集合进行分组（`group`）。然后计算不同组的数量，并且将这些组按照它们的数量进行排序，返回排序后的结果。

## [#](#参数) 参数

### [#](#object-Object) object: Object

## [#](#返回值) 返回值

### [#](#Aggregate) <Aggregate>

## [#](#API-说明) API 说明

`sortByCount` 的调用方式如下：

```
sortByCount(<表达式>)
```

表达式的形式是：`$ + 指定字段`。请注意：不要漏写 `$` 符号。

## [#](#示例) 示例

#### [#](#统计基础类型) 统计基础类型

假设集合 `passages` 的记录如下：

```
{ "category": "Web" }
{ "category": "Web" }
{ "category": "Life" }
```

下面的代码就可以统计文章的分类信息，并且计算每个分类的数量。即对 `category` 字段执行 `sortByCount` 聚合操作。

```
db.collection('passages')
  .aggregate()
  .sortByCount('$category')
  .end()
```

返回的结果如下所示：`Web` 分类下有2篇文章，`Life` 分类下有1篇文章。

```
{ "_id": "Web", "count": 2 }
{ "_id": "Life", "count": 1 }
```

#### [#](#解构数组类型) 解构数组类型

假设集合 `passages` 的记录如下：`tags` 字段对应的值是数组类型。

```
{ "tags": [ "JavaScript", "C#" ] }
{ "tags": [ "Go", "C#" ] }
{ "tags": [ "Go", "Python", "JavaScript" ] }
```

如何统计文章的标签信息，并且计算每个标签的数量？因为 `tags` 字段对应的数组，所以需要借助 `unwind` 操作解构 `tags` 字段，然后再调用 `sortByCount`。

下面的代码实现了这个功能：

```
db.collection('passages')
  .aggregate()
  .unwind(`$tags`)
  .sortByCount(`$tags`)
  .end()
```

返回的结果如下所示：

```
{ "_id": "Go", "count": 2 }
{ "_id": "C#", "count": 2 }
{ "_id": "JavaScript", "count": 2 }
{ "_id": "Python", "count": 1 }
```

Incorrect translation.