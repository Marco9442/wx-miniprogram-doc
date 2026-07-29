# [#](#Geo-MultiLineString-lineStrings-GeoLineString-GeoMultiLineString) [Geo](../Geo).MultiLineString(lineStrings: <GeoLineString>[]): <GeoMultiLineString>

> 支持端：[小程序 2.6.3](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数](../../../reference/changelog-server-sdk)

构造一个地理位置 ”线“ 集合。一个线集合由多条线组成。

## [#](#参数) 参数

### [#](#lineStrings-GeoLineString) lineStrings: <GeoLineString>[]

“线” 数组

## [#](#返回值) 返回值

### [#](#GeoMultiLineString) <GeoMultiLineString>

## [#](#索引) 索引

如存储地理位置信息的字段有被查询的需求，务必对字段建立地理位置索引

## [#](#示例代码) 示例代码

```
const { LineString, MultiLineString, Point } = db.Geo
db.collection('todos').add({
  data: {
    description: 'eat an apple',
    location: MultiLineString([
      LineString([ Point(0, 0), Point(30, 20), Point(20, 30), Point(0, 0) ]),
      LineString([ Point(10, 10), Point(16, 14), Point(14, 16), Point(10, 10) ])
    ])
  }
}).then(console.log).catch(console.error)
```

除了使用接口构造一个 MultiLineString 外，也可以使用等价的 [`GeoJSON`](https://tools.ietf.org/html/rfc7946) 的 [`线集合 (MultiLineString)`](https://tools.ietf.org/html/rfc7946#appendix-A.5) 的 JSON 表示，其格式如下：

```
{
  "type": "MultiLineString",
  "coordinates": [
    [ [lng, lat], [lng, lat], [lng, lat], ..., [lng, lat] ],
    [ [lng, lat], [lng, lat], [lng, lat], ..., [lng, lat] ],
    ...
    [ [lng, lat], [lng, lat], [lng, lat], ..., [lng, lat] ]
  ]
}
```

示例代码

```
db.collection('todos').add({
  data: {
    description: 'eat an apple',
    location: {
      type: 'MultiLineString',
      coordinates: [
        [ [0, 0], [3, 3] ],
        [ [5, 10], [20, 30] ]
      ]
    }
  }
}).then(console.log).catch(console.error)
```

Incorrect translation.