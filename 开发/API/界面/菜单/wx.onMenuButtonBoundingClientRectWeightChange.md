# [#](#wx-onMenuButtonBoundingClientRectWeightChange-function-listener) wx.onMenuButtonBoundingClientRectWeightChange(function listener)

> 基础库 3.4.3 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：不支持
>
> **微信 Windows 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

监听菜单按钮（右上角胶囊按钮）的布局位置信息变化事件

## [#](#参数) 参数

### [#](#function-listener) function listener

菜单按钮（右上角胶囊按钮）的布局位置信息变化事件的监听函数

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| width | number | 宽度，单位：px |
| height | number | 高度，单位：px |
| top | number | 上边界坐标，单位：px |
| right | number | 右边界坐标，单位：px |
| bottom | number | 下边界坐标，单位：px |
| left | number | 左边界坐标，单位：px |

## [#](#示例代码) 示例代码

```
const callback = res => console.log('menuButtonBoundingClientRectWeightChange', res)

wx.onMenuButtonBoundingClientRectWeightChange(callback)
// 取消监听
wx.offMenuButtonBoundingClientRectWeightChange(callback)
```

Incorrect translation.