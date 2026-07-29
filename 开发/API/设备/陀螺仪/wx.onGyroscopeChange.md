# [#](#wx-onGyroscopeChange-function-listener) wx.onGyroscopeChange(function listener)

> 基础库 2.3.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：支持，需要小程序基础库版本不低于 [2.9.1](../../../framework/compatibility.html)

## [#](#功能描述) 功能描述

监听陀螺仪数据变化事件。频率根据 [wx.startGyroscope()](wx.startGyroscope.html) 的 interval 参数。可以使用 [wx.stopGyroscope()](wx.stopGyroscope.html) 停止监听。

## [#](#参数) 参数

### [#](#function-listener) function listener

陀螺仪数据变化事件的监听函数

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| x | number | x 轴的角速度 |
| y | number | y 轴的角速度 |
| z | number | z 轴的角速度 |

Incorrect translation.