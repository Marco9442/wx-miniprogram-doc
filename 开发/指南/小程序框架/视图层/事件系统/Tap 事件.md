# [#](#Tap-事件) Tap 事件

## [#](#什么是-tap-事件) 什么是 tap 事件

tap 事件表示一次用户的"点击"操作：

- **移动端**：手指按下后抬起
- **PC / 开发者工具**：鼠标按下后抬起

tap 事件是基于 Web 标准的 touch 事件封装而来。与原生 click 事件不同，tap 没有 300ms 的延迟，响应更快。

在 WXML 中，通过 `bindtap` 或 `catchtap` 绑定 tap 事件的处理函数：

```
<view bindtap="handleTap">点击我</view>
<button catchtap="handleButtonTap">按钮</button>
```

```
Page({
  handleTap(e) {
    console.log('触发了 tap 事件', e)
  },
  handleButtonTap(e) {
    console.log('按钮被点击', e)
  }
})
```

tap 事件对象中包含点击的位置等信息，具体字段请参考[事件系统](../custom-component/events)。

---

## [#](#点击态) 点击态

### [#](#什么是点击态) 什么是点击态

部分敏感 API（如 `wx.openSetting`、`wx.requestSubscribeMessage`）必须由用户主动点击触发，不允许在无用户交互的情况下被调用。基础库通过**点击态**机制来实现这一限制：只有当代码运行在用户点击所产生的执行上下文中时，这些 API 才能被成功调用。

简单来说：**用户点了 → 你的事件回调里有点击态 → 可以调用敏感 API**。

### [#](#点击态的获取) 点击态的获取

以下场景中，代码执行时具有点击态：

#### [#](#_1-tap-事件回调) 1. tap 事件回调

用户点击触发的事件处理函数天然具有点击态：

```
Page({
  handleTap() {
    // ✅ 此处有点击态
    wx.openSetting({})
  }
})
```

```
<button bindtap="handleTap">打开设置</button>
```

#### [#](#_2-特定-API-的回调) 2. 特定 API 的回调

以下 API 的回调中也具有点击态：

| API | 说明 |
| --- | --- |
| `wx.showModal` | success/complete 回调中具有点击态 |
| `wx.showActionSheet` | success/complete 回调中具有点击态 |
| `wx.requestPayment` | success/complete/fail 回调中具有点击态 |
| `wx.requestOrderPayment` | success/complete/fail 回调中具有点击态 |

```
wx.showModal({
  title: '提示',
  content: '是否订阅消息？',
  success(res) {
    if (res.confirm) {
      // ✅ 此处有点击态，可调用敏感 API
      wx.requestSubscribeMessage({ tmplIds: ['...'] })
    }
  }
})
```

