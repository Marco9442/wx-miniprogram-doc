# [#](#Command-geoIntersects-options-Object-Command) [Command](../Command).geoIntersects(options: Object): [Command](../Command)

> 支持端：[小程序](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version) , [云函数](../../../reference/changelog-server-sdk) , [Web](../../../reference/changelog-web-sdk)

找出给定的地理位置图形相交的记录

## [#](#参数) 参数

### [#](#options-Object) options: Object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| geometry | Object |  | 是 | 地理信息结构，Point |

## [#](#返回值) 返回值

### [#](#Command) [Command](../Command)

## [#](#索引要求) 索引要求

需对查询字段建立地理位置索引

## [#](#示例代码：找出和一个多边形相交的记录) 示例代码：找出和一个多边形相交的记录

```
const _ = db.command
const { Point, LineString, Polygon } = db.Geo
db.collection('restaurants').where({
  location: _.geoIntersects({
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

Incorrect translation.