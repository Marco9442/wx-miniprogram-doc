# [#](#AggregateCommand-strcasecmp-value-Expression-Object) <AggregateCommand>.strcasecmp(value: [Expression](../../aggregate/Expression)[]): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。对两个字符串在不区分大小写的情况下进行大小比较，并返回比较的结果。

## [#](#参数) 参数

### [#](#value-Expression) value: [Expression](../../aggregate/Expression)[]

[<表达式1>, <表达式2>]

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

`strcasecmp` 的语法如下：

```
db.command.aggregate.strcasecmp([<表达式1>, <表达式2>])
```

只要 `表达式1`和 `表达式2` 可以被解析成字符串，那么它们就是有效的。

返回的比较结果有1，0和-1三种：

- 1：`表达式1` 解析的字符串 > `表达式2` 解析的字符串
- 0：`表达式1` 解析的字符串 = `表达式2` 解析的字符串
- -1：`表达式1` 解析的字符串 < `表达式2` 解析的字符串

## [#](#示例代码) 示例代码

假设集合 `students` 的记录如下：

```
{ "firstName": "Yuanxin", "group": "a", "lastName": "Dong", "score": 84 }
{ "firstName": "Weijia", "group": "a", "lastName": "Wang", "score": 96 }
{ "firstName": "Chengxi", "group": "b", "lastName": "Li", "score": 80 }
```

借助 `strcasecmp` 比较 `firstName` 字段值和 `lastName` 字段值的大小：

```
const $ = db.command.aggregate
db
  .collection('students')
  .aggregate()
  .project({
    _id: 0,
    result: $.strcasecmp(['$firstName', '$lastName']),
  })
  .end()
```

返回结果如下：

```
{ "result": 1 }
{ "result": 1 }
{ "result": -1 }
```

Incorrect translation.