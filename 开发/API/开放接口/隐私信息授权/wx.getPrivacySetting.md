# [#](#wx-getPrivacySetting-Object-object) wx.getPrivacySetting(Object object)

> 基础库 2.32.3 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：不支持
>
> **小程序插件**：不支持
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

查询隐私授权情况。隐私合规开发指南详情可见[《小程序隐私协议开发指南》](https://developers.weixin.qq.com/miniprogram/dev/framework/user-privacy/PrivacyAuthorize.html)

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| needAuthorization | boolean | 是否需要用户授权隐私协议（如果开发者没有在「MP后台-设置-服务内容声明-用户隐私保护指引」中声明隐私收集类型则会返回false；如果开发者声明了隐私收集，且用户之前同意过隐私协议则会返回false；如果开发者声明了隐私收集，且用户还没同意过则返回true；如果用户之前同意过、但后来小程序又新增了隐私收集类型也会返回true） |
| privacyContractName | string | 隐私授权协议的名称 |

## [#](#具体说明：) 具体说明：

1. 一定要调用 wx.getPrivacySetting 接口吗？

- 不是，wx.getPrivacySetting 只是一个辅助接口，可以根据实际情况选择使用。

## [#](#示例代码) 示例代码

```
// page.wxml
<view wx:if="{{showPrivacy}}">
  <view>隐私弹窗内容....</view>
  <button id="agree-btn" open-type="agreePrivacyAuthorization" bindagreeprivacyauthorization="handleAgreePrivacyAuthorization">同意</button>
</view>
```

```
Page({
  data: {
    showPrivacy: false
  },
  onLoad() {
    wx.getPrivacySetting({
      success: res => {
        console.log(res) // 返回结果为: res = { needAuthorization: true/false, privacyContractName: '《xxx隐私保护指引》' }
        if (res.needAuthorization) {
          // 需要弹出隐私协议
          this.setData({
            showPrivacy: true
          })
        } else {
          // 用户已经同意过隐私协议，所以不需要再弹出隐私协议，也能调用隐私接口
        }
      },
      fail: () => {},
      complete: () => {}
    })
  },
  handleAgreePrivacyAuthorization() {
    // 用户同意隐私协议事件回调
    // 用户点击了同意，之后所有隐私接口和组件都可以调用了
    // wx.getUserProfile()
    // wx.chooseMedia()
    // wx.getClipboardData()
    // wx.startRecord()
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