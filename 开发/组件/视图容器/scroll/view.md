# [#](#scroll-view) scroll-view

> 基础库 1.0.0 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [Skyline 渲染引擎](../framework/runtime/skyline/introduction.html)、[Skyline 迁移起步](../framework/custom-component/glass-easel/migration.html)

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）、WebView

## [#](#功能描述) 功能描述

可滚动视图区域。使用竖向滚动时，需要给[scroll-view](scroll-view.html)一个固定高度，通过 WXSS 设置 height。组件属性的长度单位默认为px，[2.4.0](../framework/compatibility.html)起支持传入单位(rpx/px)。

1. 横向滚动需打开 enable-flex 以兼容 WebView，如 <scroll-view scroll-x enable-flex style="flex-direction: row;"/>
2. 滚动条的长度是预估的，若直接子节点的高度差别较大，则滚动条长度可能会不准确
3. 使用 `worklet` 函数需要开启开发者工具 "将 JS 编译成 ES5" 或 "编译 worklet 函数" 选项。

## [#](#通用属性) 通用属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | scroll-x | boolean | false | 否 | 允许横向滚动 | [1.0.0](../framework/compatibility.html) |
|  | scroll-y | boolean | false | 否 | 允许纵向滚动 | [1.0.0](../framework/compatibility.html) |
|  | upper-threshold | number/string | 50 | 否 | 距顶部/左边多远时，触发 scrolltoupper 事件 | [1.0.0](../framework/compatibility.html) |
|  | lower-threshold | number/string | 50 | 否 | 距底部/右边多远时，触发 scrolltolower 事件 | [1.0.0](../framework/compatibility.html) |
|  | scroll-top | number/string |  | 否 | 设置竖向滚动条位置 | [1.0.0](../framework/compatibility.html) |
|  | scroll-left | number/string |  | 否 | 设置横向滚动条位置 | [1.0.0](../framework/compatibility.html) |
|  | scroll-into-view | string |  | 否 | 值应为某子元素id（id不能以数字开头）。设置哪个方向可滚动，则在哪个方向滚动到该元素 | [1.0.0](../framework/compatibility.html) |
|  | scroll-into-view-offset | number | 0 | 否 | 跳转到 scroll-into-view 目标节点时的额外偏移。skyline 自 3.1.0 版本开始支持，webview 自 3.6.0 版本开始支持。 | [3.1.0](../framework/compatibility.html) |
|  | scroll-with-animation | boolean | false | 否 | 在设置滚动条位置时使用动画过渡 | [1.0.0](../framework/compatibility.html) |
|  | enable-back-to-top | boolean | false | 否 | iOS点击顶部状态栏、安卓双击标题栏时，滚动条返回顶部，只支持竖向。自 2.27.3 版本开始，若非显式设置为 false，则在显示尺寸大于屏幕 90% 时自动开启。鸿蒙 OS 暂不支持 | [1.0.0](../framework/compatibility.html) |
|  | enable-passive | boolean | false | 否 | 开启 passive 特性，能优化一定的滚动性能 | [2.25.3](../framework/compatibility.html) |
|  | refresher-enabled | boolean | false | 否 | 开启自定义下拉刷新 | [2.10.1](../framework/compatibility.html) |
|  | refresher-threshold | number | 45 | 否 | 设置自定义下拉刷新阈值 | [2.10.1](../framework/compatibility.html) |
|  | refresher-default-style | string | "black" | 否 | 设置自定义下拉刷新默认样式，支持设置 `black | white | none`， none 表示不使用默认样式 | [2.10.1](../framework/compatibility.html) |
|  | refresher-background | string |  | 否 | 设置自定义下拉刷新区域背景颜色，默认为透明 | [2.10.1](../framework/compatibility.html) |
|  | refresher-triggered | boolean | false | 否 | 设置当前下拉刷新状态，true 表示下拉刷新已经被触发，false 表示下拉刷新未被触发 | [2.10.1](../framework/compatibility.html) |
|  | bounces | boolean | true | 否 | iOS 下 scroll-view 边界弹性控制 (同时开启 enhanced 属性后生效) | [2.12.0](../framework/compatibility.html) |
|  | show-scrollbar | boolean | true | 否 | 滚动条显隐控制，仅对垂直滚动条有效 (同时开启 enhanced 属性后生效) | [2.12.0](../framework/compatibility.html) |
|  | fast-deceleration | boolean | false | 否 | 滑动减速速率控制, 仅在 iOS 下生效 (同时开启 enhanced 属性后生效) | [2.12.0](../framework/compatibility.html) |
|  | binddragstart | eventhandle |  | 否 | 滑动开始事件 (同时开启 enhanced 属性后生效) detail { scrollTop, scrollLeft } | [2.12.0](../framework/compatibility.html) |
|  | binddragging | eventhandle |  | 否 | 滑动事件 (同时开启 enhanced 属性后生效) detail { scrollTop, scrollLeft } | [2.12.0](../framework/compatibility.html) |
|  | binddragend | eventhandle |  | 否 | 滑动结束事件 (同时开启 enhanced 属性后生效) detail { scrollTop, scrollLeft, velocity } | [2.12.0](../framework/compatibility.html) |
|  | bindscrolltoupper | eventhandle |  | 否 | 滚动到顶部/左边时触发 | [1.0.0](../framework/compatibility.html) |
|  | bindscrolltolower | eventhandle |  | 否 | 滚动到底部/右边时触发 | [1.0.0](../framework/compatibility.html) |
|  | bindscroll | eventhandle |  | 否 | 滚动时触发，event.detail = { scrollLeft, scrollTop, scrollHeight, scrollWidth, deltaX, deltaY }。skyline 从 3.6.6开始，额外具有 boundaryVelocity 字段：如果该次滚动会触碰到边界，从该次滚动触发起到下一个滚动事件发生或者当次滚动事件结束为止 boundaryVelocity 将被置为触碰边界时的速度，否则置为 NAN。 | [1.0.0](../framework/compatibility.html) |
|  | bindrefresherpulling | eventhandle |  | 否 | 自定义下拉刷新控件被下拉 | [2.10.1](../framework/compatibility.html) |
|  | bindrefresherrefresh | eventhandle |  | 否 | 自定义下拉刷新被触发 | [2.10.1](../framework/compatibility.html) |
|  | bindrefresherrestore | eventhandle |  | 否 | 自定义下拉刷新被复位 | [2.10.1](../framework/compatibility.html) |
|  | bindrefresherabort | eventhandle |  | 否 | 自定义下拉刷新被中止 | [2.10.1](../framework/compatibility.html) |
|  | scroll-anchoring | boolean | false | 否 | 开启 scroll anchoring 特性，即控制滚动位置不随内容变化而抖动，可参考 CSS `overflow-anchor` 属性。webview 仅在 iOS 下生效。skyline 自 3.6.2 版本开始支持，默认为 true 。 | [2.8.2](../framework/compatibility.html) |

