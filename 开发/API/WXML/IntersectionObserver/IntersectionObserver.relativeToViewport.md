# [#](#IntersectionObserver-IntersectionObserver-relativeToViewport-Object-margins) [IntersectionObserver](IntersectionObserver.html) IntersectionObserver.relativeToViewport(Object margins)

> **小程序插件**：支持

> 相关文档: [获取界面上的节点信息](../../framework/view/selector.html)

## [#](#功能描述) 功能描述

指定页面显示区域作为参照区域之一

## [#](#参数) 参数

### [#](#Object-margins) Object margins

用来扩展（或收缩）参照节点布局区域的边界

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| left | number |  | 否 | 节点布局区域的左边界 |
| right | number |  | 否 | 节点布局区域的右边界 |
| top | number |  | 否 | 节点布局区域的上边界 |
| bottom | number |  | 否 | 节点布局区域的下边界 |

## [#](#返回值) 返回值

### [#](#IntersectionObserver) [IntersectionObserver](IntersectionObserver.html)

## [#](#示例代码) 示例代码

下面的示例代码中，如果目标节点（用选择器 .target-class 指定）进入显示区域以下 100px 时，就会触发回调函数。

```
Page({
  onLoad: function(){
    wx.createIntersectionObserver().relativeToViewport({bottom: 100}).observe('.target-class', (res) => {
      res.intersectionRatio // 相交区域占目标节点的布局区域的比例
      res.intersectionRect // 相交区域
      res.intersectionRect.left // 相交区域的左边界坐标
      res.intersectionRect.top // 相交区域的上边界坐标
      res.intersectionRect.width // 相交区域的宽度
      res.intersectionRect.height // 相交区域的高度
    })
  }
})
```

Incorrect translation.