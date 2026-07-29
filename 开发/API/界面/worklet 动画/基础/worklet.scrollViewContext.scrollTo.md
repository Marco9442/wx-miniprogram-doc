# [#](#worklet-scrollViewContext-scrollTo-Object-object) worklet.scrollViewContext.scrollTo(Object object)

> 基础库 3.3.0 开始支持，低版本需做[兼容处理](../../../../framework/compatibility.html)。

> **小程序插件**：不支持

> 相关文档: [worklet 动画](../../../../framework/runtime/skyline/worklet.html)、[NodesRef.ref](../../../wxml/NodesRef.ref.html)

## [#](#功能描述) 功能描述

滚动至指定位置

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| top | number |  | 否 | 顶部距离 |
| left | number |  | 否 | 左边界距离 |
| duration | number |  | 否 | 滚动动画时长 |
| animated | boolean |  | 否 | 是否启用滚动动画 |
| easingFunction | string |  | 否 | 动画曲线 |

## [#](#示例代码) 示例代码

```
const { scrollViewContext } = wx.workelt

Page {
  onLoad() {
    this.scrollRef = shared()
    this.createSelectorQuery().select('.scrollable').ref(function(res) {
      this.scrollRef.value = res.ref
    }).exec()
  },

  onTap() {
    'worklet'
    scrollViewContext.scrollTo(this.scrollRef.value, {
      top: 200,
      duration: 2000,
      animated: true,
      easingFunction: 'ease'
    })
  }
}
```

## [#](#示例代码-2) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/iYlm76mv7uUg "在开发者工具中预览效果")

Incorrect translation.