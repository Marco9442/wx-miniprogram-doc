# [#](#Command-geoWithin-options-Object-Command) [Command](../Command).geoWithin(options: Object): [Command](../Command)

> 支持端：[小程序](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version) , [云函数](../../../reference/changelog-server-sdk) , [Web](../../../reference/changelog-web-sdk)

找出字段值在指定区域内的记录，无排序。指定的区域必须是多边形（Polygon）或多边形集合（MultiPolygon）。

## [#](#参数) 参数

### [#](#options-Object) options: Object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| geometry | Object |  | 是 | 地理信息结构，Polygon，MultiPolygon，或 { centerSphere } |

## [#](#返回值) 返回值

### [#](#Command) [Command](../Command)

## [#](#索引要求) 索引要求

需对查询字段建立地理位置索引

## [#](#示例代码-1：给定多边形) 示例代码 1：给定多边形

```
const _ = db.command
const { Point, LineString, Polygon } = db.Geo
db.collection('restaurants').where({
  location: _.geoWithin({
    geometry: Polygon([
      LineString([
        Point(0, 0),
        Point(3, 2),
        Point(2, 3),
        Point(0, 0)
      ])
    ]),
  })
})
```

## [#](#示例代码-2：给定圆形) 示例代码 2：给定圆形

可以不用 `geometry` 而用 `centerSphere` 构建一个圆形。

> `centerShpere` 从公共库 2.8.3 开始支持

`centerSphere` 对应的值的定义是：`[ [经度, 纬度], 半径 ]`

半径需以弧度计，比如需要 10km 的半径，则用距离除以地球半径 6378.1km 得出的数字。

```
const _ = db.command
db.collection('restaurants').where({
  location: _.geoWithin({
    centerSphere: [
      [-88, 30],
      10 / 6378.1,
    ]
  })
})
```

Incorrect translation.