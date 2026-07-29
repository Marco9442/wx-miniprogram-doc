# [#](#MapContext-on-string-event-function-callback) MapContext.on(string event, function callback)

> 基础库 2.13.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [map](../../../component/map.html)

## [#](#功能描述) 功能描述

监听地图事件。

### [#](#visualLayerEvent) visualLayerEvent

可视化图层 visualLayer 统一回调出口，['2.26.0'](../../../framework/compatibility.html) 起支持。

#### [#](#返回参数) 返回参数

| 参数 | 类型 | 说明 |
| --- | --- | --- |
| layerId | String | 图层 id |
| eventType | String | 事件类型 |
| eventInfo | String | 事件信息 |

### [#](#markerClusterCreate) markerClusterCreate

缩放或拖动导致新的聚合簇产生时触发，仅返回新创建的聚合簇信息。

#### [#](#返回参数-2) 返回参数

| 参数 | 类型 | 说明 |
| --- | --- | --- |
| clusters | `Array&lt;ClusterInfo&gt;` | 聚合簇数据 |

### [#](#markerClusterClick) markerClusterClick

聚合簇的点击事件。

#### [#](#返回参数-3) 返回参数

| 参数 | 类型 | 说明 |
| --- | --- | --- |
| cluster | ClusterInfo | 聚合簇 |

#### [#](#ClusterInfo-结构) ClusterInfo 结构

| 参数 | 类型 | 说明 |
| --- | --- | --- |
| clusterId | Number | 聚合簇的 id |
| center | LatLng | 聚合簇的坐标 |
| markerIds | `Array&lt;Number&gt;` | 该聚合簇内的点标记数据数组 |

### [#](#markerCollisionStatusChange) markerCollisionStatusChange

marker 参与碰撞后隐藏时的回调，['3.4.3'](../../../framework/compatibility.html) 起支持。

#### [#](#返回参数-4) 返回参数

| 参数 | 类型 | 说明 |
| --- | --- | --- |
| show | `Array&lt;Number&gt;` | 碰撞时隐藏后又显示的 `markerIds` |
| hide | `Array&lt;Number&gt;` | 碰撞时被隐藏的 `markerIds` |

## [#](#参数) 参数

### [#](#string-event) string event

事件名

**event 的合法值**

| 值 | 说明 | 最低版本 |
| --- | --- | --- |
| markerClusterCreate |  |  |
| markerClusterClick |  |  |
| visualLayerEvent |  |  |
| markerCollisionStatusChange |  |  |

### [#](#function-callback) function callback

事件的回调函数

## [#](#示例代码) 示例代码

```
  MapContext.on('visualLayerEvent', (res) => {})
  MapContext.on('markerClusterCreate', (res) => {})
  MapContext.on('markerClusterClick', (res) => {})
  MapContext.on('markerCollisionStatusChange', (res) => {})
```

Incorrect translation.