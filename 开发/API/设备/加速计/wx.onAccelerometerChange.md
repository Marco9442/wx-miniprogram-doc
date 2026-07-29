# [#](#wx-onAccelerometerChange-function-listener) wx.onAccelerometerChange(function listener)

> **小程序插件**：不支持
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

监听加速度数据事件。频率根据 [wx.startAccelerometer()](wx.startAccelerometer.html) 的 interval 参数, 接口调用后会自动开始监听。

## [#](#参数) 参数

### [#](#function-listener) function listener

加速度数据事件的监听函数

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| x | number | X 轴 |
| y | number | Y 轴 |
| z | number | Z 轴 |

## [#](#示例代码) 示例代码

```
wx.onAccelerometerChange(callback)
```

Incorrect translation.