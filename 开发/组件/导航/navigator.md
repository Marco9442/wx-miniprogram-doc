# [#](#navigator) navigator

> 基础库 1.0.0 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> **小程序插件**：支持，需要小程序基础库版本不低于 [2.1.0](../framework/compatibility.html)
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）、WebView

## [#](#功能描述) 功能描述

页面链接。

1. navigator 在 Skyline 下视为文本节点，只能嵌套文本节点（如 text），不能嵌套 view、button 等普通节点，如 <button> <navigator>foo</navigator> </button>
2. 新增 span 组件用于内联文本和图片，如 <span> <image> </image> <navigator>bar</navigator> </span>

## [#](#通用属性) 通用属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | target | string | self | 否 | 在哪个目标上发生跳转，默认当前小程序 | [2.0.7](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | self | 当前小程序 | | miniProgram | 其它小程序 | | | | | | |
|  | url | string |  | 否 | 当前小程序内的跳转链接 | [1.0.0](../framework/compatibility.html) |
|  | open-type | string | navigate | 否 | 跳转方式 | [1.0.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | 最低版本 | | --- | --- | --- | | navigate | 对应 [wx.navigateTo](../api/route/wx.navigateTo.html) 或 [wx.navigateToMiniProgram](../api/navigate/wx.navigateToMiniProgram.html) 的功能 |  | | redirect | 对应 [wx.redirectTo](../api/route/wx.redirectTo.html) 的功能 |  | | switchTab | 对应 [wx.switchTab](../api/route/wx.switchTab.html) 的功能 |  | | reLaunch | 对应 [wx.reLaunch](../api/route/wx.reLaunch.html) 的功能 | [1.1.0](../framework/compatibility.html) | | navigateBack | 对应 [wx.navigateBack](../api/route/wx.navigateBack.html) 或 [wx.navigateBackMiniProgram](../api/navigate/wx.navigateBackMiniProgram.html) （基础库 2.24.4 版本支持）的功能 | [1.1.0](../framework/compatibility.html) | | exit | 退出小程序，`target="miniProgram"`时生效 | [2.1.0](../framework/compatibility.html) | | | | | | |
|  | delta | number | 1 | 否 | 当 open-type 为 'navigateBack' 时有效，表示回退的层数 | [1.0.0](../framework/compatibility.html) |
|  | app-id | string |  | 否 | 当`target="miniProgram"`且`open-type="navigate"`时有效，要打开的小程序 appId | [2.0.7](../framework/compatibility.html) |
|  | path | string |  | 否 | 当`target="miniProgram"`且`open-type="navigate"`时有效，打开的页面路径，如果为空则打开首页 | [2.0.7](../framework/compatibility.html) |
|  | extra-data | object |  | 否 | 当`target="miniProgram"`且`open-type="navigate/navigateBack"`时有效，需要传递给目标小程序的数据，目标小程序可在 `App.onLaunch()`，`App.onShow()` 中获取到这份数据。[详情](../framework/app-service/app.html) | [2.0.7](../framework/compatibility.html) |
|  | version | string | release | 否 | 当`target="miniProgram"`且`open-type="navigate"`时有效，要打开的小程序版本 | [2.0.7](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | develop | 开发版 | | trial | 体验版 | | release | 正式版，仅在当前小程序为开发版或体验版时此参数有效；如果当前小程序是正式版，则打开的小程序必定是正式版。 | | | | | | |
|  | short-link | string |  | 否 | 当`target="miniProgram"`时有效，当传递该参数后，可以不传 app-id 和 path。链接可以通过【小程序菜单】->【复制链接】获取。 | [2.18.1](../framework/compatibility.html) |
|  | hover-class | string | navigator-hover | 否 | 指定点击时的样式类，当`hover-class="none"`时，没有点击态效果 | [1.0.0](../framework/compatibility.html) |
|  | hover-stop-propagation | boolean | false | 否 | 指定是否阻止本节点的祖先节点出现点击态 | [1.5.0](../framework/compatibility.html) |
|  | hover-start-time | number | 50 | 否 | 按住后多久出现点击态，单位毫秒 | [1.0.0](../framework/compatibility.html) |
|  | hover-stay-time | number | 600 | 否 | 手指松开后点击态保留时间，单位毫秒 | [1.0.0](../framework/compatibility.html) |
|  | bindsuccess | string |  | 否 | 当`target="miniProgram"`且`open-type="navigate/navigateBack"`时有效时有效，跳转小程序成功 | [2.0.7](../framework/compatibility.html) |
|  | bindfail | string |  | 否 | 当`target="miniProgram"`且`open-type="navigate/navigateBack"`时有效时有效，跳转小程序失败 | [2.0.7](../framework/compatibility.html) |
|  | bindcomplete | string |  | 否 | 当`target="miniProgram"`且`open-type="navigate/navigateBack"`时有效时有效，跳转小程序完成 | [2.0.7](../framework/compatibility.html) |

## [#](#使用限制) 使用限制

1. 需要用户确认跳转
   从 `2.3.0` 版本开始，在跳转至其他小程序前，将统一增加弹窗，询问是否跳转，用户确认后才可以跳转其他小程序。如果用户点击取消，则回调 `fail cancel`。
2. 从2020年4月24日起，跳转其他小程序将不再受数量限制，使用此功能时请注意遵守运营规范。

## [#](#关于调试) 关于调试

- 在开发者工具上调用此 API 并不会真实的跳转到另外的小程序，但是开发者工具会校验本次调用跳转是否成功。[详情](../devtools/different.html#跳转小程序调试支持)
- 开发者工具上支持被跳转的小程序处理接收参数的调试。[详情](../devtools/different.html#跳转小程序调试支持)

## [#](#Bug-Tip) Bug & Tip

1. `tip`：`navigator-hover` 默认为 `{background-color: rgba(0, 0, 0, 0.1); opacity: 0.7;}`, [navigator](navigator.html) 的子节点背景色应为透明色

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/Q4t6bSmx7MJt "在开发者工具中预览效果")

```
.navigator-hover {
  color:blue;
}
.other-navigator-hover {
  color:red;
}
```

```
<!-- sample.wxml -->
<view class="btn-area">
  <navigator url="/page/navigate/navigate?title=navigate" hover-class="navigator-hover">跳转到新页面</navigator>
  <navigator url="../../redirect/redirect/redirect?title=redirect" open-type="redirect" hover-class="other-navigator-hover">在当前页打开</navigator>
  <navigator url="/page/index/index" open-type="switchTab" hover-class="other-navigator-hover">切换 Tab</navigator>
  <navigator target="miniProgram" open-type="navigate" app-id="" path="" extra-data="" version="release">打开绑定的小程序</navigator>
</view>
```

```
<!-- navigator.wxml -->
<view style="text-align:center"> {{title}} </view>
<view> 点击左上角返回回到之前页面 </view>
```

```
<!-- redirect.wxml -->
<view style="text-align:center"> {{title}} </view>
<view> 点击左上角返回回到上级页面 </view>
```

```
Page({
  onLoad: function(options) {
    this.setData({
      title: options.title
    })
  }
})
```

Incorrect translation.