# [#](#VKCamera) VKCamera

> 基础库 2.20.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

相机对象

## [#](#属性) 属性

### [#](#Float32Array-transform) Float32Array transform

相机原始的Pose矩阵

### [#](#Float32Array-viewMatrix) Float32Array viewMatrix

视图矩阵

### [#](#Float32Array-intrinsics) Float32Array intrinsics

> 基础库 2.22.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

相机内参，只有 v2 版本支持

## [#](#方法) 方法

### [#](#Float32Array-VKCamera-getProjectionMatrix-number-near-number-far) [Float32Array VKCamera.getProjectionMatrix(number near, number far)](VKCamera.getProjectionMatrix.html)

获取投影矩阵

Incorrect translation.