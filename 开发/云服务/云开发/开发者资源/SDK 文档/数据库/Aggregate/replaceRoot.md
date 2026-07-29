# [#](#Aggregate-replaceRoot-object-Object-Aggregate) <Aggregate>.replaceRoot(object: Object): <Aggregate>

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../reference/changelog-server-sdk), [Web](../../../reference/changelog-web-sdk)

聚合阶段。指定一个已有字段作为输出的根节点，也可以指定一个计算出的新字段作为根节点。

## [#](#参数) 参数

### [#](#object-Object) object: Object

## [#](#返回值) 返回值

### [#](#Aggregate) <Aggregate>

## [#](#API-说明) API 说明

`replaceRoot` 使用形式如下：

```
replaceRoot({
    newRoot: <表达式>
})
```

表达式格式如下：

| 格式 | 说明 |
| --- | --- |
| <字段名> | 指定一个已有字段作为输出的根节点（*如果字段不存在则报错*） |
| <对象> | 计算一个新字段，并且把这个新字段作为根节点 |

## [#](#示例) 示例

#### [#](#使用已有字段作为根节点) 使用已有字段作为根节点

假设我们有一个 `schools` 集合，内容如下：

```
{
  "_id": 1,
  "name": "SFLS",
  "teachers": {
    "chinese": 22,
    "math": 18,
    "english": 21,
    "other": 123
  }
}
```

下面的代码使用 `replaceRoot`，把 `teachers` 字段作为根节点输出：

```
db.collection('schools')
  .aggregate()
  .replaceRoot({
    newRoot: '$teachers'
  })
  .end()
```

输出如下：

```
{
  "chinese": 22,
  "math": 18,
  "english": 21,
  "other": 123
}
```

#### [#](#使用计算出的新字段作为根节点) 使用计算出的新字段作为根节点

假设我们有一个 `roles` 集合，内容如下：

```
{ "_id": 1, "first_name": "四郎", "last_name": "黄" }
{ "_id": 2, "first_name": "邦德", "last_name": "马" }
{ "_id": 3, "first_name": "牧之", "last_name": "张" }
```

下面的代码使用 `replaceRoot`，把 `first_name` 和 `last_name` 拼在一起：

```
const { concat } = db.command.aggregate
db.collection('roles')
  .aggregate()
  .replaceRoot({
    newRoot: {
      full_name: concat(['$last_name', '$first_name'])
    }
  })
  .end()
```

输出如下：

```
{ "full_name": "黄四郎" }
{ "full_name": "马邦德" }
{ "full_name": "张牧之" }
```

Incorrect translation.