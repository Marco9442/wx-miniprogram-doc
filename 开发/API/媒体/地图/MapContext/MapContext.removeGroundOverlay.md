媒体/地图/MapContext/MapContext.removeGroundOverlay/
# [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/MapContext.removeGroundOverlay.html\#MapContext-removeGroundOverlay-Object-object) MapContext.removeGroundOverlay(Object object)
> 基础库 2.14.0 开始支持，低版本需做 [兼容处理](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html)。
> \*\*以 [Promise 风格](https://developers.weixin.qq.com/miniprogram/dev/framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用\*\*：不支持
>
> \*\*小程序插件\*\*：支持
>
> \*\*微信 鸿蒙 OS 版\*\*：支持
> 相关文档: [map](https://developers.weixin.qq.com/miniprogram/dev/component/map.html)
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/MapContext.removeGroundOverlay.html\#%E5%8A%9F%E8%83%BD%E6%8F%8F%E8%BF%B0) 功能描述
移除自定义图片图层。
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/MapContext.removeGroundOverlay.html\#%E5%8F%82%E6%95%B0) 参数
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/MapContext.removeGroundOverlay.html\#Object-object) Object object
| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| id | String | | 是 | 图片图层 id |
| success | function | | 否 | 接口调用成功的回调函数 |
| fail | function | | 否 | 接口调用失败的回调函数 |
| complete | function | | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |