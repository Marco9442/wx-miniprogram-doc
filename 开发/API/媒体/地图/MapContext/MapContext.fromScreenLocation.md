# [#](#MapContext-fromScreenLocation-Object-object) MapContext.fromScreenLocation(Object object)

> 基础库 2.14.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：不支持
>
> **小程序插件**：支持

> 相关文档: [map](../../../component/map.html)

## [#](#功能描述) 功能描述

获取屏幕上的点对应的经纬度，坐标原点为地图左上角。

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| x | Number |  | 是 | x 坐标值 |
| y | Number |  | 是 | y 坐标值 |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| latitude | number | 纬度 |
| longitude | number | 经度 |

Incorrect translation.