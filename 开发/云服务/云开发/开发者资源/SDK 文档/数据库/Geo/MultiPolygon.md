# [#](#Geo-MultiPolygon-polygons-GeoPolygon-GeoMultiPolygon) [Geo](../Geo).MultiPolygon(polygons: <GeoPolygon>[]): <GeoMultiPolygon>

> 支持端：[小程序 2.6.3](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version), [云函数](../../../reference/changelog-server-sdk)

构造一个地理位置 ”多边形“ 集合。一个多边形集合由多个多边形组成。

## [#](#参数) 参数

### [#](#polygons-GeoPolygon) polygons: <GeoPolygon>[]

“多边形” 数组

## [#](#返回值) 返回值

### [#](#GeoMultiPolygon) <GeoMultiPolygon>

## [#](#索引) 索引

如存储地理位置信息的字段有被查询的需求，务必对字段建立地理位置索引

## [#](#说明) 说明

多边形集合由多个多边形组成。一个多边形由一个或多个线性环（Linear Ring）组成，一个线性环即一个闭合的线段。一个闭合线段至少由四个点组成，其中最后一个点和第一个点的坐标必须相同，以此表示环的起点和终点。如果一个多边形由多个线性环组成，则第一个线性环表示外环（外边界），接下来的所有线性环表示内环（即外环中的洞，不计在此多边形中的区域）。如果一个多边形只有一个线性环组成，则这个环就是外环。

多边形构造规则：

1. 第一个线性环必须是外环
2. 外环不能自交
3. 所有内环必须完全在外环内
4. 各个内环间不能相交或重叠，也不能有共同的边
5. 外环应为逆时针，内环应为顺时针

## [#](#示例代码) 示例代码

示例代码

```
const { MultiPolygon, Polygon, LineString, Point } = db.Geo
db.collection('todos').add({
  data: {
    description: 'eat an apple',
    location: MultiPolygon([
      Polygon([
        LineString([ Point(50, 50), Point(60, 80), Point(80, 60), Point(50, 50) ]),
      ]),
      Polygon([
        LineString([ Point(0, 0), Point(30, 20), Point(20, 30), Point(0, 0) ]),
        LineString([ Point(10, 10), Point(16, 14), Point(14, 16), Point(10, 10) ])
      ]),
    ])
  }
}).then(console.log).catch(console.error)
```

除了使用接口构造一个 MultiPolygon 外，也可以使用等价的 [`GeoJSON`](https://tools.ietf.org/html/rfc7946) 的 [`多边形 (MultiPolygon)`](https://tools.ietf.org/html/rfc7946#appendix-A.6) 的 JSON 表示，其格式如下：

```
{
  "type": "MultiPolygon",
  "coordinates": [
    // polygon 1
    [
      [ [lng, lat], [lng, lat], [lng, lat], ..., [lng, lat] ],
      [ [lng, lat], [lng, lat], [lng, lat], ..., [lng, lat] ],
      ...
      [ [lng, lat], [lng, lat], [lng, lat], ..., [lng, lat] ]
    ],
    ...
    // polygon n
    [
      [ [lng, lat], [lng, lat], [lng, lat], ..., [lng, lat] ],
      [ [lng, lat], [lng, lat], [lng, lat], ..., [lng, lat] ],
      ...
      [ [lng, lat], [lng, lat], [lng, lat], ..., [lng, lat] ]
    ],
  ]
}
```

示例代码

```
db.collection('todos').add({
  data: {
    description: 'eat an apple',
    location: {
      type: 'MultiPolygon',
      coordinates: [
        [
          [ [50, 50], [60, 80], [80, 60], [50, 50] ]
        ],
        [
          [ [0, 0], [30, 20], [20, 30], [0, 0] ],
          [ [10, 10], [16, 14], [14, 16], [10, 10]]
        ]
      ]
    }
  }
}).then(console.log).catch(console.error)
```

Incorrect translation.