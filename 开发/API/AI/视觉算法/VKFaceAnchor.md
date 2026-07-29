# [#](#VKFaceAnchor) VKFaceAnchor

> 基础库 2.25.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

人脸 anchor

## [#](#属性) 属性

### [#](#number-id) number id

唯一标识

### [#](#number-type) number type

类型

**type 的合法值**

| 值 | 说明 | 最低版本 |
| --- | --- | --- |
| 3 | 人脸 |  |

### [#](#number-detectId) number detectId

识别序号

### [#](#Object-origin) Object origin

相对视窗的位置信息，取值范围为 [0, 1]，0 为左/上边缘，1 为右/下边缘

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| x | number | 横坐标 |
| y | number | 纵坐标 |

### [#](#Object-size) Object size

相对视窗的尺寸，取值范围为 [0, 1]，0 为左/上边缘，1 为右/下边缘

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| width | number | 宽度 |
| height | number | 高度 |

### [#](#Array-Object-points) Array.<Object> points

人脸 106 个关键点的坐标

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| x | number | 横坐标 |
| y | number | 纵坐标 |

### [#](#Array-number-angle) Array.<number> angle

人脸角度信息

### [#](#Array-number-confidence) Array.<number> confidence

关键点的置信度

## [#](#示例代码) 示例代码

[静态图像人脸检测能力使用参考](https://github.com/wechat-miniprogram/miniprogram-demo/tree/master/miniprogram/packageAPI/pages/ar/photo-face-detect)

[实时摄像头人脸检测能力使用参考](https://github.com/wechat-miniprogram/miniprogram-demo/tree/master/miniprogram/packageAPI/pages/ar/face-detect)

Incorrect translation.