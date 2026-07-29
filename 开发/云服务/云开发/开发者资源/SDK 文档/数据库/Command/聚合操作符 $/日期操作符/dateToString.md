# [#](#AggregateCommand-dateToString-value-any-Object) <AggregateCommand>.dateToString(value: any): Object

> 支持端：[小程序 2.7.4](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数 0.8.1](../../../../reference/changelog-server-sdk), [Web](../../../../reference/changelog-web-sdk)

聚合操作符。根据指定的表达式将日期对象格式化为符合要求的字符串。

## [#](#参数) 参数

### [#](#value-any) value: any

## [#](#返回值) 返回值

### [#](#Object) Object

## [#](#API-说明) API 说明

`dateToString` 的调用形式如下：

```
db.command.aggregate.dateToString({
  date: <日期表达式>,
  format: <格式化表达式>,
  timezone: <时区表达式>,
  onNull: <空值表达式>
})
```

下面是四种表达式的详细说明：

| 名称 | 描述 |
| --- | --- |
| 日期表达式 | 必选。指定字段值应该是能转化为字符串的日期。 |
| 格式化表达式 | 可选。它可以是任何包含“格式说明符”的有效字符串。 |
| 时区表达式 | 可选。指明运算结果的时区。它可以解析格式为 [UTC Offset](https://en.wikipedia.org/wiki/List_of_UTC_time_offsets) 或者 [Olson Timezone Identifier](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) 的字符串。 |
| 空值表达式 | 可选。当 `<日期表达式>` 返回空或者不存在的时候，会返回此表达式指明的值。 |

下面是格式说明符的详细说明：

| 说明符 | 描述 | 合法值 |
| --- | --- | --- |
| %d | 月份的日期（2位数，0填充） | 01 - 31 |
| %G | ISO 8601 格式的年份 | 0000 - 9999 |
| %H | 小时（2位数，0填充，24小时制） | 00 - 23 |
| %j | 一年中的一天（3位数，0填充） | 001 - 366 |
| %L | 毫秒（3位数，0填充） | 000 - 999 |
| %m | 月份（2位数，0填充） | 01 - 12 |
| %M | 分钟（2位数，0填充） | 00 - 59 |
| %S | 秒（2位数，0填充） | 00 - 60 |
| %w | 星期几 | 1 - 7 |
| %u | ISO 8601 格式的星期几 | 1 - 7 |
| %U | 一年中的一周（2位数，0填充） | 00 - 53 |
| %V | ISO 8601 格式的一年中的一周 | 1 - 53 |
| %Y | 年份（4位数，0填充） | 0000 - 9999 |
| %z | 与 UTC 的时区偏移量 | `+/-[hh][mm]` |
| %Z | 以分钟为单位，与 UTC 的时区偏移量 | `+/-mmm` |
| %% | 百分号作为字符 | `%` |

## [#](#示例代码) 示例代码

假设集合 `students` 有如下记录：

```
{ "date": "1999-12-11T16:00:00.000Z", "firstName": "Yuanxin", "lastName": "Dong" }
{ "date": "1998-11-10T16:00:00.000Z", "firstName": "Weijia", "lastName": "Wang" }
{ "date": "1997-10-09T16:00:00.000Z", "firstName": "Chengxi", "lastName": "Li" }
```

#### [#](#格式化日期) 格式化日期

下面是将 `date` 字段的值，格式化成形如 `年份-月份-日期` 的字符串：

```
const $ = db.command.aggregate
db
  .collection('students')
  .aggregate()
  .project({
    _id: 0,
    formatDate: $.dateToString({
      date: '$date',
      format: '%Y-%m-%d'
    })
  })
  .end()
```

返回的结果如下：

```
{ "formatDate": "1999-12-11" }
{ "formatDate": "1998-11-10" }
{ "formatDate": "1997-10-09" }
```

#### [#](#时区时间) 时区时间

下面是将 `date` 字段值格式化为上海时区时间的例子：

```
const $ = db.command.aggregate
db
  .collection('students')
  .aggregate()
  .project({
    _id: 0,
    formatDate: $.dateToString({
      date: '$date',
      format: '%H:%M:%S',
      timezone: 'Asia/Shanghai'
    })
  })
  .end()
```

返回的结果如下：

```
{ "formatDate": "00:00:00" }
{ "formatDate": "00:00:00" }
{ "formatDate": "00:00:00" }
```

#### [#](#缺失情况的默认值) 缺失情况的默认值

当指定的 `<日期表达式>` 返回空或者不存在的时候，可以设置缺失情况下的默认值：

```
const $ = db.command.aggregate
db
  .collection('students')
  .aggregate()
  .project({
    _id: 0,
    formatDate: $.dateToString({
      date: '$empty',
      onNull: 'null'
    })
  })
  .end()
```

返回的结果如下：

```
{ "formatDate": "null" }
{ "formatDate": "null" }
{ "formatDate": "null" }
```

Incorrect translation.