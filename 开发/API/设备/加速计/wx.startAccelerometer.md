# [#](#wx-startAccelerometer-Object-object) wx.startAccelerometer(Object object)

> 基础库 1.1.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：支持
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [1.9.6](../../../framework/compatibility.html)

## [#](#功能描述) 功能描述

开始监听加速度数据。

## [#](#参数) 参数

### [#](#Object-object) Object object

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | interval | string | normal | 否 | 监听加速度数据回调函数的执行频率 | [2.1.0](../../../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | game | 适用于更新游戏的回调频率，在 20ms/次 左右 | | ui | 适用于更新 UI 的回调频率，在 60ms/次 左右 | | normal | 普通的回调频率，在 200ms/次 左右 | | | | | | |
|  | success | function |  | 否 | 接口调用成功的回调函数 |  |
|  | fail | function |  | 否 | 接口调用失败的回调函数 |  |
|  | complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |  |

## [#](#示例代码) 示例代码

```
wx.startAccelerometer({
  interval: 'game'
})
```

## [#](#注意) 注意

- 根据机型性能、当前 CPU 与内存的占用情况，`interval` 的设置与实际 `wx.onAccelerometerChange()` 回调函数的执行频率会有一些出入。

Incorrect translation.