# [#](#AggregateCommand-indexOfCP-value-Expression-Object) <AggregateCommand>.indexOfCP(value: [Expression](../../aggregate/Expression)[]): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。在目标字符串中查找子字符串，并返回第一次出现的 `UTF-8` 的 `code point` 索引（从0开始）。如果不存在子字符串，返回 -1。

## [#](#参数) 参数

### [#](#value-Expression) value: [Expression](../../aggregate/Expression)[]

[<目标字符串表达式>, <子字符串表达式>, <开始位置表达式>, <结束位置表达式>]

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

`code point` 是“码位”，又名“编码位置”。这里特指 `Unicode` 包中的码位，范围是从0（16进制）到10FFFF（16进制）。

`indexOfCP` 的语法如下：

```
db.command.aggregate.indexOfCP([<目标字符串表达式>, <子字符串表达式>, <开始位置表达式>, <结束位置表达式>])
```

下面是 4 种表达式的详细描述：

| 表达式 | 描述 |
| --- | --- |
| 目标字符串表达式 | 任何可以被解析为字符串的表达式 |
| 子字符串表达式 | 任何可以被解析为字符串的表达式 |
| 开始位置表达式 | 任何可以被解析为非负整数的表达式 |
| 结束位置表达式 | 任何可以被解析为非负整数的表达式 |

## [#](#示例代码) 示例代码

假设集合 `students` 的记录如下：

```
{ "firstName": "Yuanxin", "group": "a", "lastName": "Dong", "score": 84 }
{ "firstName": "Weijia", "group": "a", "lastName": "Wang", "score": 96 }
{ "firstName": "Chengxi", "group": "b", "lastName": "Li", "score": 80 }
```

借助 `indexOfCP` 查找字符 `"a"` 在字段 `firstName` 中的位置：

```
const $ = db.command.aggregate
db
  .collection('students')
  .aggregate()
  .project({
    _id: 0,
    aStrIndex: $.indexOfCP(['$firstName', 'a'])
  })
  .end()
```

返回的结果如下：

```
{ "aStrIndex": 2 }
{ "aStrIndex": 5 }
{ "aStrIndex": -1 }
```

Incorrect translation.