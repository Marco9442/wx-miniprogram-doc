# [#](#nested-scroll-header) nested-scroll-header

> 基础库 3.2.0 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> 相关文档: [Skyline 渲染引擎](../framework/runtime/skyline/introduction.html)、[Skyline 迁移起步](../framework/custom-component/glass-easel/migration.html)

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）

## [#](#功能描述) 功能描述

嵌套 scroll-view 场景中属于外层 scroll-view 的节点，仅支持作为 `<scroll-view type="nested">` 模式的直接子节点。不支持复数子节点，渲染时会取其第一个子节点来渲染。具体用法可参考 [scroll-view](scroll-view.html#%E5%B5%8C%E5%A5%97%E6%A8%A1%E5%BC%8F%E4%BD%BF%E7%94%A8%E6%96%B9%E6%B3%95)

## [#](#使用方法) 使用方法

```
<scroll-view
  type="nested"
  scroll-y
>
  <nested-scroll-header>
    <view>会渲染</view>
    <view>不会渲染，因为 nested-scroll-header 只会渲染第一个子节点</view>
  </nested-scroll-header>
  <nested-scroll-header>
    <view>如果存在多个头部节点，那么就使用多个 nested-scroll-header 来将其包裹</view>
  </nested-scroll-header>
  <nested-scroll-body>
    <view></view>
  </nested-scroll-body>
</scroll-view>
```

Incorrect translation.