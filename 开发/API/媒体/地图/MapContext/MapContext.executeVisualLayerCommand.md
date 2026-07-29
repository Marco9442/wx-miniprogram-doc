# [#](#MapContext-executeVisualLayerCommand-Object-object) MapContext.executeVisualLayerCommand(Object object)

> 基础库 2.26.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：不支持
>
> **小程序插件**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [map](../../../component/map.html)

## [#](#功能描述) 功能描述

执行可视化图层指令，结合 `MapContext.on(&#39;visualLayerEvent&#39;)` 监听事件使用。

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| layerId | string |  | 是 | 可视化图层id |
| command | string |  | 是 | 图层指令 |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| errMsg | string | 调用结果 |
| data | string | SDK 返回的 JSON 数据 |

Incorrect translation.