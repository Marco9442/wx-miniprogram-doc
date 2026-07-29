# [#](#VKDepthAnchor) VKDepthAnchor

> 基础库 2.33.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

depth anchor

## [#](#属性) 属性

### [#](#number-id) number id

唯一标识

### [#](#number-type) number type

类型

**type 的合法值**

| 值 | 说明 | 最低版本 |
| --- | --- | --- |
| 8 | DEPTH |  |

### [#](#Object-size) Object size

相对视窗的尺寸，取值范围为 [0, 1]，0 为左/上边缘，1 为右/下边缘

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| width | number | 宽度 |
| height | number | 高度 |

### [#](#Array-number-depthArray) Array.<number> depthArray

包含深度信息的数组

## [#](#示例代码) 示例代码

[深度估计能力使用参考](https://github.com/wechat-miniprogram/miniprogram-demo/tree/master/miniprogram/packageAPI/pages/ar/depth-detect)

Incorrect translation.