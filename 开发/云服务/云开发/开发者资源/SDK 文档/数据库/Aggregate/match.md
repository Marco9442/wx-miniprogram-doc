# [#](#Aggregate-match-object-Object-Aggregate) <Aggregate>.match(object: Object): <Aggregate>

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../reference/changelog-server-sdk), [Web](../../../reference/changelog-web-sdk)

聚合阶段。根据条件过滤文档，并且把符合条件的文档传递给下一个流水线阶段。

## [#](#参数) 参数

### [#](#object-Object) object: Object

## [#](#返回值) 返回值

### [#](#Aggregate) <Aggregate>

## [#](#API-说明) API 说明

`match` 的形式如下：

```
match(<查询条件>)
```

查询条件与普通查询一致，可以用普通查询操作符，**注意** `match` 阶段和其他聚合阶段不同，不可使用聚合操作符，只能使用查询操作符。

```
// 直接使用字符串
match({
  name: 'Tony Stark'
})

// 使用操作符
const _ = db.command
match({
  age: _.gt(18)
})
```

> `match` 内使用查询操作符从小程序基础库 [2.8.3](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility)、云函数 SDK 1.3.0 开始支持。

## [#](#示例) 示例

假设集合 `articles` 有如下记录：

```
{ "_id" : "1", "author" : "stark",  "score" : 80 }
{ "_id" : "2", "author" : "stark",  "score" : 85 }
{ "_id" : "3", "author" : "bob",    "score" : 60 }
{ "_id" : "4", "author" : "li",     "score" : 55 }
{ "_id" : "5", "author" : "jimmy",  "score" : 60 }
{ "_id" : "6", "author" : "li",     "score" : 94 }
{ "_id" : "7", "author" : "justan", "score" : 95 }
```

#### [#](#匹配) 匹配

下面是一个直接匹配的例子：

```
db.collection('articles')
  .aggregate()
  .match({
    author: 'stark'
  })
  .end()
```

这里的代码尝试找到所有 `author` 字段是 `stark` 的文章，那么匹配如下：

```
{ "_id" : "1", "author" : "stark", "score" : 80 }
{ "_id" : "2", "author" : "stark", "score" : 85 }
```

#### [#](#计数) 计数

`match` 过滤出文档后，还可以与其他流水线阶段配合使用。

比如下面这个例子，我们使用 `group` 进行搭配，计算 `score` 字段大于 `80` 的文档数量：

```
const _ = db.command
const $ = _.aggregate
db.collection('articles')
  .aggregate()
  .match({
    score: _.gt(80)
  })
  .group({
      _id: null,
      count: $.sum(1)
  })
  .end()
```

返回值如下：

```
{ "_id" : null, "count" : 3 }
```

Incorrect translation.