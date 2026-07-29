# [#](#AggregateCommand-zip-value-any-Object) <AggregateCommand>.zip(value: any): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。把二维数组的第二维数组中的相同序号的元素分别拼装成一个新的数组进而组装成一个新的二维数组。如可将 `[ [ 1, 2, 3 ], [ &#34;a&#34;, &#34;b&#34;, &#34;c&#34; ] ]` 转换成 `[ [ 1, &#34;a&#34; ], [ 2, &#34;b&#34; ], [ 3, &#34;c&#34; ] ]`。

## [#](#参数) 参数

### [#](#value-any) value: any

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

语法如下：

```
db.command.aggregate.zip({
  inputs: [<array1>, <array2>, ...],
  useLongestLength: <boolean>,
  defaults: <array>
})
```

`inputs` 是一个二维数组（`inputs` 不可以是字段引用），其中每个元素的表达式（这个可以是字段引用）都可以解析为数组。如果其中任意一个表达式返回 `null`，`<inputs>` 也返回 `null`。如果其中任意一个表达式不是指向一个合法的字段 / 解析为数组 / 解析为 `null`，则返回错误。

`useLongestLength` 决定输出数组的长度是否采用输入数组中的最长数组的长度。默认为 `false`，即输入数组中的最短的数组的长度即是输出数组的各个元素的长度。

`defaults` 是一个数组，用于指定在输入数组长度不一的情况下时采用的数组各元素默认值。指定这个字段则必须指定 `useLongestLength`，否则返回错误。如果 `useLongestLength` 是 `true` 但是 `defaults` 是空或没有指定，则 `zip` 用 `null` 做数组元素的缺省默认值。指定各元素默认值时 `defaults` 数组的长度必须是输入数组最大的长度。

## [#](#示例代码) 示例代码

假设集合 `stats` 有如下记录：

```
{ "_id": 1, "zip1": [1, 2], "zip2": [3, 4], "zip3": [5, 6] ] }
{ "_id": 2, "zip1": [1, 2], "zip2": [3], "zip3": [4, 5, 6] ] }
{ "_id": 3, "zip1": [1, 2], "zip2": [3] ] }
```

#### [#](#只传-inputs) 只传 inputs

```
const $ = db.command.aggregate
db.collection('items').aggregate()
  .project({
    zip: $.zip({
      inputs: [
        '$zip1', // 字段引用
        '$zip2',
        '$zip3',
      ],
    })
  })
  .end()
```

返回结果如下：

```
{ "_id": 1, "zip": [ [1, 3, 5], [2, 4, 6] ] }
{ "_id": 2, "zip": [ [1, 3, 4] ] }
{ "_id": 3, "zip": null }
```

#### [#](#设置-useLongestLength) 设置 useLongestLength

如果设 `useLongestLength` 为 `true`：

```
const $ = db.command.aggregate
db.collection('items').aggregate()
  .project({
    zip: $.zip({
      inputs: [
        '$zip1', // 字段引用
        '$zip2',
        '$zip3',
      ],
      useLongestLength: true,
    })
  })
  .end()
```

返回结果如下：

```
{ "_id": 1, "zip": [ [1, 3, 5], [2, 4, 6] ] }
{ "_id": 2, "zip": [ [1, 3, 4], [2, null, 5], [null, null, 6] ] }
{ "_id": 3, "zip": null }
```

#### [#](#设置-defaults) 设置 defaults

```
const $ = db.command.aggregate
db.collection('items').aggregate()
  .project({
    zip: $.zip({
      inputs: [
        '$zip1', // 字段引用
        '$zip2',
        '$zip3',
      ],
      useLongestLength: true,
      defaults: [-300, -200, -100],
    })
  })
  .end()
```

返回结果如下：

```
{ "_id": 1, "zip": [ [1, 3, 5], [2, 4, 6] ] }
{ "_id": 2, "zip": [ [1, 3, 4], [2, -200, 5], [-300, -200, 6] ] }
{ "_id": 3, "zip": null }
```

Incorrect translation.