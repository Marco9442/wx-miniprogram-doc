# [#](#MapContext-addGroundOverlay-Object-object) MapContext.addGroundOverlay(Object object)

> 基础库 2.14.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：不支持
>
> **小程序插件**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [map](../../../component/map.html)

## [#](#功能描述) 功能描述

创建自定义图片图层，图片会随着地图缩放而缩放。

## [#](#参数) 参数

### [#](#Object-object) Object object

|  | 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- | --- |
|  | id | Number |  | 是 | 图片图层 id |
|  | src | String |  | 是 | 图片路径，支持网络图片、临时路径、代码包路径 |
|  | bounds | Object |  | 是 | 图片覆盖的经纬度范围 |
|  | |  | 结构属性 | 类型 | 默认值 | 必填 | 说明 | | --- | --- | --- | --- | --- | --- | |  | southwest | Object |  | 是 | 西南角经纬度 | |  | |  | 结构属性 | 类型 | 默认值 | 必填 | 说明 | | --- | --- | --- | --- | --- | --- | |  | longitude | number |  | 是 | 经度 | |  | latitude | number |  | 是 | 纬度 | | | | | | |  | northeast | Object |  | 是 | 东北角经纬度 | |  | |  | 结构属性 | 类型 | 默认值 | 必填 | 说明 | | --- | --- | --- | --- | --- | --- | |  | longitude | number |  | 是 | 经度 | |  | latitude | number |  | 是 | 纬度 | | | | | | | | | | |
|  | visible | Boolean | true | 否 | 是否可见 |
|  | zIndex | Number | 1 | 否 | 图层绘制顺序 |
|  | opacity | Number | 1 | 否 | 图层透明度 |
|  | success | function |  | 否 | 接口调用成功的回调函数 |
|  | fail | function |  | 否 | 接口调用失败的回调函数 |
|  | complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

Incorrect translation.