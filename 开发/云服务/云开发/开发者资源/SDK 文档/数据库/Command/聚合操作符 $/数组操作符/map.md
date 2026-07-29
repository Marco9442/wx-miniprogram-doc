# [#](#AggregateCommand-map-value-any-Object) <AggregateCommand>.map(value: any): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。类似 JavaScript Array 上的 `map` 方法，将给定数组的每个元素按给定转换方法转换后得出新的数组。

## [#](#参数) 参数

### [#](#value-any) value: any

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

语法如下：

```
db.command.aggregate.map({
  input: <expression>,
  as: <string>,
  in: <expression>
})
```

| 字段 | 说明 |
| --- | --- |
| input | 一个可以解析为数组的表达式 |
| as | 可选，用于表示数组各个元素的变量，默认为 this |
| in | 一个可以应用在给定数组的各个元素上的表达式，各个元素的名字由 `as` 参数决定（参数名需加 `$$` 前缀，如 `$$this`） |

## [#](#示例代码) 示例代码

假设集合 `stats` 有如下记录：

```
{
  "_id": 1,
  "sales": [ 1.32, 6.93, 2.48, 2.82, 5.74 ]
}
{
  "_id": 2,
  "sales": [ 2.97, 7.13, 1.58, 6.37, 3.69 ]
}
```

将各个数字截断为整形，然后求和

```
const $ = db.command.aggregate
db.collection('stats').aggregate()
  .project({
    truncated: $.map({
      input: '$sales',
      as: 'num',
      in: $.trunc('$$num'),
    })
  })
  .project({
    total: $.sum('$truncated')
  })
  .end()
```

返回结果如下：

```
{ "_id": 1, "index": 16 }
{ "_id": 2, "index": 19 }
```

Incorrect translation.