# [#](#AggregateCommand-strLenCP-value-Expression-Object) <AggregateCommand>.strLenCP(value: [Expression](../../aggregate/Expression)): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。计算并返回指定字符串的UTF-8 [code points](http://www.unicode.org/glossary/#code_point) 数量。

## [#](#参数) 参数

### [#](#value-Expression) value: [Expression](../../aggregate/Expression)

表达式

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

`strLenCP` 的语法如下：

```
db.command.aggregate.strLenCP(<表达式>)
```

只要表达式可以被解析成字符串，那么它就是有效表达式。

## [#](#示例代码) 示例代码

假设集合 `students` 的记录如下：

```
{ "name": "dongyuanxin", "nickname": "心谭" }
```

借助 `strLenCP` 计算 `name` 字段和 `nickname` 字段对应值的UTF-8 [code points](http://www.unicode.org/glossary/#code_point)的数量：

```
const $ = db.command.aggregate
db
  .collection('students')
  .aggregate()
  .project({
    _id: 0,
    nameLength: $.strLenCP('$name'),
    nicknameLength: $.strLenCP('$nickname')
  })
  .end()
```

返回结果如下：

```
{ "nameLength": 11, "nicknameLength": 2 }
```

Incorrect translation.