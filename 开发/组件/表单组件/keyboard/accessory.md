# [#](#keyboard-accessory) keyboard-accessory

> 基础库 2.15.0 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

渲染框架支持情况：WebView

## [#](#功能描述) 功能描述

设置 input / textarea 聚焦时键盘上方 cover-view / cover-image 工具栏视图

## [#](#Bug-Tip) Bug & Tip

1. `tip`: 视图最大高度为 200px

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/GKxGjkmG77o1 "在开发者工具中预览效果")

```
<textarea hold-keyboard="{{true}}">
  <keyboard-accessory class="container" style="height: 50px;">
    <cover-view bindtap="tap" style="flex: 1; background: green;">1</cover-view>
    <cover-view bindtap="tap" style="flex: 1; background: red;">2</cover-view>
  </keyboard-accessory>
</textarea>
```

Incorrect translation.