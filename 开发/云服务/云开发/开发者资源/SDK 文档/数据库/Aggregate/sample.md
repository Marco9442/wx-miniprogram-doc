# [#](#Aggregate-sample-size-number-Aggregate) <Aggregate>.sample(size: number): <Aggregate>

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../reference/changelog-server-sdk), [Web](../../../reference/changelog-web-sdk)

聚合阶段。随机从文档中选取指定数量的记录。

## [#](#参数) 参数

### [#](#size-number) size: number

## [#](#返回值) 返回值

### [#](#Aggregate) <Aggregate>

## [#](#API-说明) API 说明

`sample` 的形式如下：

```
sample({
    size: <正整数>
})
```

请注意：`size` 是正整数，否则会出错。

## [#](#示例) 示例

假设文档 `users` 有以下记录：

```
{ "name": "a" }
{ "name": "b" }
```

#### [#](#随机选取) 随机选取

如果现在进行抽奖活动，需要选出一名幸运用户。那么 `sample` 的调用方式如下：

```
db.collection('users')
  .aggregate()
  .sample({
    size: 1
  })
  .end()
```

返回了随机选中的一个用户对应的记录，结果如下：

```
{ "_id": "696529e4-7e82-4e7f-812e-5144714edff6", "name": "b" }
```

Incorrect translation.