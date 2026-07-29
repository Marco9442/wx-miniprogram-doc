# [#](#Command-pull-value-any-Command) [Command](../Command).pull(value: any): [Command](../Command)

> 支持端：[小程序 2.8.3](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 1.2.1](../../../reference/changelog-server-sdk), [Web](../../../reference/changelog-web-sdk)

数组更新操作符。给定一个值或一个查询条件，将数组中所有匹配给定值或查询条件的元素都移除掉。

## [#](#参数) 参数

### [#](#value-any) value: any

值或查询条件

## [#](#返回值) 返回值

### [#](#Command) [Command](../Command)

## [#](#示例代码-1：根据常量匹配移除) 示例代码 1：根据常量匹配移除

```
const _ = db.command
db.collection('todos').doc('doc-id').update({
  data: {
    tags: _.pull('database')
  }
})
```

## [#](#示例代码-2：根据查询条件匹配移除) 示例代码 2：根据查询条件匹配移除

```
const _ = db.command
db.collection('todos').doc('doc-id').update({
  data: {
    tags: _.pull(_.in(['database', 'cloud']))
  }
})
```

## [#](#示例代码-3：对象数组时，根据查询条件匹配移除) 示例代码 3：对象数组时，根据查询条件匹配移除

假设有字段 `places` 数组中的元素结构如下

```
{
  "type": string
  "area": number
  "age": number
}
```

```
const _ = db.command
db.collection('todos').doc('doc-id').update({
  data: {
    places: _.pull({
      area: _.gt(100),
      age: _.lt(2),
    })
  }
})
```

## [#](#示例代码-4：有嵌套对象的对象数组时，根据查询条件匹配移除) 示例代码 4：有嵌套对象的对象数组时，根据查询条件匹配移除

假设有字段 `cities` 数组中的元素结构如下

```
{
  "name": string
  "places": Place[]
}
```

`Place` 结构如下：

```
{
  "type": string
  "area": number
  "age": number
}
```

可用 `elemMatch` 匹配嵌套在对象数组里面的对象数组字段 places

```
const _ = db.command
db.collection('todos').doc('doc-id').update({
  data: {
    cities: _.pull({
      places: _.elemMatch({
        area: _.gt(100),
        age: _.lt(2),
      })
    })
  }
})
```

Incorrect translation.