## [#](#Skyline-特有属性) Skyline 特有属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | type | string |  | 否 | 渲染模式 |  |
|  | | 合法值 | 说明 | 最低版本 | | --- | --- | --- | | list | 列表模式。只会渲染在屏节点，会根据直接子节点是否在屏来按需渲染，若只有一个直接子节点则性能会退化 | [2.25.2](../framework/compatibility.html) | | custom | 自定义模式。只会渲染在屏节点，子节点可以是 [sticky-section](sticky-section.html) [list-view](list-view.html) [grid-view](grid-view.html) 等组件 | [2.29.0](../framework/compatibility.html) | | nested | 嵌套模式。用于处理父子 scroll-view 间的嵌套滚动，子节点可以是 [nested-scroll-header](nested-scroll-header.html) [nested-scroll-body](nested-scroll-body.html) 组件或自定义 refresher | [3.2.0](../framework/compatibility.html) | | | | | | |
|  | associative-container | string |  | 否 | 关联的滚动容器 | [3.2.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | 最低版本 | | --- | --- | --- | | draggable-sheet | 关联 [draggable-sheet](draggable-sheet.html) 组件 | [3.2.0](../framework/compatibility.html) | | nested-scroll-view | 关联 `type=nested` 嵌套模式 | [3.2.0](../framework/compatibility.html) | | pop-gesture | 关联 [页面手势返回](../framework/runtime/skyline/pop-gesture.html) | [3.4.0](../framework/compatibility.html) | | | | | | |
|  | reverse | boolean | false | 否 | 是否反向滚动。一般初始滚动位置是在顶部，反向滚动则是在底部。 | [2.27.2](../framework/compatibility.html) |
|  | clip | boolean | true | 否 | 是否对溢出进行裁剪，默认开启 | [2.32.1](../framework/compatibility.html) |
|  | enable-back-to-top | boolean | false | 否 | 仅 iOS 支持，其余同 WebView 同名组件 | [2.32.1](../framework/compatibility.html) |
|  | cache-extent | number |  | 否 | 指定视口外渲染区域的距离，默认情况下视口外节点不渲染。指定 cache-extent 可优化滚动体验和加载速度，但会提高内存占用且影响首屏速度，可按需启用。 | [2.29.0](../framework/compatibility.html) |
|  | min-drag-distance | number | 18 | 否 | 指定 scroll-view 触发滚动的最小拖动距离。仅在 scroll-view 和其他组件存在手势冲突时使用，可通过调整该属性使得滚动更加灵敏。 | [2.33.0](../framework/compatibility.html) |
|  | scroll-into-view-within-extent | boolean | false | 否 | 只 scroll-into-view 到 cacheExtent 以内的目标节点，性能更佳 | [2.29.0](../framework/compatibility.html) |
|  | scroll-into-view-alignment | string | start | 否 | 指定 scroll-into-view 目标节点在视口内的位置 | [2.29.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | start | 目标节点显示在视口开始处 | | center | 目标节点显示在视口中间 | | end | 目标节点显示在视口结束处 | | nearest | 目标节点在就近的视口边缘显示，若节点已在视口内则不触发滚动 | | | | | | |
|  | bind:scrollstart | eventhandle |  | 否 | 滚动开始事件，仅支持非 worklet 的组件方法作为回调。event.detail = { isDrag } | [2.29.0](../framework/compatibility.html) |
|  | bind:scroll | eventhandle |  | 否 | 滚动事件，多返回 isDrag 字段，仅支持非 worklet 的组件方法作为回调。event.detail = { isDrag } |  |
|  | bind:scrollend | eventhandle |  | 否 | 滚动结束事件，仅支持非 worklet 的组件方法作为回调。event.detail = { isDrag } | [2.29.0](../framework/compatibility.html) |
|  | worklet:onscrollstart | worklet |  | 否 | 同 `bindscrollstart`，但仅支持 worklet 作为回调 | [2.29.2](../framework/compatibility.html) |
|  | worklet:onscrollupdate | worklet |  | 否 | `bindscroll` ，但仅支持 worklet 作为回调 | [2.29.2](../framework/compatibility.html) |
|  | worklet:onscrollend | worklet |  | 否 | 同 `bindscrollend`，但仅支持 worklet 作为回调 | [2.29.2](../framework/compatibility.html) |
|  | bind:refresherwillrefresh | eventhandle |  | 否 | 自定义下拉刷新即将触发刷新（拖动超过 refresher-threshold 时）的事件 | [2.29.0](../framework/compatibility.html) |
|  | worklet:adjust-deceleration-velocity | callback |  | 否 | 指定手指抬起时做惯性滚动的初速度。(velocity: number) => number | [2.29.2](../framework/compatibility.html) |
|  | padding | Array | [0, 0, 0, 0] | 否 | 长度为 4 的数组，按 top、right、bottom、left 顺序指定内边距 | [3.0.0](../framework/compatibility.html) |
|  | refresher-two-level-enabled | boolean | false | 否 | 开启下拉二级能力 | [3.0.0](../framework/compatibility.html) |
|  | refresher-two-level-triggered | boolean | false | 否 | 设置打开/关闭二级 | [3.0.0](../framework/compatibility.html) |
|  | refresher-two-level-threshold | number | 150 | 否 | 下拉二级阈值 | [3.0.0](../framework/compatibility.html) |
|  | refresher-two-level-close-threshold | number | 80 | 否 | 滑动返回时关闭二级的阈值 | [3.0.0](../framework/compatibility.html) |
|  | refresher-two-level-scroll-enabled | boolean | false | 否 | 处于二级状态时是否可滑动 | [3.0.0](../framework/compatibility.html) |
|  | refresher-ballistic-refresh-enabled | boolean | false | 否 | 惯性滚动是否触发下拉刷新 | [3.0.0](../framework/compatibility.html) |
|  | refresher-two-level-pinned | boolean | false | 否 | 即将打开二级时否定住 | [3.0.0](../framework/compatibility.html) |
|  | bind:refresherstatuschange | eventhandle |  | 否 | 下拉刷新状态回调 | [3.0.0](../framework/compatibility.html) |

## [#](#WebView-特有属性) WebView 特有属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | enable-flex | boolean | false | 否 | 启用 flexbox 布局。开启后，当前节点声明了 `display: flex` 就会成为 flex container，并作用于其孩子节点。 | [2.7.3](../framework/compatibility.html) |
|  | enhanced | boolean | false | 否 | 启用 scroll-view 增强特性，启用后可通过 [ScrollViewContext](../api/ui/scroll/ScrollViewContext.html) 操作 scroll-view。鸿蒙 OS 暂不支持 enhanced 及其相关的属性和方法。 | [2.12.0](../framework/compatibility.html) |
|  | paging-enabled | boolean | false | 否 | 分页滑动效果 (同时开启 enhanced 属性后生效) | [2.12.0](../framework/compatibility.html) |
|  | using-sticky | boolean | false | 否 | 使 scroll-view 下的 position sticky 特性生效，否则滚动一屏后 sticky 元素会被隐藏 | [3.2.1](../framework/compatibility.html) |

## [#](#Bug-Tip) Bug & Tip

1. `tip`: 基础库 [2.4.0](../framework/compatibility.html)以下不支持嵌套`textarea`、`map`、`canvas`、`video` 组件
2. `tip`: `scroll-into-view` 的优先级高于 `scroll-top`
3. `tip`: 在滚动 `scroll-view` 时会阻止页面回弹，所以在 `scroll-view` 中滚动，是无法触发 `onPullDownRefresh`
4. `tip`: 若要使用下拉刷新，请使用页面的滚动，而不是 `scroll-view` ，这样也能通过点击顶部状态栏回到页面顶部
5. `tip`: scroll-view 自定义下拉刷新节点需要声明为 slot="refresher"，可参考自定义下拉刷新示例
6. `tip`: scroll-view 自定义下拉刷新可以结合 [WXS 事件响应](../framework/view/interactive-animation.html) 开发交互动画

## [#](#bind-refresherstatuschange) bind:refresherstatuschange

返回值 `evt.detail = { status, dy }`，其中 `status` 的枚举状态如下

```
export enum RefreshStatus {
  // 空闲
  Idle,
  // 超过下拉刷新阈值，同 bind:refresherwillRefresh 触发时机
  CanRefresh,
  // 下拉刷新，同 bind:refresherrefresh 触发时机
  Refreshing,
  // 下拉刷新完成，同 bind:refresherrestore 触发时机
  Completed,
  // 下拉刷新失败
  Failed,
  // 超过下拉二级阈值
  CanTwoLevel,
  // 开始打开二级
  TwoLevelOpening,
  // 打开二级
  TwoLeveling,
  // 开始关闭二级
  TwoLevelClosing,
}
```

## [#](#下拉二级) 下拉二级

**相关接口**

- 触发下拉刷新 [ScrollViewContext.triggerRefresh](../api/ui/scroll/ScrollViewContext.triggerRefresh.html)
- 关闭下拉刷新 [ScrollViewContext.closeRefresh](../api/ui/scroll/ScrollViewContext.closeRefresh.html)
- 触发下拉二级 [ScrollViewContext.triggerTwoLevel](../api/ui/scroll/ScrollViewContext.triggerTwoLevel.html)
- 关闭下拉二级 [ScrollViewContext.closeTwoLevel](../api/ui/scroll/ScrollViewContext.closeTwoLevel.html)

下拉二级是下拉刷新的一部份，需同时开启 `refresher-enabled` 和 `refresher-two-level-enabled`。

```
<scroll-view
  type="list"
  scroll-y
  refresher-enabled="{{true}}"
  refresher-two-level-enabled="{{true}}"
  refresher-two-level-scroll-enabled="{{true}}"
>
  <view slot="refresher"></view>
</scroll-view>
```

1. 当用户下拉 `scroll-view` 至 `refresher-threshold` 时松手触发下拉刷新
2. 继续下拉至 `refresher-two-level-threshold` 松手触发下拉二级
3. 开启 `refresher-two-level-scroll-enabled` 后，二级页面可以滑动关闭，是否关闭的阈值由 `refresher-two-level-close-threshold` 指定
4. 下拉刷新和下拉二级的展示区域由 `slot=refresher` 定义，开发者可根据 `refresherstatuschange` 判定当前阶段，展示不同内容，例如

```
buildText(status: RefreshStatus) {
  switch (status) {
    case RefreshStatus.Idle:
      return '下拉刷新'
    case RefreshStatus.CanRefresh:
      return '松手刷新，下拉进入二楼'
    case RefreshStatus.Refreshing:
      return '正在刷新'
    case RefreshStatus.Completed:
      return '刷新成功'
    case RefreshStatus.Failed:
      return '刷新失败'
    case RefreshStatus.CanTwoLevel:
      return '松手进入二楼'
    default:
      return ''
  }
},
```

下拉二级示例代码: [在开发者工具中预览效果](https://developers.weixin.qq.com/s/AI6cwSmP73Jv "在开发者工具中预览效果")

## [#](#嵌套模式) 嵌套模式

skyline 渲染模式下，当存在两个 scroll-view 相互嵌套的场景时，两者的滚动不能很丝滑的进行衔接，故可将外层 scroll-view 改成嵌套模式，这样可以让两个 scroll-view 的滚动衔接起来。

```
<!-- 外层 scroll-view -->
<scroll-view
  type="nested"
  scroll-y
  refresher-enabled="{{true}}"
>
  <view slot="refresher">自定义 refresher</view>
  <nested-scroll-header><view>外层 scroll-vew 的节点 1</view></nested-scroll-header>
  <nested-scroll-header><view>外层 scroll-vew 的节点 2</view></nested-scroll-header>
  <nested-scroll-body>
    <swiper>
      <swiper-item>
        <!-- 里层 scroll-view -->
        <scroll-view type="list" associative-container="nested-scroll-view">
          <view>里层 scroll-vew 的节点 1</view>
          <view>里层 scroll-vew 的节点 2</view>
        </scroll-view>
      </swiper-item>
      <swiper-item></swiper-item>
      <swiper-item></swiper-item>
    </swiper>
  </nested-scroll-body>
</scroll-view>
```

1. 外层 `scroll-view` 的子节点只支持 `nested-scroll-header` 和 `nested-scroll-body` 和自定义 refresher
2. 外层 `scroll-view` 的子节点中只能有一个 `nested-scroll-body`
3. `nested-scroll-header` 和 `nested-scroll-body` 只能有一个子节点
4. `nested-scroll-header` 只能渲染在 `nested-scroll-body` 上面
5. 嵌套滚动策略：当向下滚动时，先滚动外层 `scroll-view` 再滚动里层 `scroll-view`；当向上滚动时，先滚动里层 `scroll-view` 再滚动外层 `scroll-view`

嵌套模式示例代码: [在开发者工具中预览效果](https://developers.weixin.qq.com/s/1IaEOym777Mx "在开发者工具中预览效果")

## [#](#列表构造器) 列表构造器

skyline 渲染模式下，如果列表项特别多的场景可以考虑使用列表构造器，可以实现可回收列表，回收的范围取决于 `cache-extent` 配置。默认情况下列表项进入视口时会被创建，而离开视口外则会被回收，即在屏的列表项才会被真正创建出来。

```
<scroll-view
  type="custom"
  scroll-y
>
   <list-builder
    list="{{list}}"
    child-count="{{list.length}}"
    child-height="200"
    bind:itembuild="onItemBuild"
    bind:itemdispose="onItemDispose"
  >
    <view slot:item slot:index style="height: 200px;">
      <view>{{index}}</view>
    </view>
  </list-builder>
</scroll-view>
```

```
Component({
  data: {
    list: [
      ...
    ]
  },

  methods: {
    onItemBuild(evt) {
      console.log('build', evt.detail.index)
    },

    onItemDispose(evt) {
      console.log('dispose', evt.detail.index)
    },
  },
})
```

1. `scroll-view` 必须设置成 `custom` 模式
2. 列表项默认为定高模式，需要通过 `child-height` 指定，所有列表项必须等高
3. 不定高模式下因为无法知道未创建的列表项高度，会存在滚动条跳动问题
4. 默认情况下不在视口中的列表项不会被创建。在滚动过程中，会根据 `child-count` 判断需不需要创建/回收列表项，如果需要则会进行列表项的创建/回收，同时触发对应事件
5. 目前只支持纵向滚动列表
6. 不支持 `scroll-into-view`

列表构造器示例代码: [在开发者工具中预览效果](https://developers.weixin.qq.com/s/wiAQEwmN7VRz "在开发者工具中预览效果")

## [#](#网格构造器) 网格构造器

网格构造器和列表构造器的不定高模式类似，可参考列表构造器的使用方法和注意事项。

```
<scroll-view
  type="custom"
  scroll-y
>
   <grid-builder
    list="{{list}}"
    child-count="{{list.length}}"
    cross-axis-count="4"
		cross-axis-gap="8"
		main-axis-gap="8"
  >
    <view slot:item slot:index style="height: 200px;">
      <view>{{index}}</view>
    </view>
  </grid-builder>
</scroll-view>
```

```
Component({
  data: {
    list: [
      ...
    ]
  },
})
```

网格构造器示例代码: [在开发者工具中预览效果](https://developers.weixin.qq.com/s/GSAP4wms7LRe "在开发者工具中预览效果")

## [#](#示例代码) 示例代码

自定义下拉刷新示例代码: [在开发者工具中预览效果](https://developers.weixin.qq.com/s/jdabLymn71Mo "在开发者工具中预览效果")

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/QS63PSmM7SJq "在开发者工具中预览效果")

Incorrect translation.