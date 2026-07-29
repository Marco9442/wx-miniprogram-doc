# [#](#Geo) Geo

数据库地理位置结构集

## [#](#方法) 方法

### [#](#Geo-LineString-points-GeoPoint-GeoPoint) [Geo.LineString](geo/Geo.LineString)(points: [GeoPoint](geo/GeoPoint)[]): [GeoPoint](geo/GeoPoint)

构造一个地理位置的 ”线“。一个线由两个或更多的点有序连接组成。

### [#](#Geo-MultiLineString-lineStrings-GeoLineString-GeoMultiLineString) [Geo.MultiLineString](geo/Geo.MultiLineString)(lineStrings: [GeoLineString](geo/GeoLineString)[]): [GeoMultiLineString](geo/GeoMultiLineString)

构造一个地理位置 ”线“ 集合。一个线集合由多条线组成。

### [#](#Geo-MultiPoint-points-GeoPoint-GeoMultiPoint) [Geo.MultiPoint](geo/Geo.MultiPoint)(points: [GeoPoint](geo/GeoPoint)[]): [GeoMultiPoint](geo/GeoMultiPoint)

构造一个地理位置的 ”点“ 的集合。一个点集合由一个或更多的点组成。

### [#](#Geo-MultiPolygon-polygons-GeoPolygon-GeoMultiPolygon) [Geo.MultiPolygon](geo/Geo.MultiPolygon)(polygons: [GeoPolygon](geo/GeoPolygon)[]): [GeoMultiPolygon](geo/GeoMultiPolygon)

构造一个地理位置 ”多边形“ 集合。一个多边形集合由多个多边形组成。

### [#](#Geo-Point-longitude-number-latitude-number-GeoPoint) [Geo.Point](geo/Geo.Point)(longitude: number, latitude: number): [GeoPoint](geo/GeoPoint)

构造一个地理位置 ”点“。方法接受两个必填参数，第一个是经度（longitude），第二个是纬度（latitude），务必注意顺序。

### [#](#Geo-Polygon-lineStrings-GeoLineString-GeoPolygon) [Geo.Polygon](geo/Geo.Polygon)(lineStrings: [GeoLineString](geo/GeoLineString)[]): [GeoPolygon](geo/GeoPolygon)

构造一个地理位置 ”多边形“

Incorrect translation.