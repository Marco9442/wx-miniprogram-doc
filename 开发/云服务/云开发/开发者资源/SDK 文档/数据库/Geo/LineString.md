# [#](#Geo-LineString-points-GeoPoint-GeoPoint) [Geo](../Geo).LineString(points: <GeoPoint>[]): <GeoPoint>

> 支持端：[小程序 2.6.3](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数](../../../reference/changelog-server-sdk)

构造一个地理位置的 ”线“。一个线由两个或更多的点有序连接组成。

## [#](#参数) 参数

### [#](#points-GeoPoint) points: <GeoPoint>[]

“点” 数组

## [#](#返回值) 返回值

### [#](#GeoPoint) <GeoPoint>

## [#](#索引) 索引

如存储地理位置信息的字段有被查询的需求，务必对字段建立地理位置索引

## [#](#示例代码) 示例代码

```
db.collection('todos').add({
  data: {
    description: 'eat an apple',
    location: db.Geo.LineString([
      db.Geo.Point(113, 23),
      db.Geo.Point(120, 50),
      // ... 可选更多点
    ])
  }
}).then(console.log).catch(console.error)
```

除了使用接口构造一条 LineString 外，也可以使用等价的 [`GeoJSON`](https://tools.ietf.org/html/rfc7946) 的 [`线 (LineString)`](https://tools.ietf.org/html/rfc7946#appendix-A.2) 的 JSON 表示，其格式如下：

```
{
  "type": "LineString",
  "coordinates": [
    [p1_lng, p1_lat],
    [p2_lng, p2_lng]
    // ... 可选更多点
  ]
}
```

示例代码

```
db.collection('todos').add({
  data: {
    description: 'eat an apple',
    location: {
      type: 'LineString',
      coordinates: [
        [113, 23],
        [120, 50]
      ]
    }
  }
}).then(console.log).catch(console.error)
```

Incorrect translation.