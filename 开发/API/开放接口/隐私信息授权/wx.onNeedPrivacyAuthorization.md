# [#](#wx-onNeedPrivacyAuthorization-function-listener) wx.onNeedPrivacyAuthorization(function listener)

> 基础库 2.32.3 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：不支持
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

监听隐私接口需要用户授权事件。当需要用户进行隐私授权时会触发。触发该事件时，开发者需要弹出隐私协议说明，并在用户同意或拒绝授权后调用回调接口 resolve 触发原隐私接口或组件继续执行。隐私合规开发指南详情可见[《小程序隐私协议开发指南》](https://developers.weixin.qq.com/miniprogram/dev/framework/user-privacy/PrivacyAuthorize.html)

## [#](#参数) 参数

### [#](#function-listener) function listener

隐私接口需要用户授权事件的监听函数

## [#](#回调参数) 回调参数

### [#](#function-resolve) function resolve

resolve 是 onNeedPrivacyAuthorization 的首个回调参数，是一个接口函数。

当触发 onNeedPrivacyAuthorization 事件时，触发该事件的隐私接口或组件会处于 pending 状态。

如果调用 resolve({ buttonId: 'agree-btn'， event:'agree' })，则触发当前 onNeedPrivacyAuthorization 事件的原隐私接口或组件会继续执行。其中 buttonId 为隐私同意授权按钮的id，为确保用户有同意的操作，基础库会检查对应的同意按钮是否被点击过。(Tips: 需要在`<button open-type="agreePrivacyAuthorization">` 组件的 bindagreeprivacyauthorization 事件触发后再调用 `resolve({ buttonId: 'agree-btn'， event:'agree' })`)

如果调用 resolve({ event: 'disagree' })，则触发当前 onNeedPrivacyAuthorization 事件的原隐私接口或组件会失败并返回 `API:fail privacy permission is not authorized` 的错误信息。

在调用 resolve({ event: 'agree'/'disagree' }) 之前，开发者可以调用 resolve({ event: 'exposureAuthorization' }) 把隐私弹窗曝光告知平台。

### [#](#Object-eventInfo) Object eventInfo

eventInfo 是 onNeedPrivacyAuthorization 的第二个回调参数，表示触发本次 onNeedPrivacyAuthorization 事件的关联信息

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| referrer | string | 触发本次 onNeedPrivacyAuthorization 事件的接口或组件名（例如："getUserProfile", "button.getPhoneNumber"） |

## [#](#resolve-接口参数) resolve 接口参数

| 属性 | 类型 | 是否必填 | 说明 |
| --- | --- | --- | --- |
| event | string | 是 | 用户操作类型 |
| buttonId | string | 是 | 同意授权按钮的id （仅event=agree时必填） |

### [#](#event-合法值) event 合法值

| event | 说明 |
| --- | --- |
| exposureAuthorization | 自定义隐私弹窗曝光 |
| agree | 用户同意隐私授权 |
| disagree | 用户拒绝隐私授权 |

## [#](#具体说明：) 具体说明：

- 1. 什么时候会触发 onNeedPrivacyAuthorization 事件？
  - 1. 调用隐私相关接口（比如 wx.getUserProfile、wx.getClipboardData）和组件（比如 `<button open-type="getPhoneNumber"></button>`），并且用户还未同意过隐私协议时
  - 2. 调用 wx.requirePrivacyAuthorize 接口来模拟隐私接口调用，并且用户还未同意过隐私协议时
  - 3. 如果用户已经同意过隐私协议，则不会再触发 onNeedPrivacyAuthorization 事件
- 2. 当触发 onNeedPrivacyAuthorization 事件时，触发该事件的隐私接口或组件会处于 pending 状态，等待用户授权后才会继续执行，此时开发者需要弹出自定义隐私弹窗，并在用户点击同意/拒绝后调用回调接口 resolve ，触发该事件的隐私接口或组件才会继续执行。
- 3. wx.onNeedPrivacyAuthorization 是覆盖式注册监听，若重复注册监听，则只有最后一次注册会生效。
- 4. 一定要注册 wx.onNeedPrivacyAuthorization 监听以及调用 resolve 吗？
  - 1. 不是的，如果能保证在调用隐私接口之前，用户已经轻触过了 `<button open-type="agreePrivacyAuthorization">` 按钮，那就不需要 wx.onNeedPrivacyAuthorization。
  - 2. 但如果注册了 wx.onNeedPrivacyAuthorization 监听，则一定要调用 resolve 接口。

## [#](#示例代码) 示例代码

```
// page.wxml
<view wx:if="{{showPrivacy}}">
  <view>隐私弹窗内容....</view>
  <button id="agree-btn" open-type="agreePrivacyAuthorization" bindagreeprivacyauthorization="handleAgreePrivacyAuthorization">同意</button>
</view>
```

```
// page.js
Page({
  data: {
    showPrivacy: false
  },
  onLoad() {
    wx.onNeedPrivacyAuthorization((resolve, eventInfo) => {
      console.log('触发本次事件的接口是：' + eventInfo.referrer)
      // 需要用户同意隐私授权时
      // 弹出开发者自定义的隐私授权弹窗
      this.setData({
        showPrivacy: true
      })
      this.resolvePrivacyAuthorization = resolve
    })

    wx.getUserProfile({
      success: console.log,
      fail: console.error
    })
  },
  handleAgreePrivacyAuthorization() {
    // 用户点击同意按钮后
    this.resolvePrivacyAuthorization({ buttonId: 'agree-btn', event: 'agree' })
    // 用户点击同意后，开发者调用 resolve({ buttonId: 'agree-btn', event: 'agree' })  告知平台用户已经同意，参数传同意按钮的id。为确保用户有同意的操作，基础库在 resolve 被调用后，会去检查对应的同意按钮有没有被点击过。检查通过后，相关隐私接口会继续调用
    // 用户点击拒绝后，开发者调用 resolve({ event:'disagree' }) 告知平台用户已经拒绝
  }
})
```

## [#](#完整示例demo) 完整示例demo

demo1: 演示使用 `wx.getPrivacySetting` 和 `<button open-type="agreePrivacyAuthorization">` 在首页处理隐私弹窗逻辑
<https://developers.weixin.qq.com/s/gi71sGm67hK0>

demo2: 演示使用 `wx.onNeedPrivacyAuthorization` 和 `<button open-type="agreePrivacyAuthorization">` 在多个页面处理隐私弹窗逻辑，同时演示了如何处理多个隐私接口同时调用。
<https://developers.weixin.qq.com/s/hndZUOmA7gKn>

demo3: 演示 `wx.onNeedPrivacyAuthorization`、`wx.requirePrivacyAuthorize`、`<button open-type="agreePrivacyAuthorization">` 和 `<input type="nickname">` 组件如何结合使用
<https://developers.weixin.qq.com/s/jX7xWGmA7UKa>

demo4: 演示使用 `wx.onNeedPrivacyAuthorization` 和 `<button open-type="agreePrivacyAuthorization">` 在多个 tabBar 页面处理隐私弹窗逻辑。
<https://developers.weixin.qq.com/s/g6BWZGmt7XK9>

Incorrect translation.