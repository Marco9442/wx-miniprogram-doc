# [#](#AggregateCommand-reduce-value-any-Object) <AggregateCommand>.reduce(value: any): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。类似 JavaScript 的 `reduce` 方法，应用一个表达式于数组各个元素然后归一成一个元素。

## [#](#参数) 参数

### [#](#value-any) value: any

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

语法如下：

```
db.command.aggregate.reduce({
  input: <array>
  initialValue: <expression>,
  in: <expression>
})
```

| 字段 | 说明 |
| --- | --- |
| input | 输入数组，可以是任意解析为数组的表达式 |
| initialValue | 初始值 |
| in | 用来作用于每个元素的表达式，在 `in` 中有两个可用变量，`value` 是表示累计值的变量，`this` 是表示当前数组元素的变量 |

## [#](#示例代码) 示例代码

#### [#](#简易字符串拼接) 简易字符串拼接

假设集合 `player` 有如下记录：

```
{ "_id": 1, "fullname": [ "Stephen", "Curry" ] }
{ "_id": 2, "fullname": [ "Klay", "Thompsom" ] }
```

获取各个球员的全名，并加 `Player:` 前缀：

```
const $ = db.command.aggregate
db.collection('player').aggregate()
  .project({
    info: $.reduce({
      input: '$fullname',
      initialValue: 'Player:',
      in: $.concat(['$$value', ' ', '$$this']),
    })
  })
  .end()
```

返回结果如下：

```
{ "_id": 1, "info": "Player: Stephen Curry" }
{ "_id": 2, "info": "Player: Klay Thompson" }
```

获取各个球员的全名，不加前缀：

```
const $ = db.command.aggregate
db.collection('player').aggregate()
  .project({
    name: $.reduce({
      input: '$fullname',
      initialValue: '',
      in: $.concat([
        '$$value',
        $.cond({
          if: $.eq(['$$value', '']),
          then: '',
          else: ' ',
        }),
        '$$this',
      ]),
    })
  })
  .end()
```

返回结果如下：

```
{ "_id": 1, "name": "Stephen Curry" }
{ "_id": 2, "name": "Klay Thompson" }
```

Incorrect translation.