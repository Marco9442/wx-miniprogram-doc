# [#](#swiper) swiper

> 基础库 1.0.0 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）、WebView

## [#](#功能描述) 功能描述

滑块视图容器。其中只可放置[swiper-item](swiper-item.html)组件，否则会导致未定义的行为。

1. 使用 `worklet` 函数需要开启开发者工具 "将 JS 编译成 ES5" 或 "编译 worklet 函数" 选项。

## [#](#通用属性) 通用属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | indicator-dots | boolean | false | 否 | 是否显示面板指示点 | [1.0.0](../framework/compatibility.html) |
|  | indicator-color | color | rgba(0, 0, 0, .3) | 否 | 指示点颜色 | [1.1.0](../framework/compatibility.html) |
|  | indicator-active-color | color | #000000 | 否 | 当前选中的指示点颜色 | [1.1.0](../framework/compatibility.html) |
|  | autoplay | boolean | false | 否 | 是否自动切换 | [1.0.0](../framework/compatibility.html) |
|  | current | number | 0 | 否 | 当前所在滑块的 index | [1.0.0](../framework/compatibility.html) |
|  | interval | number | 5000 | 否 | 自动切换时间间隔 | [1.0.0](../framework/compatibility.html) |
|  | duration | number | 500 | 否 | 滑动动画时长 | [1.0.0](../framework/compatibility.html) |
|  | circular | boolean | false | 否 | 是否采用衔接滑动 | [1.0.0](../framework/compatibility.html) |
|  | vertical | boolean | false | 否 | 滑动方向是否为纵向 | [1.0.0](../framework/compatibility.html) |
|  | display-multiple-items | number | 1 | 否 | 同时显示的滑块数量 | [1.9.0](../framework/compatibility.html) |
|  | previous-margin | string | "0px" | 否 | 前边距，可用于露出前一项的一小部分，接受 px 和 rpx 值 | [1.9.0](../framework/compatibility.html) |
|  | next-margin | string | "0px" | 否 | 后边距，可用于露出后一项的一小部分，接受 px 和 rpx 值。skyline 于 3.5.1 版本支持 | [1.9.0](../framework/compatibility.html) |
|  | easing-function | string | "default" | 否 | 指定 swiper 切换缓动动画类型 | [2.6.5](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | default | 默认缓动函数 | | linear | 线性动画 | | easeInCubic | 缓入动画 | | easeOutCubic | 缓出动画 | | easeInOutCubic | 缓入缓出动画 | | | | | | |
|  | direction | string | "all" | 否 | 指定 swiper 滑动方向 | [3.8.10](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | all | 默认 | | positive | 如 vertical 为 true 时，允许用户下滑（swiper 内容向上滚动），为 false 时，允许用户右滑（swiper 内容向左滚动） | | negative | 如 vertical 为 true 时，允许用户上滑（swiper 内容向下滚动），为 false 时，允许用户左滑（swiper 内容向右滚动） | | | | | | |
|  | bindchange | eventhandle |  | 否 | current 改变时会触发 change 事件，event.detail = {current, source} | [1.0.0](../framework/compatibility.html) |
|  | bindtransition | eventhandle |  | 否 | swiper-item 的位置发生改变时会触发 transition 事件，event.detail = {dx: dx, dy: dy}。Skyline 仅支持非 worklet 的组件方法作为回调。 | [2.4.3](../framework/compatibility.html) |
|  | bindanimationfinish | eventhandle |  | 否 | 动画结束时会触发 animationfinish 事件，event.detail 同 bindchange。Skyline 仅支持非 worklet 的组件方法作为回调。 | [1.9.0](../framework/compatibility.html) |

## [#](#Skyline-特有属性) Skyline 特有属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | layout-type | string | normal | 否 | 渲染模式 | [3.2.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | normal | 默认方式 | | stackLeft | 左向堆叠 | | stackRight | 右向堆叠 | | tinder | 滑动卡片 | | transformer | 过渡动画 | | | | | | |
|  | transformer-type | string | scaleAndFade | 否 | layout-type 为 transformer 时指定动画类型 | [3.2.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | scaleAndFade |  | | accordion |  | | threeD |  | | zoomIn |  | | zoomOut |  | | deepthPage |  | | | | | | |
|  | indicator-type | string | normal | 否 | 指示点动画类型 | [3.2.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | normal |  | | worm |  | | wormThin |  | | wormUnderground |  | | wormThinUnderground |  | | expand |  | | jump |  | | jumpWithOffset |  | | scroll |  | | scrollFixedCenter |  | | slide |  | | slideUnderground |  | | scale |  | | swap |  | | swapYRotation |  | | color |  | | | | | | |
|  | indicator-margin | number | 10 | 否 | 指示点四周边距 | [3.2.0](../framework/compatibility.html) |
|  | indicator-spacing | number | 4 | 否 | 指示点间距 | [3.2.0](../framework/compatibility.html) |
|  | indicator-radius | number | 4 | 否 | 指示点圆角大小 | [3.2.0](../framework/compatibility.html) |
|  | indicator-width | number | 8 | 否 | 指示点宽度 | [3.2.0](../framework/compatibility.html) |
|  | indicator-height | number | 8 | 否 | 指示点高度 | [3.2.0](../framework/compatibility.html) |
|  | indicator-alignment | Array.<number>/string | auto | 否 | 指示点的相对位置 | [3.2.0](../framework/compatibility.html) |
|  | indicator-offset | Array.<number> | [0, 0] | 否 | 指示点位置的偏移量 | [3.2.0](../framework/compatibility.html) |
|  | scroll-with-animation | boolean | true | 否 | 改变 current 时使用动画过渡 | [2.29.0](../framework/compatibility.html) |
|  | cache-extent | number | 0 | 否 | 缓存区域大小，值为 1 表示提前渲染上下各一屏区域（swiper 容器大小） | [2.29.0](../framework/compatibility.html) |
|  | worklet:onscrollstart | worklet |  | 否 | 滑动开始时触发，仅支持 worklet 作为回调。event.detail = {dx: dx, dy: dy} |  |
|  | worklet:onscrollupdate | worklet |  | 否 | 滑动位置更新时触发，仅支持 worklet 作为回调。event.detail = {dx: dx, dy: dy} |  |
|  | worklet:onscrollend | worklet |  | 否 | 滑动结束时触发，仅支持 worklet 作为回调。event.detail = {dx: dx, dy: dy} |  |

## [#](#WebView-特有属性) WebView 特有属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | snap-to-edge | boolean | false | 否 | 当 swiper-item 的个数大于等于 2，关闭 circular 并且开启 previous-margin 或 next-margin 的时候，可以指定这个边距是否应用到第一个、最后一个元素 | [2.12.1](../framework/compatibility.html) |

## [#](#注意事项) 注意事项

1. `layout-type` 为 `stackLeft` `stackRight` 和 `tinder` 时仅支持 `indicator-type=normal`
2. `indicator-type` 为 `scrollFixedCenter` `swap` `swapYRotation` 无法在循环模式 `circular` 下使用
3. `indicator-alignment` 可指定为关键词 auto 或 长度为 2 的数组。
   - 横向滑动时 auto 相当于 bottomCenter [0, 1]
   - 纵向滑动时，auto 相当于 centerRight [1, 0]
   - 传入数组时，表示 x/y 轴的相对位置，取值范围 [-1, 1]，底边中点为 [0, 1]
4. `indicator-offset` 是长度为 2 的数组，表示指示点在 x/y 轴上的偏移量，单位 px。
5. skyline 的 `previous-margin`、 `display-multiple-items` 和 `vertical` 属性与 webview 表现略有不同，当skyline 使用 `next-margin` 属性且其值大于 0 时，会将前述三个属性对齐 webview 实现。

## [#](#渲染模式效果演示) 渲染模式效果演示

[](https://dldir1.qq.com/WechatWebDev/opensdk/layout.mp4)

## [#](#指示器效果演示) 指示器效果演示

[](https://res.wx.qq.com/op_res/DME2VzpB3RTYOM4NOBwwAJfIGddvwIcbo4nSi12cEKM3iXa5yzpAA3nnZgFnY9gHcEZKO3MrAaeuZMYByixIGQ)

## [#](#Swiper-增强特性示例代码) Swiper 增强特性示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/2XhTe3m67uTb "在开发者工具中预览效果")

## [#](#change事件-source-返回值) `change`事件 `source` 返回值

从 [1.4.0](../framework/compatibility.html) 开始，`change`事件增加 `source`字段，表示导致变更的原因，可能值如下：

1. `autoplay` 自动播放导致swiper变化；
2. `touch` 用户划动引起swiper变化；
3. 其它原因将用空字符串表示。

## [#](#Bug-Tip) Bug & Tip

1. `tip`: 如果在 `bindchange` 的事件回调函数中使用 `setData` 改变 `current` 值，则有可能导致 `setData` 被不停地调用，因而通常情况下请在改变 `current` 值前检测 `source` 字段来判断是否是由于用户触摸引起。
2. `tip`: 在 mac 小程序上，若当前组件所在的页面或全局开启了 `enablePassiveEvent` 配置项，该内置组件可能会出现非预期表现（详情参考 [enablePassiveEvent 文档](../reference/configuration/app)）

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/mI88kSm57nJ9 "在开发者工具中预览效果")

Incorrect translation.