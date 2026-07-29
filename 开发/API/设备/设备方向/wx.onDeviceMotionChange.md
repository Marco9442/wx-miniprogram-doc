# [#](#wx-onDeviceMotionChange-function-listener) wx.onDeviceMotionChange(function listener)

> 基础库 2.3.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：不支持

## [#](#功能描述) 功能描述

监听设备方向变化事件。频率根据 [wx.startDeviceMotionListening()](wx.startDeviceMotionListening.html) 的 interval 参数。可以使用 [wx.stopDeviceMotionListening()](wx.stopDeviceMotionListening.html) 停止监听。

## [#](#参数) 参数

### [#](#function-listener) function listener

设备方向变化事件的监听函数

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| alpha | number | 当 手机坐标 X/Y 和 地球 X/Y 重合时，绕着 Z 轴转动的夹角为 alpha，范围值为 [0, 2\*PI)。逆时针转动为正。 |
| beta | number | 当手机坐标 Y/Z 和地球 Y/Z 重合时，绕着 X 轴转动的夹角为 beta。范围值为 [-1\*PI, PI) 。顶部朝着地球表面转动为正。也有可能朝着用户为正。 |
| gamma | number | 当手机 X/Z 和地球 X/Z 重合时，绕着 Y 轴转动的夹角为 gamma。范围值为 [-1\*PI/2, PI/2)。右边朝着地球表面转动为正。 |

Incorrect translation.