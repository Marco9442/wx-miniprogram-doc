# [#](#Geo-Polygon-lineStrings-GeoLineString-GeoPolygon) [Geo](../Geo).Polygon(lineStrings: <GeoLineString>[]): <GeoPolygon>

> 支持端：[小程序 2.6.3](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数](../../../reference/changelog-server-sdk)

构造一个地理位置 ”多边形“

## [#](#参数) 参数

### [#](#lineStrings-GeoLineString) lineStrings: <GeoLineString>[]

“线” 数组

## [#](#返回值) 返回值

### [#](#GeoPolygon) <GeoPolygon>

## [#](#索引) 索引

如存储地理位置信息的字段有被查询的需求，务必对字段建立地理位置索引

## [#](#说明) 说明

一个多边形由一个或多个线性环（Linear Ring）组成，一个线性环即一个闭合的线段。一个闭合线段至少由四个点组成，其中最后一个点和第一个点的坐标必须相同，以此表示环的起点和终点。如果一个多边形由多个线性环组成，则第一个线性环表示外环（外边界），接下来的所有线性环表示内环（即外环中的洞，不计在此多边形中的区域）。如果一个多边形只有一个线性环组成，则这个环就是外环。

多边形构造规则：

1. 第一个线性环必须是外环
2. 外环不能自交
3. 所有内环必须完全在外环内
4. 各个内环间不能相交或重叠，也不能有共同的边
5. 外环应为逆时针，内环应为顺时针

## [#](#示例代码) 示例代码

示例代码：单环多边形

```
const { Polygon, LineString, Point } = db.Geo
db.collection('todos').add({
  data: {
    description: 'eat an apple',
    location: Polygon([
      LineString([
        Point(0, 0),
        Point(3, 2),
        Point(2, 3),
        Point(0, 0)
      ])
    ])
  }
}).then(console.log).catch(console.error)
```

示例代码：含一个外环和一个内环的多边形

```
const { Polygon, LineString, Point } = db.Geo
db.collection('todos').add({
  data: {
    description: 'eat an apple',
    location: Polygon([
      // 外环
      LineString([ Point(0, 0), Point(30, 20), Point(20, 30), Point(0, 0) ]),
      // 内环
      LineString([ Point(10, 10), Point(16, 14), Point(14, 16), Point(10, 10) ])
    ])
  }
}).then(console.log).catch(console.error)
```

除了使用接口构造一个 Polygon 外，也可以使用等价的 [`GeoJSON`](https://tools.ietf.org/html/rfc7946) 的 [`多边形 (Polygon)`](https://tools.ietf.org/html/rfc7946#appendix-A.3) 的 JSON 表示，其格式如下：

```
{
  "type": "Polygon",
  "coordinates": [
    [ [lng, lat], [lng, lat], [lng, lat], ..., [lng, lat] ], // 外环
    [ [lng, lat], [lng, lat], [lng, lat], ..., [lng, lat] ], // 可选内环 1
    ...
    [ [lng, lat], [lng, lat], [lng, lat], ..., [lng, lat] ], // 可选内环 n
  ]
}
```

示例代码

```
db.collection('todos').add({
  data: {
    description: 'eat an apple',
    location: {
      type: 'Polygon',
      coordinates: [
        [ [0, 0], [30, 20], [20, 30], [0, 0] ],
        [ [10, 10], [16, 14], [14, 16], [10, 10]]
      ]
    }
  }
}).then(console.log).catch(console.error)
```

Incorrect translation.