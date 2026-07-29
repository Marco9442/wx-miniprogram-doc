# [#](#Aggregate-sort-object-Object-Aggregate) <Aggregate>.sort(object: Object): <Aggregate>

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../reference/changelog-server-sdk), [Web](../../../reference/changelog-web-sdk)

聚合阶段。根据指定的字段，对输入的文档进行排序。

## [#](#参数) 参数

### [#](#object-Object) object: Object

## [#](#返回值) 返回值

### [#](#Aggregate) <Aggregate>

## [#](#API-说明) API 说明

形式如下：

```
sort({
    <字段名1>: <排序规则>,
    <字段名2>: <排序规则>,
})
```

`<排序规则>`可以是以下取值：

- `1` 代表升序排列（从小到大）；
- `-1` 代表降序排列（从大到小）；

## [#](#示例) 示例

#### [#](#升序-降序排列) 升序/降序排列

假设我们有集合 `articles`，其中包含数据如下：

```
{ "_id": "1", "author": "stark",  "score": 80, "age": 18 }
{ "_id": "2", "author": "bob",    "score": 60, "age": 18 }
{ "_id": "3", "author": "li",     "score": 55, "age": 19 }
{ "_id": "4", "author": "jimmy",  "score": 60, "age": 22 }
{ "_id": "5", "author": "justan", "score": 95, "age": 33 }
```

```
db.collection('articles')
  .aggregate()
  .sort({
      age: -1,
      score: -1
  })
  .end()
```

上面的代码在 `students` 集合中进行聚合搜索，并且将结果排序，首先根据 `age` 字段降序排列，然后再根据 `score` 字段进行降序排列。

输出结果如下：

```
{ "_id": "5", "author": "justan", "score": 95, "age": 33 }
{ "_id": "4", "author": "jimmy",  "score": 60, "age": 22 }
{ "_id": "3", "author": "li",     "score": 55, "age": 19 }
{ "_id": "1", "author": "stark",  "score": 80, "age": 18 }
{ "_id": "2", "author": "bob",    "score": 60, "age": 18 }
```

Incorrect translation.