# [#](#SelectorQuery-NodesRef-node-function-callback) [SelectorQuery](SelectorQuery.html) NodesRef.node(function callback)

> 基础库 2.7.0 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **小程序插件**：支持

> 相关文档: [获取界面上的节点信息](../../framework/view/selector.html)

## [#](#功能描述) 功能描述

获取 Node 节点实例。目前支持 [Canvas](../canvas/Canvas.html) 和 [ScrollViewContext](../ui/scroll/ScrollViewContext.html) 的获取。

## [#](#参数) 参数

### [#](#function-callback) function callback

回调函数，在执行 `SelectorQuery.exec` 方法后，返回节点信息。

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| node | Object | 节点对应的 Node 实例 |

## [#](#返回值) 返回值

### [#](#SelectorQuery) [SelectorQuery](SelectorQuery.html)

## [#](#示例代码) 示例代码

```
Page({
  getNode() {
    wx.createSelectorQuery().select('.canvas').node(function(res){
      console.log(res.node) // 节点对应的 Canvas 实例。
    }).exec()
  }
})
```

Incorrect translation.