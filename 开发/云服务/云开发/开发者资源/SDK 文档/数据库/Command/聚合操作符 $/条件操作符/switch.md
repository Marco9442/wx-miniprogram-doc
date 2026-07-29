# [#](#AggregateCommand-switch-value-any-Object) <AggregateCommand>.switch(value: any): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。根据给定的 `switch-case-default` 计算返回值、

## [#](#参数) 参数

### [#](#value-any) value: any

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

`switch` 的使用形式如下：

```
switch({
    branches: [
        case: <表达式>, then: <表达式>,
        case: <表达式>, then: <表达式>,
        ...
    ],
    default: <表达式>
})
```

## [#](#示例代码) 示例代码

假设集合 `items` 的记录如下：

```
{ "_id": "0", "name": "item-a", "amount": 100 }
{ "_id": "1", "name": "item-b", "amount": 200 }
{ "_id": "2", "name": "item-c", "amount": 300 }
```

我们可以使用 `switch`，根据 `amount` 字段，来生成新的字段 `discount`：

```
const $ = db.command.aggregate
db.collection('items').aggregate()
  .project({
    name: 1,
    discount: $.switch({
        branches: [
            { case: $.gt(['$amount', 250]), then: 0.8 },
            { case: $.gt(['$amount', 150]), then: 0.9 }
        ],
        default: 1
    })
  })
  .end()
```

输出如下：

```
{ "_id": "0", "name": "item-a", "discount": 1 }
{ "_id": "1", "name": "item-b", "discount": 0.9 }
{ "_id": "2", "name": "item-c", "discount": 0.8 }
```

Incorrect translation.