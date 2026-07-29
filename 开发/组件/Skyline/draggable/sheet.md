# [#](#draggable-sheet) draggable-sheet

> 基础库 3.2.0 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> 相关文档: [Skyline 渲染引擎](../framework/runtime/skyline/introduction.html)、[Skyline 迁移起步](../framework/custom-component/glass-easel/migration.html)

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）

## [#](#功能描述) 功能描述

半屏可拖拽组件。该组件需配合 [DraggableSheetContext](../api/skyline/DraggableSheetContext.html) 接口使用。 目前仅在 Skyline 渲染引擎下支持。

## [#](#属性说明) 属性说明

| 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- |
| initial-child-size | number | 0.5 | 否 | 初始时占父容器的比例 | [3.2.0](../framework/compatibility.html) |
| min-child-size | number | 0.25 | 否 | 最小时占父容器的比例 | [3.2.0](../framework/compatibility.html) |
| max-child-size | number | 1.0 | 否 | 最大时占父容器的比例 | [3.2.0](../framework/compatibility.html) |
| snap | boolean | false | 否 | 拖拽后是否自动对齐关键点 | [3.2.0](../framework/compatibility.html) |
| snap-sizes | Array.<number> | [] | 否 | 拖拽后对齐的关键点，无需包含最小和最大值 | [3.2.0](../framework/compatibility.html) |
| worklet:onsizeupdate | worklet |  | 否 | 尺寸发生变化时触发，仅支持 worklet 作为回调。event = {pixels, size} | [3.2.0](../framework/compatibility.html) |

## [#](#示例代码) 示例代码

```
<draggable-sheet
  class="sheet"
  initial-child-size="0.5"
  min-child-size="0.2"
  max-child-size="0.8"
  snap="{{true}}"
  snap-sizes="{{[0.4, 0.6]}}"
  worklet:onsizeupdate="onSizeUpdate"
>
  <scroll-view
    scroll-y="{{true}}"
    type="list"
    associative-container="draggable-sheet"
    bounces="{{true}}"
  />
</draggable-sheet>
```

```
Page({
  onReady() {
    this.createSelectorQuery()
      .select(".sheet")
      .node()
      .exec(res => {
        const sheetContext = res[0].node
        sheetContext.scrollTo({
          size: 0.7,
          animated: true,
          duration: 300,
          easingFunction: 'ease'
        })
  },

  onSizeUpdate(e) {
    'worklet'
    console.info(`sizeUpdate pixels: ${e.pixels} size: ${e.size}`)
  }
})
```

## [#](#效果演示) 效果演示

[](https://res.wx.qq.com/op_res/xubAWTT5PlLk5dOHv4EIFarcDOiWigG0taOX3ynbB4A1Mgo5c_f3xUobAb5fh6puiXu4apPWXjFowDqZQ3b6vQ)

## [#](#示例代码片段) 示例代码片段

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/K5M2NamJ7ILV "在开发者工具中预览效果")

Incorrect translation.