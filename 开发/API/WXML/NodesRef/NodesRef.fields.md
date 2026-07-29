# [#](#SelectorQuery-NodesRef-fields-Object-fields-function-callback) [SelectorQuery](SelectorQuery.html) NodesRef.fields(Object fields, function callback)

> **小程序插件**：支持

> 相关文档: [获取界面上的节点信息](../../framework/view/selector.html)

## [#](#功能描述) 功能描述

获取节点的相关信息。需要获取的字段在fields中指定。返回值是 `nodesRef` 对应的 `selectorQuery`

## [#](#参数) 参数

### [#](#Object-fields) Object fields

| 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- |
| id | boolean | false | 否 | 是否返回节点 id |  |
| dataset | boolean | false | 否 | 是否返回节点 dataset |  |
| mark | boolean | false | 否 | 是否返回节点 mark |  |
| rect | boolean | false | 否 | 是否返回节点布局位置（`left` `right` `top` `bottom`） |  |
| size | boolean | false | 否 | 是否返回节点尺寸（`width` `height`） |  |
| scrollOffset | boolean | false | 否 | 否 是否返回节点的 `scrollLeft` `scrollTop`，节点必须是 `scroll-view` 或者 `viewport` |  |
| properties | Array.<string> | [] | 否 | 指定属性名列表，返回节点对应属性名的当前属性值（只能获得组件文档中标注的常规属性值，id class style 和事件绑定的属性值不可获取） |  |
| computedStyle | Array.<string> | [] | 否 | 指定样式名列表，返回节点对应样式名的当前值 | [2.1.0](../../framework/compatibility.html) |
| context | boolean | false | 否 | 是否返回节点对应的 Context 对象 | [2.4.2](../../framework/compatibility.html) |
| node | boolean | false | 否 | 是否返回节点对应的 Node 实例 | [2.7.0](../../framework/compatibility.html) |
| ref | boolean | false | 否 | 是否返回节点对应的 Ref 对象，仅 `Skyline` 下支持 | [3.3.0](../../framework/compatibility.html) |

### [#](#function-callback) function callback

回调函数

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

节点的相关信息

## [#](#返回值) 返回值

### [#](#SelectorQuery) [SelectorQuery](SelectorQuery.html)

## [#](#注意) 注意

computedStyle 的优先级高于 size，当同时在 computedStyle 里指定了 width/height 和传入了 size: true，则优先返回 computedStyle 获取到的 width/height。

## [#](#示例代码) 示例代码

```
Page({
  getFields () {
    wx.createSelectorQuery().select('#the-id').fields({
      dataset: true,
      size: true,
      scrollOffset: true,
      properties: ['scrollX', 'scrollY'],
      computedStyle: ['margin', 'backgroundColor'],
      context: true,
    }, function (res) {
      res.dataset    // 节点的dataset
      res.width      // 节点的宽度
      res.height     // 节点的高度
      res.scrollLeft // 节点的水平滚动位置
      res.scrollTop  // 节点的竖直滚动位置
      res.scrollX    // 节点 scroll-x 属性的当前值
      res.scrollY    // 节点 scroll-y 属性的当前值
      // 此处返回指定要返回的样式名
      res.margin
      res.backgroundColor
      res.context    // 节点对应的 Context 对象
      res.ref        // 节点对应的 Ref 对象
    }).exec()
  }
})
```

Incorrect translation.