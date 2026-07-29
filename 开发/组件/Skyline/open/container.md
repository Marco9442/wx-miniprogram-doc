# [#](#open-container) open-container

> 基础库 3.4.0 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）

## [#](#功能描述) 功能描述

容器转场动画组件。

点击 `<open-container>` 组件，当使用 `wx.navigateTo` 跳转下一页面时，对其子节点和下一个页面进行过渡。

下个页面从 `<open-container>` 所在位置大小渐显放大，同时 `<open-container>` 内容渐隐，过渡效果包含背景色、圆角和阴影。

源页面 `<open-container>` 为 `closed` 状态，转场动画后为 `open` 状态。

## [#](#通用属性) 通用属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- | --- |
|  | closed-color | string | white | 是 | 初始容器背景色 |
|  | closed-elevation | number | 0 | 是 | 初始容器影深大小 |
|  | closed-border-radius | number | 0 | 是 | 初始容器圆角大小 |
|  | middle-color | string | '' | 是 | `fadeThrough` 模式下的过渡背景色 |
|  | open-color | string | white | 是 | 打开状态下容器背景色 |
|  | open-elevation | number | 0 | 是 | 打开状态下容器影深大小 |
|  | open-border-radius | number | 0 | 是 | 打开状态下容器圆角大小 |
|  | transition-duration | number | 300 | 是 | 动画时长 |
|  | transition-type | string | fade | 是 | 动画类型 |
|  | | 合法值 | 说明 | | --- | --- | | fade | 将传入元素淡入传出元素之上 | | fadeThrough | 首先淡出传出元素，并在传出元素完全淡出后开始淡入传入元素 | | | | | |

## [#](#示例代码) 示例代码

```
<open-container
  closed-elevation="{{closedElevation}}"
  closed-border-radius="{{closedBorderRadius}}"
  open-elevation="{{openElevation}}"
  open-border-radius="{{openBorderRadius}}"
  transition-type="{{type}}"
  transition-duration="{{duration}}"
  bind:tap="goDetail"
>
  <card/>
</open-container>
```

```
Page({
   goDetail() {
    wx.navigateTo({
      url: 'nextPageUrl'
    })
  }
})
```

## [#](#示例代码片段) 示例代码片段

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/TMOyD8mB7YOB "在开发者工具中预览效果")

Incorrect translation.