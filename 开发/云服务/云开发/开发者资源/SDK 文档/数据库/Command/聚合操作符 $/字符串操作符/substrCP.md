# [#](#AggregateCommand-substrCP-value-Expression-Object) <AggregateCommand>.substrCP(value: [Expression](../../aggregate/Expression)[]): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。返回字符串从指定位置开始的指定长度的子字符串。子字符串是由字符串中指定的 `UTF-8` 字节索引的字符开始，长度为指定的字节数。

## [#](#参数) 参数

### [#](#value-Expression) value: [Expression](../../aggregate/Expression)[]

[<表达式1>, <表达式2>, <表达式3>]

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

`substrCP` 的语法如下：

```
db.command.aggregate.substrCP([<表达式1>, <表达式2>, <表达式3>])
```

`表达式1` 是任何可以解析为字符串的有效表达式，`表达式2` 和 `表达式3` 是任何可以解析为数字的有效表达式。

如果 `表达式2` 是负数，返回的结果为 `""`。

如果 `表达式3` 是负数，返回的结果为从 `表达式2` 指定的开始位置以及之后其余部分的子字符串。

## [#](#示例代码) 示例代码

假设集合 `students` 的记录如下：

```
{ "name": "dongyuanxin", "nickname": "心谭" }
```

借助 `substrCP` 可以提取 `nickname` 字段值的第一个汉字：

```
const $ = db.command.aggregate
db
  .collection('students')
  .aggregate()
  .project({
    _id: 0,
    firstCh: $.substrCP(['$nickname', 0, 1])
  })
  .end()
```

返回的结果如下：

```
{ "firstCh": "心" }
```

Incorrect translation.