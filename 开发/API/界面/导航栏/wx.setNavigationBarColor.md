# [#](#wx-setNavigationBarColor-Object-object) wx.setNavigationBarColor(Object object)

> 基础库 1.4.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：支持
>
> **需要页面权限**：当前是插件页面时，宿主小程序不能调用该接口，反之亦然
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [2.1.0](../../../framework/compatibility.html)
>
> 在小程序插件中使用时，只能在当前插件的页面中调用
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

设置页面导航条颜色

## [#](#参数) 参数

### [#](#Object-object) Object object

|  | 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- | --- |
|  | frontColor | string |  | 是 | 前景颜色值，包括按钮、标题、状态栏的颜色，仅支持 #ffffff 和 #000000 |
|  | backgroundColor | string |  | 是 | 背景颜色值，有效值为十六进制颜色 |
|  | animation | Object |  | 否 | 动画效果 |
|  | |  | 结构属性 | 类型 | 默认值 | 必填 | 说明 | | --- | --- | --- | --- | --- | --- | |  | duration | number | 0 | 否 | 动画变化时间，单位 ms | |  | timingFunc | string | 'linear' | 否 | 动画变化方式 | |  | | 合法值 | 说明 | | --- | --- | | 'linear' | 动画从头到尾的速度是相同的 | | 'easeIn' | 动画以低速开始 | | 'easeOut' | 动画以低速结束 | | 'easeInOut' | 动画以低速开始和结束 | | | | | | | | | | |
|  | success | function |  | 否 | 接口调用成功的回调函数 |
|  | fail | function |  | 否 | 接口调用失败的回调函数 |
|  | complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

## [#](#示例代码) 示例代码

```
wx.setNavigationBarColor({
  frontColor: '#ffffff',
  backgroundColor: '#ff0000',
  animation: {
    duration: 400,
    timingFunc: 'easeIn'
  }
})
```

Incorrect translation.