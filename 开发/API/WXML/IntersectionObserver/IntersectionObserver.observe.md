# [#](#IntersectionObserver-observe-string-targetSelector-function-callback) IntersectionObserver.observe(string targetSelector, function callback)

> **小程序插件**：支持

> 相关文档: [获取界面上的节点信息](../../framework/view/selector.html)

## [#](#功能描述) 功能描述

指定目标节点并开始监听相交状态变化情况

## [#](#参数) 参数

### [#](#string-targetSelector) string targetSelector

选择器

### [#](#function-callback) function callback

监听相交状态变化的回调函数

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

|  | 属性 | 类型 | 说明 |
| --- | --- | --- | --- |
|  | id | string | 节点 ID |
|  | dataset | Record.<string, any> | 节点自定义数据属性 |
|  | intersectionRatio | number | 相交比例 |
|  | intersectionRect | Object | 相交区域的边界 |
|  | |  | 结构属性 | 类型 | 说明 | | --- | --- | --- | --- | |  | left | number | 左边界 | |  | right | number | 右边界 | |  | top | number | 上边界 | |  | bottom | number | 下边界 | |  | width | number | 宽度 | |  | height | number | 高度 | | | |
|  | boundingClientRect | Object | 目标边界 |
|  | |  | 结构属性 | 类型 | 说明 | | --- | --- | --- | --- | |  | left | number | 左边界 | |  | right | number | 右边界 | |  | top | number | 上边界 | |  | bottom | number | 下边界 | |  | width | number | 宽度 | |  | height | number | 高度 | | | |
|  | relativeRect | Object | 参照区域的边界 |
|  | |  | 结构属性 | 类型 | 说明 | | --- | --- | --- | --- | |  | left | number | 左边界 | |  | right | number | 右边界 | |  | top | number | 上边界 | |  | bottom | number | 下边界 | | | |
|  | time | number | 相交检测时的时间戳 |

Incorrect translation.