> 注意：`wx.requestPayment` 和 `wx.requestOrderPayment` 回调中获得的点击态**不可**用于触发 `wx.openEmbeddedMiniProgram`，详见[支付后打开半屏小程序能力的相关调整通知](https://developers.weixin.qq.com/community/develop/doc/000644871006f83372416ff2c66801)。

### [#](#点击态的传递) 点击态的传递

在事件回调中调用以下 API 时，如果调用时具有点击态，则该 API 的 success/complete/fail 回调会**继承**点击态：

- `wx.request`
- `wx.downloadFile`
- `wx.getSetting`

这使得"点击后发请求，请求完成后调用敏感 API"这一常见模式能够正常工作：

```
Page({
  handleTap() {
    // ✅ 有点击态
    wx.request({
      url: 'https://example.com/api/check',
      success(res) {
        // ✅ 点击态被传递到此处
        wx.openSetting({})
      }
    })
  }
})
```

点击态的传递支持链式调用：

```
Page({
  handleTap() {
    // ✅ 有点击态
    wx.request({
      url: 'https://example.com/api/step1',
      success() {
        // ✅ 有点击态
        wx.request({
          url: 'https://example.com/api/step2',
          success() {
            // ✅ 有点击态，仍可调用敏感 API
            wx.requestSubscribeMessage({ tmplIds: ['...'] })
          }
        })
      }
    })
  }
})
```

### [#](#点击态的生命周期) 点击态的生命周期

点击态在**当前宏任务结束时自动失效**，而不是被某个 API 调用后立即消耗。这意味着在同一个同步执行流中，可以多次调用需要点击态的 API：

```
Page({
  handleTap() {
    // ✅ 有点击态
    wx.openSetting({})              // 成功调用
    wx.requestSubscribeMessage({    // 仍然成功，点击态未被消耗
      tmplIds: ['...']
    })
    wx.request({
      url: 'https://example.com/api',
      success() {
        // ✅ 有点击态（通过 wx.request 的传递机制）
      }
    })
  }
})
```

但 `setTimeout` / `setInterval` 会创建新的宏任务，点击态不会延续到新的宏任务中：

```
Page({
  handleTap() {
    // ✅ 有点击态

    setTimeout(() => {
      // ❌ 新的宏任务，点击态已失效
      wx.openSetting({}) // 调用失败
    }, 0)

    setInterval(() => {
      // ❌ 新的宏任务，点击态已失效
    }, 1000)
  }
})
```

微任务（microtask）在当前宏任务内执行，因此点击态保持有效：

```
Page({
  async handleTap() {
    // ✅ 有点击态

    await someAsyncOperation()
    // ✅ 点击态仍然有效（Promise/async/await 属于微任务）

    wx.openSetting({}) // 成功调用
  }
})
```

### [#](#需要点击态的-API-列表) 需要点击态的 API 列表

以下 API 必须在具有点击态的上下文中调用，否则会调用失败或功能降级：

| API | 说明 |
| --- | --- |
| [`wx.openSetting`](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/setting/wx.openSetting.html) | 打开设置页面 |
| [`wx.requestSubscribeMessage`](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/subscribe-message/wx.requestSubscribeMessage.html) | 请求订阅消息 |
| [`wx.requestSubscribeDeviceMessage`](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/subscribe-message/wx.requestSubscribeDeviceMessage.html) | 请求订阅设备消息 |
| [`wx.exitMiniProgram`](https://developers.weixin.qq.com/miniprogram/dev/api/navigate/wx.exitMiniProgram.html) | 退出小程序 |
| [`wx.getUserProfile`](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/user-info/wx.getUserProfile.html) | 获取用户信息 |
| [`wx.openCustomerServiceChat`](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/service-chat/wx.openCustomerServiceChat.html) | 打开客服会话 |
| [`wx.addPhoneCalendar`](https://developers.weixin.qq.com/miniprogram/dev/api/device/calendar/wx.addPhoneCalendar.html) | 添加手机日历事件 |
| [`wx.addPhoneRepeatCalendar`](https://developers.weixin.qq.com/miniprogram/dev/api/device/calendar/wx.addPhoneRepeatCalendar.html) | 添加手机重复日历事件 |
| [`wx.chooseLicensePlate`](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/license-plate/wx.chooseLicensePlate.html) | 选择车牌号 |
| [`wx.shareFileMessage`](https://developers.weixin.qq.com/miniprogram/dev/api/share/wx.shareFileMessage.html) | 分享文件到聊天 |
| [`wx.shareVideoMessage`](https://developers.weixin.qq.com/miniprogram/dev/api/share/wx.shareVideoMessage.html) | 分享视频到聊天 |
| [`wx.addFileToFavorites`](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/favorites/wx.addFileToFavorites.html) | 添加文件到收藏 |
| [`wx.addVideoToFavorites`](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/favorites/wx.addVideoToFavorites.html) | 添加视频到收藏 |
| [`wx.openSystemBluetoothSetting`](https://developers.weixin.qq.com/miniprogram/dev/api/base/system/wx.openSystemBluetoothSetting.html) | 打开系统蓝牙设置 |
| [`wx.openAppAuthorizeSetting`](https://developers.weixin.qq.com/miniprogram/dev/api/base/system/wx.openAppAuthorizeSetting.html) | 打开应用权限设置 |
| [`wx.openOfficialAccountArticle`](https://developers.weixin.qq.com/miniprogram/dev/api/navigate/wx.openOfficialAccountArticle.html) | 打开公众号文章 |
| [`wx.openOfficialAccountProfile`](https://developers.weixin.qq.com/miniprogram/dev/api/navigate/wx.openOfficialAccountProfile.html) | 打开公众号资料页 |
| [`wx.openChannelsLiveNoticeInfo`](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/channels/wx.openChannelsLiveNoticeInfo.html) | 打开视频号直播预告 |
| [`wx.openInquiriesTopic`](https://developers.weixin.qq.com/miniprogram/dev/api/navigate/wx.openInquiriesTopic.html) | 打开问一问话题 |
| [`wx.notifyGroupMembers`](https://developers.weixin.qq.com/miniprogram/dev/api/chattool/wx.notifyGroupMembers.html) | 通知群成员 |
| [`wx.shareFileToGroup`](https://developers.weixin.qq.com/miniprogram/dev/api/chattool/wx.shareFileToGroup.html) | 分享文件到群 |
| [`wx.shareImageToGroup`](https://developers.weixin.qq.com/miniprogram/dev/api/chattool/wx.shareImageToGroup.html) | 分享图片到群 |
| [`wx.shareVideoToGroup`](https://developers.weixin.qq.com/miniprogram/dev/api/chattool/wx.shareVideoToGroup.html) | 分享视频到群 |
| [`wx.shareToOfficialAccount`](https://developers.weixin.qq.com/miniprogram/dev/api/share/wx.shareToOfficialAccount.html) | 分享到公众号 |
| [`wx.openEmbeddedMiniProgram`](https://developers.weixin.qq.com/miniprogram/dev/api/navigate/wx.openEmbeddedMiniProgram.html) | 打开半屏小程序 |
| [`VideoContext.startCasting`](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.startCasting.html) | 开始投屏，拉起半屏搜索设备 |
| [`VideoContext.switchCasting`](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.switchCasting.html) | 切换投屏设备 |
| [`VideoContext.reconnectCasting`](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.reconnectCasting.html) | 重连投屏设备 |
| [`VideoContext.exitCasting`](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.exitCasting.html) | 退出投屏 |

### [#](#常见错误与排查) 常见错误与排查

在缺少点击态的情况下调用上述 API，会收到如下错误信息：

```
{apiName}:fail can only be invoked by user TAP gesture.
```

例如：

```
// 在 onLoad 中直接调用（无点击态）
Page({
  onLoad() {
    wx.openSetting({
      fail(err) {
        console.log(err.errMsg)
        // "openSetting:fail can only be invoked by user TAP gesture."
      }
    })
  }
})
```

### [#](#最佳实践) 最佳实践

1. **尽早调用敏感 API**：在点击事件回调中尽快调用需要点击态的 API，避免不必要的异步延迟。
2. **避免在 setTimeout 中调用**：`setTimeout`/`setInterval` 会创建新的宏任务，导致点击态失效。
3. **利用点击态传递**：如果需要先请求后端再调用敏感 API，使用 `wx.request` 的回调来组织代码，点击态会自动传递到回调中。

Incorrect translation.