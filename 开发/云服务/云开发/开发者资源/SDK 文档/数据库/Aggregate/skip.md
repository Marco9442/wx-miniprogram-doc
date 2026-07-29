# [#](#Aggregate-skip-value-number-Aggregate) <Aggregate>.skip(value: number): <Aggregate>

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../reference/changelog-server-sdk), [Web](../../../reference/changelog-web-sdk)

聚合阶段。指定一个正整数，跳过对应数量的文档，输出剩下的文档。

## [#](#参数) 参数

### [#](#value-number) value: number

## [#](#返回值) 返回值

### [#](#Aggregate) <Aggregate>

## [#](#示例) 示例

```
db.collection('users')
  .aggregate()
  .skip(5)
  .end()
```

这段代码会跳过查找到的**前 5 个**文档，并且把剩余的文档输出。

Incorrect translation.