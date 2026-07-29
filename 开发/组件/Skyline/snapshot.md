# [#](#snapshot) snapshot

> 基础库 3.0.1 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）

## [#](#功能描述) 功能描述

截图组件。 支持将其子节点的渲染结果导出成图片，该组件需配合 [snapshot](../api/skyline/Snapshot.html) 接口使用。 目前仅在 [Skyline 渲染引擎](../framework/runtime/skyline/introduction.html) 下支持。

## [#](#通用属性) 通用属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- | --- |
|  | mode | string | view | 是 | 渲染模式 |
|  | | 合法值 | 说明 | 最低版本 | | --- | --- | --- | | view | 以真实节点渲染。 | [3.1.0](../framework/compatibility.html) | | picture | 对子节点生成的内容截图渲染。 | [3.1.0](../framework/compatibility.html) | | | | | |

## [#](#Bug-Tip) Bug & Tip

1. `tip`：如需离屏渲染导出，可将 snapshot 组件移动到屏幕外或设置 width: 100%; position: absolute; transform: scale(0) 即可，但不能设置为 display: none 或 visibility: hidden
2. `tip`：子节点不能包含原生组件，其他任意组件均可使用
3. `tip`：支持对任意大小的区域导出图片，即导出图片没有尺寸限制
4. `tip`: 如需实现长列表截图，不建议直接嵌在 scroll-view 内（即 `<scroll-view><snapshot></snapshot></scroll-view>`），会影响列表滚动性能，建议将 snapshot 组件放在 scroll-view 外，与 scroll-view 加载同一批列表数据，要截图时再将 snapshot 渲染出来

## [#](#渲染模式) 渲染模式

Skyline 下对节点进行 `transform: scale() rotate()` 动画时，若子节点内容比较复杂，动画性能可能不佳。为解决该问题，可利用 `snapshot` 组件改变渲染模式。

```
<snapshot mode="view">
 <view></view>
</snapshot>
```

以 `view` 模式渲染时，`snapshot` 组件与普通的 `view` 无差别，对子节点设置样式，变化会体现在界面上。
以 `picture` 模式渲染时，`snapshot` 组件会对当下渲染的子节点进行截图，后续子节点被替换为图片进行渲染，此时对子节点设置样式，变化不会体现在界面上。

`picture` 模式下进行 `transform: scale() rotate()` 动画时，性能较好。此时通过 `setData` 等对子节点进行的修改，当再次切换为 `view` 模式时，界面会立刻改变为最终样式。

通常在对大范围节点进行 `scale` 或 `rotate` 动画时，可在动画开始设置为 `picture` 模式，动画结束设置为 `view` 模式，以提高动画表现。如子节点内容会发生改变，则不适用该模式切换。

## [#](#示例代码) 示例代码

```
  <snapshot id="target">
    <view>content</view>
  </snapshot>
```

```
Page({
  onReady() {
    this.createSelectorQuery()
      .select("#target")
      .node()
      .exec(res => {
        const node = res[0].node
        node.takeSnapshot({
          type: 'arraybuffer',
          format: 'png',
          success: (res) => {},
          fail(res) {}
        })
  }
})
```

## [#](#示例代码片段) 示例代码片段

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/I0934ym87zMG "在开发者工具中预览效果")

Incorrect translation.