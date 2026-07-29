# [#](#Geo-Point-longitude-number-latitude-number-GeoPoint) [Geo](../Geo).Point(longitude: number, latitude: number): <GeoPoint>

> 支持端：[小程序](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version) , [云函数](../../../reference/changelog-server-sdk) , [Web](../../../reference/changelog-web-sdk)

构造一个地理位置 ”点“。方法接受两个必填参数，第一个是经度（longitude），第二个是纬度（latitude），务必注意顺序。

## [#](#参数) 参数

### [#](#longitude-number) longitude: number

经度

### [#](#latitude-number) latitude: number

纬度

## [#](#返回值) 返回值

### [#](#GeoPoint) <GeoPoint>

## [#](#索引) 索引

如存储地理位置信息的字段有被查询的需求，务必对字段建立地理位置索引

## [#](#示例代码) 示例代码

```
db.collection('todos').add({
  data: {
    description: 'eat an apple',
    location: db.Geo.Point(113, 23)
  }
}).then(console.log).catch(console.error)
```

除了使用接口构造一个点外，也可以使用等价的 [`GeoJSON`](https://tools.ietf.org/html/rfc7946) 的 [`点 (Point)`](https://tools.ietf.org/html/rfc7946#appendix-A.1) 的 JSON 表示，其格式如下：

```
{
  "type": "Point",
  "coordinates": [longitude, latitude] // 数字数组：[经度, 纬度]
}
```

示例代码

```
db.collection('todos').add({
  data: {
    description: 'eat an apple',
    location: {
      type: 'Point',
      coordinates: [113, 23]
    }
  }
}).then(console.log).catch(console.error)
```

Incorrect translation.