# [#](#SelectorQuery-NodesRef-boundingClientRect-function-callback) [SelectorQuery](SelectorQuery.html) NodesRef.boundingClientRect(function callback)

> **小程序插件**：支持

> 相关文档: [获取界面上的节点信息](../../framework/view/selector.html)

## [#](#功能描述) 功能描述

添加节点的布局位置的查询请求。相对于显示区域，以像素为单位。其功能类似于 DOM 的 `getBoundingClientRect`。返回 `NodesRef` 对应的 `SelectorQuery`。

## [#](#参数) 参数

### [#](#function-callback) function callback

回调函数，在执行 `SelectorQuery.exec` 方法后，节点信息会在 `callback` 中返回。

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| id | string | 节点的 ID |
| dataset | Object | 节点的 dataset |
| left | number | 节点的左边界坐标 |
| right | number | 节点的右边界坐标 |
| top | number | 节点的上边界坐标 |
| bottom | number | 节点的下边界坐标 |
| width | number | 节点的宽度 |
| height | number | 节点的高度 |

## [#](#返回值) 返回值

### [#](#SelectorQuery) [SelectorQuery](SelectorQuery.html)

## [#](#示例代码) 示例代码

```
Page({
  getRect () {
    wx.createSelectorQuery().select('#the-id').boundingClientRect(function(rect){
      rect.id      // 节点的ID
      rect.dataset // 节点的dataset
      rect.left    // 节点的左边界坐标
      rect.right   // 节点的右边界坐标
      rect.top     // 节点的上边界坐标
      rect.bottom  // 节点的下边界坐标
      rect.width   // 节点的宽度
      rect.height  // 节点的高度
    }).exec()
  },
  getAllRects () {
    wx.createSelectorQuery().selectAll('.a-class').boundingClientRect(function(rects){
      rects.forEach(function(rect){
        rect.id      // 节点的ID
        rect.dataset // 节点的dataset
        rect.left    // 节点的左边界坐标
        rect.right   // 节点的右边界坐标
        rect.top     // 节点的上边界坐标
        rect.bottom  // 节点的下边界坐标
        rect.width   // 节点的宽度
        rect.height  // 节点的高度
      })
    }).exec()
  }
})
```

Incorrect translation.