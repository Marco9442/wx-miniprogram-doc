# [#](#API-总览) API 总览

- **当前最新版 多端 SDK（ 即 Android SDK >= 1.5 以及 iOS SDK >= 1.5.3 版本) 对齐小程序基础库的版本是 3.6.5；其余版本 SDK 对齐小程序基础库的版本是 3.2.5**
- 其他通用接口的接口文档可查看 [小程序 API 文档中心](/miniprogram/dev/api/)，如果与小程序 API 有所区别的即可点击跳转对应接口文档
- 是否支持：指的是是否适用于多端框架；由于和小程序是同源 API，「否」表示的是只支持小程序环境中使用，不适用于多端框架使用
- 如果测试出现了不符合预期的情况，可先检查一下 SDK 是否已经是最新的，以及是否配置了扩展 SDK ，如自查依旧无法定位问题可前往[社区](https://developers.weixin.qq.com/community/develop/mixflow)进行反馈
- 如开发者的 App 中需使用到下方标记的尚未支持的 API，可前往[社区](https://developers.weixin.qq.com/community/develop/mixflow)进行反馈

图表中

是[1]: 表示支持，但 API 返回的内容和小程序的存在差异

否[1]: 表示不支持，原因是有替代方案

支持的类型

1. 支持，但 API 返回内容有差异
2. 支持，但交互行为存在差异
3. 支持，但停止维护

不支持的原因

1. 有其他替代方案
2. 尚未支持，后续会支持
3. 尚未支持，后续会支持，但是 API 含义会有差异
4. 微信特有交互流程，后续不会支持
5. 已废弃，后续不会支持
6. 特定系统才有的 API，后续不会支持

补充：

- 点此查看[基础 SDK 包含的 JSAPI](../pre-read/sdk/sdk#_2-1-1-%E5%9F%BA%E7%A1%80-sdk-%E5%B7%B2%E7%BB%8F%E5%8C%85%E5%90%AB%E7%9A%84-jsapi-%E5%A6%82%E4%B8%8B)
- 点此查看[JSAPI 对应依赖的 扩展 SDK](../pre-read/sdk/sdk#_2-2-%E6%89%A9%E5%B1%95-sdk)

## [#](#基础) 基础

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.env](https://developers.weixin.qq.com/miniprogram/dev/api/base/wx.env.html) | 环境变量 | 是 |
| [wx.canIUse](https://developers.weixin.qq.com/miniprogram/dev/api/base/wx.canIUse.html) | 判断应用的 API，回调，参数，组件等是否在当前版本可用 | 是 |
| [wx.base64ToArrayBuffer](https://developers.weixin.qq.com/miniprogram/dev/api/base/wx.base64ToArrayBuffer.html) | 将 Base64 字符串转成 ArrayBuffer 对象 | 是[3] |
| [wx.arrayBufferToBase64](https://developers.weixin.qq.com/miniprogram/dev/api/base/wx.arrayBufferToBase64.html) | 将 ArrayBuffer 对象转成 Base64 字符串 | 是[3] |

### [#](#系统) 系统

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.getSystemInfo](diffapi/getSystemInfo) | 获取系统信息 | 是[1] |
| [wx.openSystemBluetoothSetting](https://developers.weixin.qq.com/miniprogram/dev/api/base/system/wx.openSystemBluetoothSetting.html) | 跳转系统蓝牙设置页 | 否[2] |
| [wx.openAppAuthorizeSetting](https://developers.weixin.qq.com/miniprogram/dev/api/base/system/wx.openAppAuthorizeSetting.html) | 跳转系统授权管理页 | 是 |
| [wx.getAppAuthorizeSetting](https://developers.weixin.qq.com/miniprogram/dev/api/base/system/wx.getAppAuthorizeSetting.html) | 获取 App 授权设置 | 是 |
| [wx.getWindowInfo](https://developers.weixin.qq.com/miniprogram/dev/api/base/system/wx.getWindowInfo.html) | 获取窗口信息 | 是 |
| [wx.getSystemSetting](https://developers.weixin.qq.com/miniprogram/dev/api/base/system/wx.getSystemSetting.html) | 获取设备设置 | 是 |
| [wx.getSystemInfoSync](diffapi/getSystemInfo) | wx.getSystemInfo 的同步版本 | 是[1] |
| [wx.getSystemInfoAsync](diffapi/getSystemInfo) | 异步获取系统信息 | 是[1] |
| [wx.getDeviceInfo](https://developers.weixin.qq.com/miniprogram/dev/api/base/system/wx.getDeviceInfo.html) | 获取设备基础信息 | 是 |
| [wx.getAppBaseInfo](diffapi/getAppBaseInfo) | 获取 App 基础信息 | 是[1] |

### [#](#更新) 更新

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.updateWeChatApp](https://developers.weixin.qq.com/miniprogram/dev/api/base/update/wx.updateWeChatApp.html) | 更新客户端版本 | 否[4] |
| [wx.getUpdateManager](https://developers.weixin.qq.com/miniprogram/dev/api/base/update/wx.getUpdateManager.html) | 获取全局唯一的版本更新管理器，用于管理小程序更新 | 是，[查看使用要求](../handbook/web/publish) |

### [#](#生命周期) 生命周期

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.getLaunchOptionsSync](diffapi/getLaunchOptionsSync) | 获取应用启动时的参数 | 是[1] |
| [wx.getEnterOptionsSync](diffapi/getEnterOptionsSync) | 获取本次应用启动时的参数 | 是[1] |

### [#](#应用级事件) 应用级事件

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.onUnhandledRejection](https://developers.weixin.qq.com/miniprogram/dev/api/base/app/app-event/wx.onUnhandledRejection.html) | 监听未处理的 Promise 拒绝事件 | 是 |
| [wx.onThemeChange](https://developers.weixin.qq.com/miniprogram/dev/api/base/app/app-event/wx.onThemeChange.html) | 监听系统主题改变事件 | 是 |
| [wx.onPageNotFound](https://developers.weixin.qq.com/miniprogram/dev/api/base/app/app-event/wx.onPageNotFound.html) | 监听应用要打开的页面不存在事件 | 是 |
| [wx.onLazyLoadError](https://developers.weixin.qq.com/miniprogram/dev/api/base/app/app-event/wx.onLazyLoadError.html) | 监听应用异步组件加载失败回调 | 是 |
| [wx.onError](https://developers.weixin.qq.com/miniprogram/dev/api/base/app/app-event/wx.onError.html) | 监听应用错误事件 | 是 |
| [wx.onAudioInterruptionEnd](https://developers.weixin.qq.com/miniprogram/dev/api/base/app/app-event/wx.onAudioInterruptionEnd.html) | 监听音频中断结束事件 | 是 |
| [wx.onAudioInterruptionBegin](https://developers.weixin.qq.com/miniprogram/dev/api/base/app/app-event/wx.onAudioInterruptionBegin.html) | 监听音频因为受到系统占用而被中断开始事件 | 是 |
| [wx.onAppShow](https://developers.weixin.qq.com/miniprogram/dev/api/base/app/app-event/wx.onAppShow.html) | 应用切前台事件 | 是 |
| [wx.onAppHide](https://developers.weixin.qq.com/miniprogram/dev/api/base/app/app-event/wx.onAppHide.html) | 监听应用切后台事件 | 是 |
| [wx.offUnhandledRejection](https://developers.weixin.qq.com/miniprogram/dev/api/base/app/app-event/wx.offUnhandledRejection.html) | 取消监听未处理的 Promise 拒绝事件 | 是 |
| [wx.offThemeChange](https://developers.weixin.qq.com/miniprogram/dev/api/base/app/app-event/wx.offThemeChange.html) | 取消监听系统主题改变事件 | 是 |
| [wx.offPageNotFound](https://developers.weixin.qq.com/miniprogram/dev/api/base/app/app-event/wx.offPageNotFound.html) | 取消监听应用要打开的页面不存在事件 | 是 |
| [wx.offLazyLoadError](https://developers.weixin.qq.com/miniprogram/dev/api/base/app/app-event/wx.offLazyLoadError.html) | 取消监听应用异步组件加载失败回调 | 是 |
| [wx.offError](https://developers.weixin.qq.com/miniprogram/dev/api/base/app/app-event/wx.offError.html) | 取消监听应用错误事件 | 是 |
| [wx.offAudioInterruptionEnd](https://developers.weixin.qq.com/miniprogram/dev/api/base/app/app-event/wx.offAudioInterruptionEnd.html) | 取消监听音频中断结束事件 | 是 |
| [wx.offAudioInterruptionBegin](https://developers.weixin.qq.com/miniprogram/dev/api/base/app/app-event/wx.offAudioInterruptionBegin.html) | 取消监听音频因为受到系统占用而被中断开始事件 | 是 |
| [wx.offAppShow](https://developers.weixin.qq.com/miniprogram/dev/api/base/app/app-event/wx.offAppShow.html) | 取消监听应用切前台事件 | 是 |
| [wx.offAppHide](https://developers.weixin.qq.com/miniprogram/dev/api/base/app/app-event/wx.offAppHide.html) | 取消监听应用切后台事件 | 是 |

### [#](#调试) 调试

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.setEnableDebug](https://developers.weixin.qq.com/miniprogram/dev/api/base/debug/wx.setEnableDebug.html) | 设置是否打开调试开关 | 是 |
| [wx.getRealtimeLogManager](https://developers.weixin.qq.com/miniprogram/dev/api/base/debug/wx.getRealtimeLogManager.html) | 获取实时日志管理器对象 | 是[2]，但日志只在本地生效，尚未有系统可以查询 |
| [wx.getLogManager](https://developers.weixin.qq.com/miniprogram/dev/api/base/debug/wx.getLogManager.html) | 获取日志管理器对象 | 是[2]，但日志只在本地生效，尚未有系统可以查询 |

### [#](#性能) 性能

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.reportPerformance](https://developers.weixin.qq.com/miniprogram/dev/api/base/performance/wx.reportPerformance.html) | 小程序测速上报 | 否[2] |
| [wx.preloadWebview](https://developers.weixin.qq.com/miniprogram/dev/api/base/performance/wx.preloadWebview.html) | 预加载下个页面的 WebView | 否[2] |
| [wx.preloadSkylineView](https://developers.weixin.qq.com/miniprogram/dev/api/base/performance/wx.preloadSkylineView.html) | 预加载下个页面所需要的 Skyline 运行环境 | 否[2] |
| [wx.preloadAssets](https://developers.weixin.qq.com/miniprogram/dev/api/base/performance/wx.preloadAssets.html) | 为视图层预加载媒体资源文件, 目前支持：font，image | 否[2] |
| [wx.getPerformance](https://developers.weixin.qq.com/miniprogram/dev/api/base/performance/wx.getPerformance.html) | 获取当前应用性能相关的信息 | 是 |

### [#](#加密) 加密

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.getUserCryptoManager](https://developers.weixin.qq.com/miniprogram/dev/api/base/crypto/wx.getUserCryptoManager.html) | 获取用户加密模块 | 否[1]，可使用[微信网关](https://developers.weixin.qq.com/miniprogram/security/gateway/)替代 |

## [#](#路由) 路由

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.switchTab](https://developers.weixin.qq.com/miniprogram/dev/api/route/wx.switchTab.html) | 跳转到 tabBar 页面，并关闭其他所有非 tabBar 页面 | 是 |
| [wx.reLaunch](https://developers.weixin.qq.com/miniprogram/dev/api/route/wx.reLaunch.html) | 关闭所有页面，打开到应用内的某个页面 | 是 |
| [wx.redirectTo](https://developers.weixin.qq.com/miniprogram/dev/api/route/wx.redirectTo.html) | 关闭当前页面，跳转到应用内的某个页面 | 是 |
| [wx.navigateTo](https://developers.weixin.qq.com/miniprogram/dev/api/route/wx.navigateTo.html) | 保留当前页面，跳转到应用内的某个页面 | 是 |
| [wx.navigateBack](https://developers.weixin.qq.com/miniprogram/dev/api/route/wx.navigateBack.html) | 关闭当前页面，返回上一页面或多级页面 | 是 |

### [#](#EventChannel) EventChannel

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [EventChannel.emit](https://developers.weixin.qq.com/miniprogram/dev/api/route/EventChannel.emit.html) | 触发一个事件 | 是 |
| [EventChannel.off](https://developers.weixin.qq.com/miniprogram/dev/api/route/EventChannel.off.html) | 取消监听一个事件 | 是 |
| [EventChannel.on](https://developers.weixin.qq.com/miniprogram/dev/api/route/EventChannel.on.html) | 持续监听一个事件 | 是 |
| [EventChannel.once](https://developers.weixin.qq.com/miniprogram/dev/api/route/EventChannel.once.html) | 监听一个事件一次，触发后失效 | 是 |

## [#](#跳转) 跳转

- wx.navigateToMiniProgram 不支持，开发者可使用新接口 [wx.miniapp.launchMiniProgram](miniapp/launchMiniProgram) 实现

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.openEmbeddedMiniProgram](https://developers.weixin.qq.com/miniprogram/dev/api/navigate/wx.openEmbeddedMiniProgram.html) | 打开半屏小程序 | 否[4] |
| [wx.navigateToMiniProgram](https://developers.weixin.qq.com/miniprogram/dev/api/navigate/wx.navigateToMiniProgram.html) | 打开另一个小程序 | 否[4] |
| [wx.navigateBackMiniProgram](https://developers.weixin.qq.com/miniprogram/dev/api/navigate/wx.navigateBackMiniProgram.html) | 返回到上一个小程序 | 否[4] |
| [wx.exitMiniProgram](https://developers.weixin.qq.com/miniprogram/dev/api/navigate/wx.exitMiniProgram.html) | 退出当前小程序 | 否[4] |

## [#](#转发) 转发

- 可以通过新接口实现分享到微信的功能，详情可查看
  [wx.miniapp.shareImageMessage](miniapp/shareImageMessage)、
  [wx.miniapp.shareMiniProgramMessage](miniapp/shareMiniProgramMessage)、
  [wx.miniapp.shareTextMessage](miniapp/shareTextMessage)、
  [wx.miniapp.shareWebPageMessage](miniapp/shareWebPageMessage)、
  [wx.miniapp.shareVideoMessage](miniapp/shareVideoMessage)

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.updateShareMenu](https://developers.weixin.qq.com/miniprogram/dev/api/share/wx.updateShareMenu.html) | 更新转发属性 | 否[4] |
| [wx.showShareMenu](https://developers.weixin.qq.com/miniprogram/dev/api/share/wx.showShareMenu.html) | 显示当前页面的转发按钮 | 否[4] |
| [wx.showShareImageMenu](https://developers.weixin.qq.com/miniprogram/dev/api/share/wx.showShareImageMenu.html) | 打开分享图片弹窗，可以将图片发送给朋友、收藏或下载 | 否[4] |
| [wx.shareVideoMessage](https://developers.weixin.qq.com/miniprogram/dev/api/share/wx.shareVideoMessage.html) | 转发视频到聊天 | 否[1] |
| [wx.shareFileMessage](https://developers.weixin.qq.com/miniprogram/dev/api/share/wx.shareFileMessage.html) | 转发文件到聊天 | 否[1] |
| [wx.onCopyUrl](https://developers.weixin.qq.com/miniprogram/dev/api/share/wx.onCopyUrl.html) | 监听用户点击右上角菜单的「复制链接」按钮时触发的事件 | 否[4] |
| [wx.offCopyUrl](https://developers.weixin.qq.com/miniprogram/dev/api/share/wx.updateShareMenu.html) | 移除用户点击右上角菜单的「复制链接」按钮时触发的事件的监听函数 | 否[4] |
| [wx.hideShareMenu](https://developers.weixin.qq.com/miniprogram/dev/api/share/wx.hideShareMenu.html) | 隐藏当前页面的转发按钮 | 否[4] |
| [wx.getShareInfo](https://developers.weixin.qq.com/miniprogram/dev/api/share/wx.getShareInfo.html) | 获取转发详细信息 | 否[4] |
| [wx.authPrivateMessage](https://developers.weixin.qq.com/miniprogram/dev/api/share/wx.authPrivateMessage.html) | 验证私密消息 | 否[4] |

## [#](#界面) 界面

### [#](#交互) 交互

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.showToast](https://developers.weixin.qq.com/miniprogram/dev/api/ui/interaction/wx.showToast.html) | 显示消息提示框 | 是 |
| [wx.showModal](https://developers.weixin.qq.com/miniprogram/dev/api/ui/interaction/wx.showModal.html) | 显示模态对话框 | 是 |
| [wx.showLoading](https://developers.weixin.qq.com/miniprogram/dev/api/ui/interaction/wx.showLoading.html) | 显示 loading 提示框 | 是 |
| [wx.showActionSheet](https://developers.weixin.qq.com/miniprogram/dev/api/ui/interaction/wx.showActionSheet.html) | 显示操作菜单 | 是 |
| [wx.hideToast](https://developers.weixin.qq.com/miniprogram/dev/api/ui/interaction/wx.hideToast.html) | 隐藏消息提示框 | 是 |
| [wx.hideLoading](https://developers.weixin.qq.com/miniprogram/dev/api/ui/interaction/wx.hideLoading.html) | 隐藏 loading 提示框 | 是 |
| [wx.enableAlertBeforeUnload](https://developers.weixin.qq.com/miniprogram/dev/api/ui/interaction/wx.enableAlertBeforeUnload.html) | 开启应用页面返回询问对话框 | 是 |
| [wx.disableAlertBeforeUnload](https://developers.weixin.qq.com/miniprogram/dev/api/ui/interaction/wx.disableAlertBeforeUnload.html) | 关闭应用页面返回询问对话框 | 是 |

### [#](#导航栏) 导航栏

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.showNavigationBarLoading](https://developers.weixin.qq.com/miniprogram/dev/api/ui/navigation-bar/wx.showNavigationBarLoading.html) | 在当前页面显示导航条加载动画 | 是 |
| [wx.setNavigationBarTitle](https://developers.weixin.qq.com/miniprogram/dev/api/ui/navigation-bar/wx.setNavigationBarTitle.html) | 动态设置当前页面的标题 | 是 |
| [wx.setNavigationBarColor](https://developers.weixin.qq.com/miniprogram/dev/api/ui/navigation-bar/wx.setNavigationBarColor.html) | 设置页面导航条颜色 | 是 |
| [wx.hideNavigationBarLoading](https://developers.weixin.qq.com/miniprogram/dev/api/ui/navigation-bar/wx.hideNavigationBarLoading.html) | 在当前页面隐藏导航条加载动画 | 是 |
| [wx.hideHomeButton](https://developers.weixin.qq.com/miniprogram/dev/api/ui/navigation-bar/wx.hideHomeButton.html) | 隐藏返回首页按钮 | 是 |

### [#](#背景) 背景

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.setBackgroundTextStyle](https://developers.weixin.qq.com/miniprogram/dev/api/ui/background/wx.setBackgroundTextStyle.html) | 动态设置下拉背景字体、loading 图的样式 | 是 |
| [wx.setBackgroundColor](https://developers.weixin.qq.com/miniprogram/dev/api/ui/background/wx.setBackgroundTextStyle.html) | 动态设置窗口的背景色 | 是 |

### [#](#Tab-Bar) Tab Bar

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.showTabBarRedDot](https://developers.weixin.qq.com/miniprogram/dev/api/ui/tab-bar/wx.showTabBarRedDot.html) | 显示 tabBar 某一项的右上角的红点 | 是 |
| [wx.showTabBar](https://developers.weixin.qq.com/miniprogram/dev/api/ui/tab-bar/wx.showTabBar.html) | 显示 tabBar | 是 |
| [wx.setTabBarStyle](https://developers.weixin.qq.com/miniprogram/dev/api/ui/tab-bar/wx.setTabBarStyle.html) | 动态设置 tabBar 的整体样式 | 是 |
| [wx.setTabBarItem](https://developers.weixin.qq.com/miniprogram/dev/api/ui/tab-bar/wx.setTabBarItem.html) | 动态设置 tabBar 某一项的内容，`2.7.0` 起图片支持临时文件和网络文件 | 是 |
| [wx.setTabBarBadge](https://developers.weixin.qq.com/miniprogram/dev/api/ui/tab-bar/wx.setTabBarBadge.html) | 为 tabBar 某一项的右上角添加文本 | 是 |
| [wx.removeTabBarBadge](https://developers.weixin.qq.com/miniprogram/dev/api/ui/tab-bar/wx.removeTabBarBadge.html) | 移除 tabBar 某一项右上角的文本 | 是 |
| [wx.hideTabBarRedDot](https://developers.weixin.qq.com/miniprogram/dev/api/ui/tab-bar/wx.hideTabBarRedDot.html) | 隐藏 tabBar 某一项的右上角的红点 | 是 |
| [wx.hideTabBar](https://developers.weixin.qq.com/miniprogram/dev/api/ui/tab-bar/wx.hideTabBar.html) | 隐藏 tabBar |  |

### [#](#字体) 字体

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.loadFontFace](https://developers.weixin.qq.com/miniprogram/dev/api/ui/font/wx.loadFontFace.html) | 动态加载网络字体，文件地址需为下载类型 | 是 |

### [#](#下拉刷新) 下拉刷新

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.stopPullDownRefresh](https://developers.weixin.qq.com/miniprogram/dev/api/ui/pull-down-refresh/wx.stopPullDownRefresh.html) | 停止当前页面下拉刷新 | 是 |
| [wx.startPullDownRefresh](https://developers.weixin.qq.com/miniprogram/dev/api/ui/pull-down-refresh/wx.startPullDownRefresh.html) | 开始下拉刷新 | 是 |

### [#](#滚动) 滚动

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.pageScrollTo](https://developers.weixin.qq.com/miniprogram/dev/api/ui/scroll/wx.pageScrollTo.html) | 将页面滚动到目标位置，支持选择器和滚动距离两种方式定位 | 是 |

#### [#](#ScrollViewContext) ScrollViewContext

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [ScrollViewContext.scrollIntoView](https://developers.weixin.qq.com/miniprogram/dev/api/ui/scroll/ScrollViewContext.scrollIntoView.html) | 滚动至指定位置 | 是 |
| [ScrollViewContext.scrollTo](https://developers.weixin.qq.com/miniprogram/dev/api/ui/scroll/ScrollViewContext.scrollTo.html) | 滚动至指定位置 | 是 |

### [#](#动画) 动画

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.createAnimation](https://developers.weixin.qq.com/miniprogram/dev/api/ui/animation/wx.createAnimation.html) | 创建一个动画实例 [animation](https://developers.weixin.qq.com/miniprogram/dev/api/ui/animation/Animation.html) 对象 | 是 |

### [#](#置顶) 置顶

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.setTopBarText](https://developers.weixin.qq.com/miniprogram/dev/api/ui/sticky/wx.setTopBarText.html) | 动态设置置顶栏文字内容 | 否[5] |

### [#](#自定义组件) 自定义组件

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.nextTick](https://developers.weixin.qq.com/miniprogram/dev/api/ui/custom-component/wx.nextTick.html) | 延迟一部分操作到下一个时间片再执行 | 是 |

### [#](#菜单) 菜单

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.getMenuButtonBoundingClientRect](https://developers.weixin.qq.com/miniprogram/dev/api/ui/menu/wx.getMenuButtonBoundingClientRect.html) | 获取菜单按钮（右上角胶囊按钮）的布局位置信息 | 是[2], App 里不再呈现胶囊标识，该接口依旧返回相关坐标信息，便于开发者进行多端兼容 |

### [#](#窗口) 窗口

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.setWindowSize](https://developers.weixin.qq.com/miniprogram/dev/api/ui/window/wx.setWindowSize.html) | 设置窗口大小，该接口仅适用于 PC 平台 | 否[6] |
| [wx.onWindowResize](https://developers.weixin.qq.com/miniprogram/dev/api/ui/window/wx.onWindowResize.html) | 监听窗口尺寸变化事件 | 否[6] |
| [wx.offWindowResize](https://developers.weixin.qq.com/miniprogram/dev/api/ui/window/wx.offWindowResize.html) | 移除窗口尺寸变化事件的监听函数 | 否[6] |

### [#](#worklet-动画) worklet 动画

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.worklet](https://developers.weixin.qq.com/miniprogram/dev/api/ui/window/wx.setWindowSize.html) | 获取 worklet 对象 | 否[2] |

## [#](#网络) 网络

### [#](#发起请求) 发起请求

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.request](https://developers.weixin.qq.com/miniprogram/dev/api/network/request/wx.request.html) | 发起 HTTPS 网络请求 | 是 |

### [#](#下载) 下载

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.downloadFile](https://developers.weixin.qq.com/miniprogram/dev/api/network/download/wx.downloadFile.html) | 下载文件资源到本地 | 是[2]，下载允许的最大文件已调整为 2G |

### [#](#上传) 上传

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.uploadFile](https://developers.weixin.qq.com/miniprogram/dev/api/network/upload/wx.uploadFile.html) | 将本地资源上传到服务器 | 是 |

### [#](#WebSocket) WebSocket

- 下方 WebSocket 相关的 JSAPI 依赖扩展 SDK 「Network SDK」 ,开发者需在项目中的 `project.miniapp.json` 配置勾选对应的 SDK 方可生效；
- 注意：Android 和 iOS 的扩展 SDK 有所区别，详情查看 `project.miniapp.json`

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.sendSocketMessage](https://developers.weixin.qq.com/miniprogram/dev/api/network/websocket/wx.sendSocketMessage.html) | 通过 WebSocket 连接发送数据 | 是 |
| [wx.onSocketOpen](https://developers.weixin.qq.com/miniprogram/dev/api/network/websocket/wx.onSocketOpen.html) | 监听 WebSocket 连接打开事件 | 是 |
| [wx.onSocketMessage](https://developers.weixin.qq.com/miniprogram/dev/api/network/websocket/wx.onSocketMessage.html) | 监听 WebSocket 接受到服务器的消息事件 | 是 |
| [wx.onSocketError](https://developers.weixin.qq.com/miniprogram/dev/api/network/websocket/wx.onSocketError.html) | 监听 WebSocket 错误事件 | 是 |
| [wx.onSocketClose](https://developers.weixin.qq.com/miniprogram/dev/api/network/websocket/wx.onSocketClose.html) | 监听 WebSocket 连接关闭事件 | 是 |
| [wx.connectSocket](https://developers.weixin.qq.com/miniprogram/dev/api/network/websocket/wx.connectSocket.html) | 创建一个 WebSocket 连接 | 是 |
| [wx.closeSocket](https://developers.weixin.qq.com/miniprogram/dev/api/network/websocket/wx.closeSocket.html) | 关闭 WebSocket 连接 | 是 |

### [#](#mDNS) mDNS

- 下方 mDNS 相关的 JSAPI 依赖扩展 SDK 「Network SDK」 ,开发者需在项目中的 `project.miniapp.json` 配置勾选对应的 SDK 方可生效；
- 注意：Android 和 iOS 的扩展 SDK 有所区别，详情查看 `project.miniapp.json`

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.stopLocalServiceDiscovery](https://developers.weixin.qq.com/miniprogram/dev/api/network/mdns/wx.stopLocalServiceDiscovery.html) | 停止搜索 mDNS 服务 | 是 |
| [wx.startLocalServiceDiscovery](https://developers.weixin.qq.com/miniprogram/dev/api/network/mdns/wx.startLocalServiceDiscovery.html) | 开始搜索局域网下的 mDNS 服务 | 是 |
| [wx.onLocalServiceResolveFail](https://developers.weixin.qq.com/miniprogram/dev/api/network/mdns/wx.onLocalServiceResolveFail.html) | 监听 mDNS 服务解析失败的事件 | 是 |
| [wx.onLocalServiceLost](https://developers.weixin.qq.com/miniprogram/dev/api/network/mdns/wx.onLocalServiceLost.html) | 监听 mDNS 服务离开的事件 | 是 |
| [wx.onLocalServiceFound](https://developers.weixin.qq.com/miniprogram/dev/api/network/mdns/wx.onLocalServiceFound.html) | 监听 mDNS 服务发现的事件 | 是 |
| [wx.onLocalServiceDiscoveryStop](https://developers.weixin.qq.com/miniprogram/dev/api/network/mdns/wx.onLocalServiceDiscoveryStop.html) | 监听 mDNS 服务停止搜索的事件 | 是 |
| [wx.offLocalServiceResolveFail](https://developers.weixin.qq.com/miniprogram/dev/api/network/mdns/wx.offLocalServiceResolveFail.html) | 取消监听 mDNS 服务解析失败的事件 | 是 |
| [wx.offLocalServiceLost](https://developers.weixin.qq.com/miniprogram/dev/api/network/mdns/wx.offLocalServiceLost.html) | 取消监听 mDNS 服务离开的事件 | 是 |
| [wx.offLocalServiceFound](https://developers.weixin.qq.com/miniprogram/dev/api/network/mdns/wx.offLocalServiceFound.html) | 取消监听 mDNS 服务发现的事件 | 是 |
| [wx.offLocalServiceDiscoveryStop](https://developers.weixin.qq.com/miniprogram/dev/api/network/mdns/wx.offLocalServiceDiscoveryStop.html) | 取消监听 mDNS 服务停止搜索的事件 | 是 |

### [#](#TCP-通信) TCP 通信

- 下方 TCP 通信相关的 JSAPI 依赖扩展 SDK 「Network SDK」 ,开发者需在项目中的 `project.miniapp.json` 配置勾选对应的 SDK 方可生效；
- 注意：Android 和 iOS 的扩展 SDK 有所区别，详情查看 `project.miniapp.json`

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.createTCPSocket](https://developers.weixin.qq.com/miniprogram/dev/api/network/tcp/wx.createTCPSocket.html) | 创建一个 TCP Socket 实例 | 支持 |

### [#](#UDP-通信) UDP 通信

- 下方 UDP 通信相关的 JSAPI 依赖扩展 SDK 「Network SDK」 ,开发者需在项目中的 `project.miniapp.json` 配置勾选对应的 SDK 方可生效；
- 注意：Android 和 iOS 的扩展 SDK 有所区别，详情查看 `project.miniapp.json`

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.createUDPSocket](https://developers.weixin.qq.com/miniprogram/dev/api/network/udp/wx.createUDPSocket.html) | 创建一个 UDP Socket 实例 | 支持 |

## [#](#支付) 支付

- 需使用 [wx.miniapp.requestPayment](miniapp/requestPayment)
- iOS 的部分场景，需使用苹果内购 IAP（In-App Purchase），详情可查看[wx.miniapp.IAP](miniapp/IAP)
- 如果是 iOS ，则需要在项目中的 `project.miniapp.json` 配置勾选 「OpenFuns SDK（含支付）」这个扩展 SDK

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.requestPluginPayment](https://developers.weixin.qq.com/miniprogram/dev/api/payment/wx.requestPluginPayment.html) | 插件中发起支付 | 否[1] |
| [wx.requestPayment](https://developers.weixin.qq.com/miniprogram/dev/api/payment/wx.requestPayment.html) | 发起微信支付 | 否[1] |

## [#](#监听-Scheme-UniversalLink-进入多端-App) 监听 Scheme/UniversalLink 进入多端 App

- 需使用[wx.miniapp.registOpenURL](miniapp/registOpenURL)

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.miniapp.registOpenURL](miniapp/registOpenURL) | 监听通过 Scheme/UniversalLink 进入 App 的事件 | 是 |

## [#](#数据缓存) 数据缓存

- 多端应用模式下，wx.setStorage 的限制有所提升，单个 key 允许存储的最大数据长度为 100 MB，所有数据存储上限为 2G

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.setStorageSync](https://developers.weixin.qq.com/miniprogram/dev/api/storage/wx.setStorageSync.html) | 将数据存储在本地缓存中指定的 key 中 | 支持 |
| [wx.setStorage](https://developers.weixin.qq.com/miniprogram/dev/api/storage/wx.setStorage.html) | 将数据存储在本地缓存中指定的 key 中 | 支持 |
| [wx.revokeBufferURL](https://developers.weixin.qq.com/miniprogram/dev/api/storage/wx.revokeBufferURL.html) | 根据 URL 销毁存在内存中的数据 | 支持 |
| [wx.removeStorageSync](https://developers.weixin.qq.com/miniprogram/dev/api/storage/wx.removeStorageSync.html) | [wx.removeStorage](https://developers.weixin.qq.com/miniprogram/dev/api/storage/wx.removeStorage.html) 的同步版本 | 支持 |
| [wx.removeStorage](https://developers.weixin.qq.com/miniprogram/dev/api/storage/wx.removeStorage.html) | 从本地缓存中移除指定 key | 支持 |
| [wx.getStorageSync](https://developers.weixin.qq.com/miniprogram/dev/api/storage/wx.getStorageSync.html) | 从本地缓存中同步获取指定 key 的内容 | 支持 |
| [wx.getStorageInfoSync](https://developers.weixin.qq.com/miniprogram/dev/api/storage/wx.getStorageInfoSync.html) | [wx.getStorageInfo](https://developers.weixin.qq.com/miniprogram/dev/api/storage/wx.getStorageInfo.html) 的同步版本 | 支持 |
| [wx.getStorageInfo](https://developers.weixin.qq.com/miniprogram/dev/api/storage/wx.getStorageInfo.html) | 异步获取当前 storage 的相关信息 | 支持 |
| [wx.getStorage](https://developers.weixin.qq.com/miniprogram/dev/api/storage/wx.getStorage.html) | 从本地缓存中异步获取指定 key 的内容 | 支持 |
| [wx.createBufferURL](https://developers.weixin.qq.com/miniprogram/dev/api/storage/wx.createBufferURL.html) | 根据传入的 buffer 创建一个唯一的 URL 存在内存中 | 支持 |
| [wx.clearStorageSync](https://developers.weixin.qq.com/miniprogram/dev/api/storage/wx.clearStorageSync.html) | [wx.clearStorage](https://developers.weixin.qq.com/miniprogram/dev/api/storage/wx.clearStorage.html) 的同步版本 | 支持 |
| [wx.clearStorage](https://developers.weixin.qq.com/miniprogram/dev/api/storage/wx.clearStorage.html) | 清理本地数据缓存 | 支持 |
| [wx.batchSetStorageSync](https://developers.weixin.qq.com/miniprogram/dev/api/storage/wx.batchSetStorageSync.html) | 将数据批量存储在本地缓存中指定的 key 中 | 支持 |
| [wx.batchSetStorage](https://developers.weixin.qq.com/miniprogram/dev/api/storage/wx.batchSetStorage.html) | 将数据批量存储在本地缓存中指定的 key 中 | 支持 |
| [wx.batchGetStorageSync](https://developers.weixin.qq.com/miniprogram/dev/api/storage/wx.batchGetStorageSync.html) | 从本地缓存中同步批量获取指定 key 的内容 | 支持 |
| [wx.batchGetStorage](https://developers.weixin.qq.com/miniprogram/dev/api/storage/wx.batchGetStorage.html) | 从本地缓存中异步批量获取指定 key 的内容 | 支持 |

### [#](#周期性更新) 周期性更新

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.setBackgroundFetchToken](https://developers.weixin.qq.com/miniprogram/dev/api/storage/background-fetch/wx.setBackgroundFetchToken.html) | 设置自定义登录态，在周期性拉取数据时带上，便于第三方服务器验证请求合法性 | 否[2] |
| [wx.onBackgroundFetchData](https://developers.weixin.qq.com/miniprogram/dev/api/storage/background-fetch/wx.onBackgroundFetchData.html) | 监听收到 backgroundFetch 数据事件 | 否[2] |
| [wx.getBackgroundFetchToken](https://developers.weixin.qq.com/miniprogram/dev/api/storage/background-fetch/wx.getBackgroundFetchToken.html) | 获取设置过的自定义登录态 | 否[2] |
| [wx.getBackgroundFetchData](https://developers.weixin.qq.com/miniprogram/dev/api/storage/background-fetch/wx.getBackgroundFetchData.html) | 拉取 backgroundFetch 客户端缓存数据 | 否[2] |

### [#](#缓存管理器) 缓存管理器

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.createCacheManager](https://developers.weixin.qq.com/miniprogram/dev/api/storage/cachemanager/wx.createCacheManager.html) | 创建缓存管理器 | 否[2] |

## [#](#数据分析) 数据分析

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.reportMonitor](https://developers.weixin.qq.com/miniprogram/dev/api/data-analysis/wx.reportMonitor.html) | 自定义业务数据监控上报接口 | 否[2] |
| [wx.reportEvent](https://developers.weixin.qq.com/miniprogram/dev/api/data-analysis/wx.reportEvent.html) | 事件上报 | 否[2] |
| [wx.reportAnalytics](https://developers.weixin.qq.com/miniprogram/dev/api/data-analysis/wx.reportAnalytics.html) | 自定义分析数据上报接口 | 否[2] |
| [wx.getExptInfoSync](https://developers.weixin.qq.com/miniprogram/dev/api/data-analysis/wx.getExptInfoSync.html) | 给定实验参数数组，获取对应的实验参数值 | 否[2] |

## [#](#画布) 画布

- Android 端上使用 canvas 功能需要勾选 Xweb SDK ( XWeb SDK 或 XWeb Embed SDK 都可以)
- 可在开发者工具的 `project.miniapp.json` 中勾选上

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.createOffscreenCanvas](https://developers.weixin.qq.com/miniprogram/dev/api/canvas/wx.createOffscreenCanvas.html) | 创建离屏 canvas 实例 | 是 |
| [wx.createCanvasContext](https://developers.weixin.qq.com/miniprogram/dev/api/canvas/wx.createCanvasContext.html) | 创建 canvas 的绘图上下文 [CanvasContext](https://developers.weixin.qq.com/miniprogram/dev/api/canvas/CanvasContext.html) 对象 | 是 |
| [wx.canvasToTempFilePath](https://developers.weixin.qq.com/miniprogram/dev/api/canvas/wx.canvasToTempFilePath.html) | 把当前画布指定区域的内容导出生成指定大小的图片 | 是 |
| [wx.canvasPutImageData](https://developers.weixin.qq.com/miniprogram/dev/api/canvas/wx.canvasPutImageData.html) | 将像素数据绘制到画布 | 是 |
| [wx.canvasGetImageData](https://developers.weixin.qq.com/miniprogram/dev/api/canvas/wx.canvasGetImageData.html) | 获取 canvas 区域隐含的像素数据 | 是 |

## [#](#媒体) 媒体

### [#](#地图) 地图

- 如下支持的地图相关接口能力，需配置 LBS SDK ，且需前往腾讯位置服务平台注册开发者账号并创建应用 Key，详情可查看[位置服务使用指南](../handbook/devtools/lbs)

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.createMapContext](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/wx.createMapContext.html) | 创建 [map](https://developers.weixin.qq.com/miniprogram/dev/component/map.html)上下文 [MapContext](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/MapContext.html)对象 | 是[2] |

#### [#](#MapContext) MapContext

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [MapContext.addArc](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/MapContext.addArc.html) | 添加弧线，途经点与夹角必须设置一个 | 是 |
| [MapContext.addCustomLayer](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/MapContext.addCustomLayer.html) | 添加个性化图层 | 是 |
| [MapContext.addGroundOverlay](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/MapContext.addGroundOverlay.html) | 创建自定义图片图层，图片会随着地图缩放而缩放 | 是 |
| [MapContext.addMarkers](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/MapContext.addMarkers.html) | 添加 marker | 是 |
| [MapContext.addVisualLayer](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/MapContext.addVisualLayer.html) | 添加可视化图层 | 是 |
| [MapContext.fromScreenLocation](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/MapContext.fromScreenLocation.html) | 获取屏幕上的点对应的经纬度，坐标原点为地图左上角 | 是 |
| [MapContext.getCenterLocation](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/MapContext.getCenterLocation.html) | 获取当前地图中心的经纬度 | 是 |
| [MapContext.getRegion](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/MapContext.getRegion.html) | 获取当前地图的视野范围 | 是 |
| [MapContext.getRotate](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/MapContext.getRotate.html) | 获取当前地图的旋转角 | 是 |
| [MapContext.getScale](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/MapContext.getScale.html) | 获取当前地图的缩放级别 | 是 |
| [MapContext.getSkew](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/MapContext.getSkew.html) | 获取当前地图的倾斜角 | 是 |
| [MapContext.includePoints](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/MapContext.includePoints.html) | 缩放视野展示所有经纬度 | 是 |
| [MapContext.initMarkerCluster](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/MapContext.initMarkerCluster.html) | 初始化点聚合的配置，未调用时采用默认配置 | 是 |
| [MapContext.moveAlong](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/MapContext.moveAlong.html) | 沿指定路径移动 `marker`，用于轨迹回放等场景 | 是 |
| [MapContext.moveToLocation](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/MapContext.moveToLocation.html) | 将地图中心移置当前定位点，此时需设置地图组件 show-location 为true | 是 |
| [MapContext.on](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/MapContext.on.html) | 监听地图事件 | 是 |
| [MapContext.openMapApp](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/MapContext.openMapApp.html) | 拉起地图 APP 选择导航 | 否[2] |
| [MapContext.removeArc](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/MapContext.removeArc.html) | 删除弧线 | 是 |
| [MapContext.removeCustomLayer](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/MapContext.removeCustomLayer.html) | 移除个性化图层 | 是 |
| [MapContext.removeGroundOverlay](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/MapContext.removeGroundOverlay.html) | 移除自定义图片图层 | 是 |
| [MapContext.removeMarkers](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/MapContext.removeMarkers.html) | 移除 marker | 是 |
| [MapContext.removeVisualLayer](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/MapContext.removeVisualLayer.html) | 移除可视化图层 | 是 |
| [MapContext.setBoundary](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/MapContext.setBoundary.html) | 限制地图的显示范围 | 是 |
| [MapContext.setCenterOffset](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/MapContext.setCenterOffset.html) | 设置地图中心点偏移，向后向下为增长，屏幕比例范围(0.25~0.75)，默认偏移为[0.5, 0.5] | 是 |
| [MapContext.setLocMarkerIcon](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/MapContext.setLocMarkerIcon.html) | 设置定位点图标，支持网络路径、本地路径、代码包路径 | 是 |
| [MapContext.toScreenLocation](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/MapContext.toScreenLocation.html) | 获取经纬度对应的屏幕坐标，坐标原点为地图左上角 | 是 |
| [MapContext.translateMarker](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/MapContext.translateMarker.html) | 平移 marker，带动画 | 是 |
| [MapContext.updateGroundOverlay](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/MapContext.updateGroundOverlay.html) | 更新自定义图片图层 | 是 |

### [#](#图片) 图片

- 图片、音视频、相机、相册、录音等多媒体相关 JSAPI 依赖扩展 SDK 「Media SDK」 ,开发者需在项目中的 `project.miniapp.json` 配置勾选对应的 SDK 方可生效；
- 注意：在 iOS SDK >= 1.3.11 以及 开发者工具版本 >= 1.06.2405102，iOS Media SDK 已经被拆分为：Audio SDK、Video SDK、Image SDK、Camera SDK，开发者需按需勾选
- wx.previewMedia：iOS SDK >= 1.5.2 且需勾选 Video SDK；Android SDK >= 1.5.9 且需勾选 media sdk

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.saveImageToPhotosAlbum](https://developers.weixin.qq.com/miniprogram/dev/api/media/image/wx.saveImageToPhotosAlbum.html) | 保存图片到系统相册 | 是 |
| [wx.previewMedia](diffapi/previewMedia) | 预览图片和视频 | 已支持，但参数有差异 |
| [wx.previewImage](https://developers.weixin.qq.com/miniprogram/dev/api/media/image/wx.previewImage.html) | 在新页面中全屏预览图片 | 是[2]，长按识别功能暂时还不支持 |
| [wx.getImageInfo](https://developers.weixin.qq.com/miniprogram/dev/api/media/image/wx.getImageInfo.html) | 获取图片信息 | 是 |
| [wx.editImage](https://developers.weixin.qq.com/miniprogram/dev/api/media/image/wx.editImage.html) | 编辑图片接口 | 否[2] |
| [wx.cropImage](https://developers.weixin.qq.com/miniprogram/dev/api/media/image/wx.cropImage.html) | 裁剪图片接口 | 是，Android SDK >=1.5.6；iOS SDK >=1.5.12 |
| [wx.compressImage](https://developers.weixin.qq.com/miniprogram/dev/api/media/image/wx.compressImage.html) | 压缩图片接口，可选压缩质量 | 是 |
| [wx.chooseMessageFile](https://developers.weixin.qq.com/miniprogram/dev/api/media/image/wx.chooseMessageFile.html) | 从客户端会话选择文件 | 否[4]，可使用[wx.miniapp.chooseFile](miniapp/chooseFile)代替 |
| [wx.chooseImage](https://developers.weixin.qq.com/miniprogram/dev/api/media/image/wx.chooseImage.html) | 从本地相册选择图片或使用相机拍照 | 是，已不维护；建议使用wx.chooseMedia |

### [#](#视频) 视频

- 图片、音视频、相机、相册、录音等多媒体相关 JSAPI 依赖扩展 SDK 「Media SDK」 ,开发者需在项目中的 `project.miniapp.json` 配置勾选对应的 SDK 方可生效；
- 注意：在 iOS SDK >= 1.3.11 以及 开发者工具版本 >= 1.06.2405102，iOS Media SDK 已经被拆分为：Audio SDK、Video SDK、Image SDK、Camera SDK，开发者需按需勾选
- 补充：iOS 应用中，如果使用`wx.chooseMedia` 则必须勾选 Video SDK
- wx.compressVideo：Android SDK >= 1.4.13；iOS SDK >= 1.5.4
- wx.getVideoInfo：iOS SDK >= 1.5.4；

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.saveVideoToPhotosAlbum](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/wx.saveVideoToPhotosAlbum.html) | 保存视频到系统相册 | 是 |
| [wx.getVideoInfo](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/wx.getVideoInfo.html) | 获取视频详细信息 | 是 |
| [wx.createVideoContext](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/wx.createVideoContext.html) | 创建 [video](https://developers.weixin.qq.com/miniprogram/dev/component/video.html) 上下文 [VideoContext](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/VideoContext.html) 对象 | 是 |
| [wx.compressVideo](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/wx.compressVideo.html) | 压缩视频接口 | 是 |
| wx.openVideoEditor | 打开视频编辑器 | 否，但是有对应的解决方案，详情可查看[donut-ugc-editor](https://cloud.tencent.com/document/product/584/118710) |
| [wx.chooseVideo](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/wx.chooseVideo.html) | 拍摄视频或从手机相册中选视频 | 是 |
| [wx.chooseMedia](diffapi/chooseMedia) | 拍摄或从手机相册中选择图片或视频（需查看接口文档进行权限配置方可使用） | 是[2] |

### [#](#音频) 音频

- 图片、音视频、相机、相册、录音等多媒体相关 JSAPI 依赖扩展 SDK 「Media SDK」 ,开发者需在项目中的 `project.miniapp.json` 配置勾选对应的 SDK 方可生效；
- 注意：在 iOS SDK >= 1.3.11 以及 开发者工具版本 >= 1.06.2405102，iOS Media SDK 已经被拆分为：Audio SDK、Video SDK、Image SDK、Camera SDK，开发者需按需勾选

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.stopVoice](https://developers.weixin.qq.com/miniprogram/dev/api/media/audio/wx.stopVoice.html) | 结束播放语音 | 是 |
| [wx.setInnerAudioOption](https://developers.weixin.qq.com/miniprogram/dev/api/media/audio/wx.setInnerAudioOption.html) | 设置 [InnerAudioContext](https://developers.weixin.qq.com/miniprogram/dev/api/media/audio/InnerAudioContext.html) 的播放选项 | 是 |
| [wx.playVoice](https://developers.weixin.qq.com/miniprogram/dev/api/media/audio/wx.playVoice.html) | 开始播放语音 | 是 |
| [wx.pauseVoice](https://developers.weixin.qq.com/miniprogram/dev/api/media/audio/wx.pauseVoice.html) | 暂停正在播放的语音 | 是 |
| [wx.getAvailableAudioSources](https://developers.weixin.qq.com/miniprogram/dev/api/media/audio/wx.getAvailableAudioSources.html) | 获取当前支持的音频输入源 | 是 |
| [wx.createWebAudioContext](https://developers.weixin.qq.com/miniprogram/dev/api/media/audio/wx.createWebAudioContext.html) | 创建 [WebAudioContext](https://developers.weixin.qq.com/miniprogram/dev/api/media/audio/WebAudioContext.html) | 是 |
| [wx.createMediaAudioPlayer](https://developers.weixin.qq.com/miniprogram/dev/api/media/audio/wx.createMediaAudioPlayer.html) | 创建媒体音频播放器对象 [MediaAudioPlayer](https://developers.weixin.qq.com/miniprogram/dev/api/media/audio/MediaAudioPlayer.html) 对象，可用于播放视频解码器 [VideoDecoder](https://developers.weixin.qq.com/miniprogram/dev/api/media/video-decoder/VideoDecoder.html) 输出的音频 | 是 |
| [wx.createInnerAudioContext](https://developers.weixin.qq.com/miniprogram/dev/api/media/audio/wx.createInnerAudioContext.html) | 创建内部 [audio](https://developers.weixin.qq.com/miniprogram/dev/component/audio.html) 上下文 [InnerAudioContext](https://developers.weixin.qq.com/miniprogram/dev/api/media/audio/InnerAudioContext.html) 对象 | 是 |
| [wx.createAudioContext](https://developers.weixin.qq.com/miniprogram/dev/api/media/audio/wx.createAudioContext.html) | 创建 [audio](https://developers.weixin.qq.com/miniprogram/dev/component/audio.html) 上下文 [AudioContext](https://developers.weixin.qq.com/miniprogram/dev/api/media/audio/AudioContext.html) 对象 | 是 |

### [#](#背景音频) 背景音频

- 图片、音视频、相机、相册、录音等多媒体相关 JSAPI 依赖扩展 SDK 「Media SDK」 ,开发者需在项目中的 `project.miniapp.json` 配置勾选对应的 SDK 方可生效；
- 注意：在 iOS SDK >= 1.3.11 以及 开发者工具版本 >= 1.06.2405102，iOS Media SDK 已经被拆分为：Audio SDK、Video SDK、Image SDK、Camera SDK，开发者需按需勾选

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.stopBackgroundAudio](https://developers.weixin.qq.com/miniprogram/dev/api/media/background-audio/wx.stopBackgroundAudio.html) | 停止播放音乐 | 是 |
| [wx.seekBackgroundAudio](https://developers.weixin.qq.com/miniprogram/dev/api/media/background-audio/wx.seekBackgroundAudio.html) | 控制音乐播放进度 | 是 |
| [wx.playBackgroundAudio](https://developers.weixin.qq.com/miniprogram/dev/api/media/background-audio/wx.playBackgroundAudio.html) | 使用后台播放器播放音乐 | 是 |
| [wx.pauseBackgroundAudio](https://developers.weixin.qq.com/miniprogram/dev/api/media/background-audio/wx.pauseBackgroundAudio.html) | 暂停播放音乐 | 是 |
| [wx.onBackgroundAudioStop](https://developers.weixin.qq.com/miniprogram/dev/api/media/background-audio/wx.onBackgroundAudioStop.html) | 监听音乐停止事件 | 是 |
| [wx.onBackgroundAudioPlay](https://developers.weixin.qq.com/miniprogram/dev/api/media/background-audio/wx.onBackgroundAudioPlay.html) | 监听音乐播放事件 | 是 |
| [wx.onBackgroundAudioPause](https://developers.weixin.qq.com/miniprogram/dev/api/media/background-audio/wx.onBackgroundAudioPause.html) | 监听音乐暂停事件 | 是 |
| [wx.getBackgroundAudioPlayerState](https://developers.weixin.qq.com/miniprogram/dev/api/media/background-audio/wx.getBackgroundAudioPlayerState.html) | 获取后台音乐播放状态 | 是 |
| [wx.getBackgroundAudioManager](diffapi/getBackgroundAudioManager) | 获取**全局唯一**的[背景音频管理器](https://developers.weixin.qq.com/miniprogram/dev/api/media/background-audio/BackgroundAudioManager.html) | 是 |

### [#](#实时音视频) 实时音视频

- 使用 live-player 和 live-pusher 组件需要勾选 「Live SDK」（如果开发者工具上没看到该扩展 SDK ，请将开发者工具升级到最新）
- 且 Android SDK 需 ≥ 1.2.9 ； iOS SDK 需 >= 1.6.3
- 以及 iOS 端使用「Live SDK」时，还需配置 LiveLicenseUrl 和 LiveLicenseKey,详细操作可查看<https://cloud.tencent.com/document/product/454/34750>,即该能力依赖腾讯云的 SDK ，需要按照文档进行配置
  ![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202503170957973.png)

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.createLivePusherContext](https://developers.weixin.qq.com/miniprogram/dev/api/media/live/wx.createLivePusherContext.html) | 创建 [live-pusher](https://developers.weixin.qq.com/miniprogram/dev/component/live-pusher.html) 上下文 [LivePusherContext](https://developers.weixin.qq.com/miniprogram/dev/api/media/live/LivePusherContext.html) 对象 | 是 |
| [wx.createLivePlayerContext](https://developers.weixin.qq.com/miniprogram/dev/api/media/live/wx.createLivePlayerContext.html) | 创建 [live-player](https://developers.weixin.qq.com/miniprogram/dev/component/live-pusher.html) 上下文 [LivePlayerContext](https://developers.weixin.qq.com/miniprogram/dev/api/media/live/LivePlayerContext.html) 对象 | 是 |

### [#](#录音) 录音

- 图片、音视频、相机、相册、录音等多媒体相关 JSAPI 依赖扩展 SDK 「Media SDK」 ,开发者需在项目中的 `project.miniapp.json` 配置勾选对应的 「Media SDK」 方可生效；
- RecorderManager 相关接口还需要在 `project.miniapp.json` 配置下列权限方可生效
  - Android：「Android 权限描述配置」 -> 「允许应用程序录制音频」
  - iOS：「隐私信息访问许可描述」 -> 「麦克风」

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F%E4%BC%81%E4%B8%9A%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_2b38bf09-fadd-4ef5-ba16-ebbac1187f21.png) ![](https://res.wx.qq.com/op_res/LbYQe0g9Ht0wgUr3Y6wWv8R3hgAND9QdpzHkof9nDa73xUvAZ_Lgh3iLmRYLg4QqLutr9gHPnGkfdANCPO6J-A)

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.stopRecord](https://developers.weixin.qq.com/miniprogram/dev/api/media/recorder/wx.stopRecord.html) | 停止录音 | 是 |
| [wx.startRecord](https://developers.weixin.qq.com/miniprogram/dev/api/media/recorder/wx.startRecord.html) | 开始录音 | 是 |
| [wx.getRecorderManager](https://developers.weixin.qq.com/miniprogram/dev/api/media/recorder/wx.getRecorderManager.html) | 获取**全局唯一**的录音管理器 [RecorderManager](https://developers.weixin.qq.com/miniprogram/dev/api/media/recorder/RecorderManager.html) | 是 |

### [#](#相机) 相机

- 图片、音视频、相机、相册、录音等多媒体相关 JSAPI 依赖扩展 SDK 「Media SDK」 ,开发者需在项目中的 `project.miniapp.json` 配置勾选对应的 SDK 方可生效；

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.createCameraContext](https://developers.weixin.qq.com/miniprogram/dev/api/media/camera/wx.createCameraContext.html) | 创建 [camera](https://developers.weixin.qq.com/miniprogram/dev/component/camera.html) 上下文 [CameraContext](https://developers.weixin.qq.com/miniprogram/dev/api/media/camera/CameraContext.html) 对象 | 是 |

### [#](#富文本) 富文本

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [EditorContext](https://developers.weixin.qq.com/miniprogram/dev/api/media/editor/EditorContext.html) | EditorContext 实例 | 是 |

#### [#](#EditorContext) EditorContext

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [EditorContext.blur](https://developers.weixin.qq.com/miniprogram/dev/api/media/editor/EditorContext.blur.html) | 编辑器失焦，同时收起键盘 | 是 |
| [EditorContext.clear](https://developers.weixin.qq.com/miniprogram/dev/api/media/editor/EditorContext.clear.html) | 清空编辑器内容 | 是 |
| [EditorContext.format](https://developers.weixin.qq.com/miniprogram/dev/api/media/editor/EditorContext.format.html) | 修改样式 | 是 |
| [EditorContext.getContents](https://developers.weixin.qq.com/miniprogram/dev/api/media/editor/EditorContext.getContents.html) | 获取编辑器内容 | 是 |
| [EditorContext.getSelectionText](https://developers.weixin.qq.com/miniprogram/dev/api/media/editor/EditorContext.getSelectionText.html) | 获取编辑器已选区域内的纯文本内容 | 是 |
| [EditorContext.insertDivider](https://developers.weixin.qq.com/miniprogram/dev/api/media/editor/EditorContext.insertDivider.html) | 插入分割线 | 是 |
| [EditorContext.insertImage](https://developers.weixin.qq.com/miniprogram/dev/api/media/editor/EditorContext.insertImage.html) | 插入图片 | 是 |
| [EditorContext.insertText](https://developers.weixin.qq.com/miniprogram/dev/api/media/editor/EditorContext.insertText.html) | 覆盖当前选区，设置一段文本 | 是 |
| [EditorContext.redo](https://developers.weixin.qq.com/miniprogram/dev/api/media/editor/EditorContext.redo.html) | 恢复 | 是 |
| [EditorContext.removeFormat](https://developers.weixin.qq.com/miniprogram/dev/api/media/editor/EditorContext.removeFormat.html) | 清除当前选区的样式 | 是 |
| [EditorContext.scrollIntoView](https://developers.weixin.qq.com/miniprogram/dev/api/media/editor/EditorContext.scrollIntoView.html) | 使得编辑器光标处滚动到窗口可视区域内 | 是 |
| [EditorContext.setContents](https://developers.weixin.qq.com/miniprogram/dev/api/media/editor/EditorContext.setContents.html) | 初始化编辑器内容，html 和 delta 同时存在时仅 delta 生效 | 是 |
| [EditorContext.undo](https://developers.weixin.qq.com/miniprogram/dev/api/media/editor/EditorContext.undo.html) | 撤销 | 是 |

### [#](#音视频合成) 音视频合成

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.createMediaContainer](https://developers.weixin.qq.com/miniprogram/dev/api/media/video-processing/wx.createMediaContainer.html) | 创建[音视频处理容器](https://developers.weixin.qq.com/miniprogram/dev/api/media/video-processing/MediaContainer.html)，最终可将容器中的轨道合成一个视频 | 否[2] |

### [#](#实时语音) 实时语音

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.updateVoIPChatMuteConfig](https://developers.weixin.qq.com/miniprogram/dev/api/media/voip/wx.updateVoIPChatMuteConfig.html) | 更新实时语音静音设置 | 否[4] |
| [wx.subscribeVoIPVideoMembers](https://developers.weixin.qq.com/miniprogram/dev/api/media/voip/wx.subscribeVoIPVideoMembers.html) | 订阅视频画面成员 | 否[4] |
| [wx.setEnable1v1Chat](https://developers.weixin.qq.com/miniprogram/dev/api/media/voip/wx.setEnable1v1Chat.html) | 开启双人通话 | 否[4] |
| [wx.onVoIPVideoMembersChanged](https://developers.weixin.qq.com/miniprogram/dev/api/media/voip/wx.onVoIPVideoMembersChanged.html) | 监听实时语音通话成员视频状态变化事件 | 否[4] |
| [wx.onVoIPChatStateChanged](https://developers.weixin.qq.com/miniprogram/dev/api/media/voip/wx.onVoIPChatStateChanged.html) | 监听房间状态变化事件 | 否[4] |
| [wx.onVoIPChatSpeakersChanged](https://developers.weixin.qq.com/miniprogram/dev/api/media/voip/wx.onVoIPChatSpeakersChanged.html) | 监听实时语音通话成员通话状态变化事件 | 否[4] |
| [wx.onVoIPChatMembersChanged](https://developers.weixin.qq.com/miniprogram/dev/api/media/voip/wx.onVoIPChatMembersChanged.html) | 监听实时语音通话成员在线状态变化事件 | 否[4] |
| [wx.onVoIPChatInterrupted](https://developers.weixin.qq.com/miniprogram/dev/api/media/voip/wx.onVoIPChatInterrupted.html) | 监听被动断开实时语音通话事件 | 否[4] |
| [wx.offVoIPVideoMembersChanged](https://developers.weixin.qq.com/miniprogram/dev/api/media/voip/wx.offVoIPVideoMembersChanged.html) | 移除实时语音通话成员视频状态变化事件的监听函数 | 否[4] |
| [wx.offVoIPChatStateChanged](https://developers.weixin.qq.com/miniprogram/dev/api/media/voip/wx.offVoIPChatStateChanged.html) | 移除房间状态变化事件的监听函数 | 否[4] |
| [wx.offVoIPChatSpeakersChanged](https://developers.weixin.qq.com/miniprogram/dev/api/media/voip/wx.offVoIPChatSpeakersChanged.html) | 移除实时语音通话成员通话状态变化事件的监听函数 | 否[4] |
| [wx.offVoIPChatMembersChanged](https://developers.weixin.qq.com/miniprogram/dev/api/media/voip/wx.offVoIPChatMembersChanged.html) | 移除实时语音通话成员在线状态变化事件的监听函数 | 否[4] |
| [wx.offVoIPChatInterrupted](https://developers.weixin.qq.com/miniprogram/dev/api/media/voip/wx.offVoIPChatInterrupted.html) | 移除被动断开实时语音通话事件的监听函数 | 否[4] |
| [wx.joinVoIPChat](https://developers.weixin.qq.com/miniprogram/dev/api/media/voip/wx.joinVoIPChat.html) | 加入 (创建) 实时语音通话 | 否[4] |
| [wx.join1v1Chat](https://developers.weixin.qq.com/miniprogram/dev/api/media/voip/wx.join1v1Chat.html) | 加入（创建）双人通话 | 否[4] |
| [wx.exitVoIPChat](https://developers.weixin.qq.com/miniprogram/dev/api/media/voip/wx.exitVoIPChat.html) | 退出（销毁）实时语音通话 | 否[4] |

### [#](#画面录制器) 画面录制器

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.createMediaRecorder](https://developers.weixin.qq.com/miniprogram/dev/api/media/media-recorder/wx.createMediaRecorder.html) | 创建 [WebGL 画面录制器](https://developers.weixin.qq.com/miniprogram/dev/api/media/media-recorder/MediaRecorder.html)，可逐帧录制在 WebGL 上渲染的画面并导出视频文件 | 否[2] |

### [#](#视频解码器) 视频解码器

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.createVideoDecoder](https://developers.weixin.qq.com/miniprogram/dev/api/media/video-decoder/wx.createVideoDecoder.html) | 创建[视频解码器](https://developers.weixin.qq.com/miniprogram/dev/api/media/video-decoder/VideoDecoder.html)，可逐帧获取解码后的数据 | 否[2] |

## [#](#位置) 位置

- 如下支持的位置相关接口能力，需配置 LBS SDK ，且需前往腾讯位置服务平台注册开发者账号并创建应用 Key，详情可查看[位置服务使用指南](../handbook/devtools/lbs)
- `wx.startLocationUpdateBackground` 在 iOS 应用中使用前，需前往 `project.miniapp.json` 开启 「Location updates of Background Modes」，并且还需要填写对应的隐私信息许可描述，如下图

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202406221530022.png)

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.stopLocationUpdate](https://developers.weixin.qq.com/miniprogram/dev/api/location/wx.stopLocationUpdate.html) | 关闭监听实时位置变化，前后台都停止消息接收 | 是 |
| [wx.startLocationUpdateBackground](https://developers.weixin.qq.com/miniprogram/dev/api/location/wx.startLocationUpdateBackground.html) | 开启小程序进入前后台时均接收位置消息，需引导用户开启[授权](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/authorize) | 是 |
| [wx.startLocationUpdate](https://developers.weixin.qq.com/miniprogram/dev/api/location/wx.startLocationUpdate.html) | 开启小程序进入前台时接收位置消息 | 是 |
| [wx.openLocation](https://developers.weixin.qq.com/miniprogram/dev/api/location/wx.openLocation.html) | 使用微信内置地图查看位置 | 是 |
| [wx.onLocationChangeError](https://developers.weixin.qq.com/miniprogram/dev/api/location/wx.onLocationChangeError.html) | 监听持续定位接口返回失败时触发 | 是 |
| [wx.onLocationChange](https://developers.weixin.qq.com/miniprogram/dev/api/location/wx.onLocationChange.html) | 监听实时地理位置变化事件，需结合 wx.startLocationUpdateBackground、wx.startLocationUpdate 使用 | 是 |
| [wx.offLocationChangeError](https://developers.weixin.qq.com/miniprogram/dev/api/location/wx.offLocationChangeError.html) | 移除持续定位接口返回失败时触发 | 是 |
| [wx.offLocationChange](https://developers.weixin.qq.com/miniprogram/dev/api/location/wx.offLocationChange.html) | 移除实时地理位置变化事件的监听函数 | 是 |
| [wx.getLocation](https://developers.weixin.qq.com/miniprogram/dev/api/location/wx.getLocation.html) | 获取当前的地理位置、速度 | 是 |
| [wx.getFuzzyLocation](https://developers.weixin.qq.com/miniprogram/dev/api/location/wx.getFuzzyLocation.html) | 获取当前的模糊地理位置 | 否[2] |
| [wx.choosePoi](https://developers.weixin.qq.com/miniprogram/dev/api/location/wx.choosePoi.html) | 打开 POI 列表选择位置，支持模糊定位（精确到市）和精确定位混选 | 否[2] |
| [wx.chooseLocation](https://developers.weixin.qq.com/miniprogram/dev/api/location/wx.chooseLocation.html) | 打开地图选择位置 | 是[2] |

## [#](#文件) 文件

wx.openDocument 补充说明

- 在 Android 端使用该接口实现在应用内部预览，需在 project.miniapp.json 中将 XWEB 扩展 SDK 勾上，并且 Android SDK 版本需大于或等于 1.4.10
- 此外该接口在 Android 端使用时新增入参 `openInternal` 用于控制是否应用内打开文件（仅当开启 xweb 时生效）；该值的枚举值为 `true` 和 `false`

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.saveFileToDisk](https://developers.weixin.qq.com/miniprogram/dev/api/file/wx.saveFileToDisk.html) | 保存文件系统的文件到用户磁盘，仅在 PC 端支持 | 是 |
| [wx.openDocument](https://developers.weixin.qq.com/miniprogram/dev/api/file/wx.openDocument.html) | 新开页面打开文档 | 是 |
| [wx.getFileSystemManager](https://developers.weixin.qq.com/miniprogram/dev/api/file/wx.getFileSystemManager.html) | 获取全局唯一的[文件管理器](https://developers.weixin.qq.com/miniprogram/dev/api/file/FileSystemManager.html) | 是 |
| wx.saveFile | 保存文件到本地。wx.saveFile 即将废弃，请使用 [wx.getFileSystemManager().saveFile](https://developers.weixin.qq.com/miniprogram/dev/api/file/FileSystemManager.saveFile.html) | 是 |
| wx.removeSavedFile | 删除本地缓存文件。wx.removeSavedFile 即将废弃，请使用 [wx.getFileSystemManager().removeSavedFile](https://developers.weixin.qq.com/miniprogram/dev/api/file/FileSystemManager.removeSavedFile.html) | 是 |
| wx.getSavedFileList | 获取该小程序下已保存的本地缓存文件列表。wx.getSavedFileList 即将废弃，请使用 [wx.getFileSystemManager().getSavedFileList](https://developers.weixin.qq.com/miniprogram/dev/api/file/FileSystemManager.getSavedFileList.html) | 是 |
| wx.getSavedFileInfo | 获取本地文件的文件信息。wx.getSavedFileInfo 即将废弃，请使用 [wx.getFileSystemManager().getFileInfo](https://developers.weixin.qq.com/miniprogram/dev/api/file/FileSystemManager.getFileInfo.html) | 是 |
| wx.getFileInfo | 获取文件信息。wx.getFileInfo 即将废弃，请使用 [wx.getFileSystemManager().getFileInfo](https://developers.weixin.qq.com/miniprogram/dev/api/file/FileSystemManager.getFileInfo.html) | 是 |

### [#](#蓝牙-通用) 蓝牙-通用

- 蓝牙相关 JSAPI 依赖扩展 SDK 「Bluetooth SDK」 ,开发者需在项目中的 `project.miniapp.json` 配置勾选对应的 SDK 方可生效；
- 系统要求，手机上需要开启地理位置权限后才可以搜索到蓝牙

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.stopBluetoothDevicesDiscovery](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth/wx.stopBluetoothDevicesDiscovery.html) | 停止搜寻附近的蓝牙外围设备 | 是 |
| [wx.startBluetoothDevicesDiscovery](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth/wx.startBluetoothDevicesDiscovery.html) | 开始搜寻附近的蓝牙外围设备 | 是 |
| [wx.openBluetoothAdapter](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth/wx.openBluetoothAdapter.html) | 初始化蓝牙模块 | 是 |
| [wx.onBluetoothDeviceFound](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth/wx.onBluetoothDeviceFound.html) | 监听搜索到新设备的事件 | 是 |
| [wx.onBluetoothAdapterStateChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth/wx.onBluetoothAdapterStateChange.html) | 监听蓝牙适配器状态变化事件 | 是 |
| [wx.offBluetoothDeviceFound](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth/wx.offBluetoothDeviceFound.html) | 移除搜索到新设备的事件的监听函数 | 是 |
| [wx.offBluetoothAdapterStateChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth/wx.offBluetoothAdapterStateChange.html) | 移除蓝牙适配器状态变化事件的监听函数 | 是 |
| [wx.makeBluetoothPair](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth/wx.makeBluetoothPair.html) | 蓝牙配对接口，仅安卓支持 | 是 |
| [wx.isBluetoothDevicePaired](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth/wx.isBluetoothDevicePaired.html) | 查询蓝牙设备是否配对，仅安卓支持 | 是 |
| [wx.getConnectedBluetoothDevices](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth/wx.getConnectedBluetoothDevices.html) | 根据主服务 UUID 获取已连接的蓝牙设备 | 是 |
| [wx.getBluetoothDevices](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth/wx.getBluetoothDevices.html) | 获取在蓝牙模块生效期间所有搜索到的蓝牙设备 | 是 |
| [wx.getBluetoothAdapterState](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth/wx.getBluetoothAdapterState.html) | 获取本机蓝牙适配器状态 | 是 |
| [wx.closeBluetoothAdapter](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth/wx.closeBluetoothAdapter.html) | 关闭蓝牙模块 | 是 |

### [#](#蓝牙-低功耗中心设备) 蓝牙-低功耗中心设备

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.writeBLECharacteristicValue](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth-ble/wx.writeBLECharacteristicValue.html) | 向蓝牙低功耗设备特征值中写入二进制数据 | 是 |
| [wx.setBLEMTU](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth-ble/wx.setBLEMTU.html) | 协商设置蓝牙低功耗的最大传输单元 (Maximum Transmission Unit, MTU) | 是 |
| [wx.readBLECharacteristicValue](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth-ble/wx.readBLECharacteristicValue.html) | 读取蓝牙低功耗设备特征值的二进制数据 | 是 |
| [wx.onBLEMTUChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth-ble/wx.onBLEMTUChange.html) | 监听蓝牙低功耗的最大传输单元变化事件（仅安卓触发） | 是 |
| [wx.onBLEConnectionStateChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth-ble/wx.onBLEConnectionStateChange.html) | 监听蓝牙低功耗连接状态改变事件 | 是 |
| [wx.onBLECharacteristicValueChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth-ble/wx.onBLECharacteristicValueChange.html) | 监听蓝牙低功耗设备的特征值变化事件 | 是 |
| [wx.offBLEMTUChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth-ble/wx.offBLEMTUChange.html) | 移除蓝牙低功耗的最大传输单元变化事件的监听函数 | 是 |
| [wx.offBLEConnectionStateChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth-ble/wx.offBLEConnectionStateChange.html) | 移除蓝牙低功耗连接状态改变事件的监听函数 | 是 |
| [wx.offBLECharacteristicValueChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth-ble/wx.offBLECharacteristicValueChange.html) | 移除蓝牙低功耗设备的特征值变化事件的监听函数 | 是 |
| [wx.notifyBLECharacteristicValueChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth-ble/wx.notifyBLECharacteristicValueChange.html) | 启用蓝牙低功耗设备特征值变化时的 notify 功能，订阅特征 | 是 |
| [wx.getBLEMTU](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth-ble/wx.getBLEMTU.html) | 获取蓝牙低功耗的最大传输单元 | 是 |
| [wx.getBLEDeviceServices](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth-ble/wx.getBLEDeviceServices.html) | 获取蓝牙低功耗设备所有服务 (service) | 是 |
| [wx.getBLEDeviceRSSI](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth-ble/wx.getBLEDeviceRSSI.html) | 获取蓝牙低功耗设备的信号强度 (Received Signal Strength Indication, RSSI) | 是 |
| [wx.getBLEDeviceCharacteristics](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth-ble/wx.getBLEDeviceCharacteristics.html) | 获取蓝牙低功耗设备某个服务中所有特征 (characteristic) | 是 |
| [wx.createBLEConnection](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth-ble/wx.createBLEConnection.html) | 连接蓝牙低功耗设备 | 是 |
| [wx.closeBLEConnection](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth-ble/wx.closeBLEConnection.html) | 断开与蓝牙低功耗设备的连接 | 是 |

### [#](#蓝牙-低功耗外围设备) 蓝牙-低功耗外围设备

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.onBLEPeripheralConnectionStateChanged](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth-peripheral/wx.onBLEPeripheralConnectionStateChanged.html) | 监听当前外围设备被连接或断开连接事件 | 是 |
| [wx.offBLEPeripheralConnectionStateChanged](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth-peripheral/wx.offBLEPeripheralConnectionStateChanged.html) | 移除当前外围设备被连接或断开连接事件的监听函数 | 是 |
| [wx.createBLEPeripheralServer](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth-peripheral/wx.createBLEPeripheralServer.html) | 建立本地作为[蓝牙低功耗外围设备的服务端](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth-peripheral/BLEPeripheralServer.html)，可创建多个 | 是 |

### [#](#蓝牙-信标-Beacon) 蓝牙-信标(Beacon)

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.stopBeaconDiscovery](https://developers.weixin.qq.com/miniprogram/dev/api/device/ibeacon/wx.stopBeaconDiscovery.html) | 停止搜索附近的 Beacon 设备 | 是 |
| [wx.startBeaconDiscovery](https://developers.weixin.qq.com/miniprogram/dev/api/device/ibeacon/wx.startBeaconDiscovery.html) | 开始搜索附近的 Beacon 设备 | 是 |
| [wx.onBeaconUpdate](https://developers.weixin.qq.com/miniprogram/dev/api/device/ibeacon/wx.onBeaconUpdate.html) | 监听 Beacon 设备更新事件，仅能注册一个监听 | 是 |
| [wx.onBeaconServiceChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/ibeacon/wx.onBeaconServiceChange.html) | 监听 Beacon 服务状态变化事件，仅能注册一个监听 | 是 |
| [wx.offBeaconUpdate](https://developers.weixin.qq.com/miniprogram/dev/api/device/ibeacon/wx.offBeaconUpdate.html) | 移除 Beacon 设备更新事件的监听函数 | 是 |
| [wx.offBeaconServiceChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/ibeacon/wx.offBeaconServiceChange.html) | 移除 Beacon 服务状态变化事件的监听函数 | 是 |
| [wx.getBeacons](https://developers.weixin.qq.com/miniprogram/dev/api/device/ibeacon/wx.getBeacons.html) | 获取所有已搜索到的 Beacon 设备 | 是 |
| [BeaconInfo](https://developers.weixin.qq.com/miniprogram/dev/api/device/ibeacon/BeaconInfo.html) | Beacon 设备 | 是 |

### [#](#近场通讯（NFC）) 近场通讯（NFC）

- NFC JSAPI 依赖扩展 SDK 「NFC SDK」 ,开发者需在项目中的 `project.miniapp.json` 配置勾选方可生效
- Android SDK >= 1.5.6

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.getNFCAdapter](https://developers.weixin.qq.com/miniprogram/dev/api/device/nfc/wx.getNFCAdapter.html) | 获取 NFC 实例 | 是 |

### [#](#Wi-Fi) Wi-Fi

- 下方 WIFI 相关的 JSAPI 依赖扩展 SDK 「Network SDK」 ,开发者需在项目中的 `project.miniapp.json` 配置勾选对应的 SDK 方可生效；
- 注意：Android 和 iOS 的扩展 SDK 有所区别，详情查看 `project.miniapp.json`
- 注意：iOS 13 及以上系统，获取当前连接的 Wi-Fi 信息需要先获取系统定位权限，因此在 iOS 13 及以上系统使用此接口时，需要先调用`wx.getLocation`，触发定位权限申请的弹窗，待用户授权后才可以正常获取到 wifi 信息

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.stopWifi](https://developers.weixin.qq.com/miniprogram/dev/api/device/wifi/wx.stopWifi.html) | 关闭 Wi-Fi 模块 | 是 |
| [wx.startWifi](https://developers.weixin.qq.com/miniprogram/dev/api/device/wifi/wx.startWifi.html) | 初始化 Wi-Fi 模块 | 是 |
| [wx.setWifiList](https://developers.weixin.qq.com/miniprogram/dev/api/device/wifi/wx.setWifiList.html) | 设置 `wifiList` 中 AP 的相关信息 | 是 |
| [wx.onWifiConnected](https://developers.weixin.qq.com/miniprogram/dev/api/device/wifi/wx.onWifiConnected.html) | 监听连接上 Wi-Fi 的事件 | 是 |
| [wx.offWifiConnected](https://developers.weixin.qq.com/miniprogram/dev/api/device/wifi/wx.offWifiConnected.html) | 移除连接上 Wi-Fi 的事件的监听函数 | 是 |
| [wx.onGetWifiList](https://developers.weixin.qq.com/miniprogram/dev/api/device/wifi/wx.onGetWifiList.html) | 监听获取到 Wi-Fi 列表数据事件 | 是 |
| [wx.offGetWifiList](https://developers.weixin.qq.com/miniprogram/dev/api/device/wifi/wx.offGetWifiList.html) | 移除获取到 Wi-Fi 列表数据事件的监听函数 | 是 |
| [wx.onWifiConnectedWithPartialInfo](https://developers.weixin.qq.com/miniprogram/dev/api/device/wifi/wx.onWifiConnectedWithPartialInfo.html) | 监听连接上 Wi-Fi 的事件 | 否[2] |
| [wx.offWifiConnectedWithPartialInfo](https://developers.weixin.qq.com/miniprogram/dev/api/device/wifi/wx.offWifiConnectedWithPartialInfo.html) | 移除连接上 Wi-Fi 的事件的监听函数 | 否[2] |
| [wx.getWifiList](https://developers.weixin.qq.com/miniprogram/dev/api/device/wifi/wx.getWifiList.html) | 请求获取 Wi-Fi 列表 | 是 |
| [wx.getConnectedWifi](https://developers.weixin.qq.com/miniprogram/dev/api/device/wifi/wx.getConnectedWifi.html) | 获取已连接中的 Wi-Fi 信息 | 是 |
| [wx.connectWifi](https://developers.weixin.qq.com/miniprogram/dev/api/device/wifi/wx.connectWifi.html) | 连接 Wi-Fi | 是 |
| [WifiInfo](https://developers.weixin.qq.com/miniprogram/dev/api/device/wifi/WifiInfo.html) | Wifi 信息 | 是 |

### [#](#日历) 日历

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.addPhoneRepeatCalendar](https://developers.weixin.qq.com/miniprogram/dev/api/device/calendar/wx.addPhoneRepeatCalendar.html) | 向系统日历添加重复事件 | 是 |
| [wx.addPhoneCalendar](https://developers.weixin.qq.com/miniprogram/dev/api/device/calendar/wx.addPhoneCalendar.html) | 向系统日历添加事件 | 是 |

### [#](#联系人) 联系人

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.chooseContact](https://developers.weixin.qq.com/miniprogram/dev/api/device/contact/wx.chooseContact.html) | 拉起手机通讯录，选择联系人 | 是 |
| [wx.addPhoneContact](https://developers.weixin.qq.com/miniprogram/dev/api/device/contact/wx.addPhoneContact.html) | 添加手机通讯录联系人 | 是 |

### [#](#无障碍) 无障碍

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.checkIsOpenAccessibility](https://developers.weixin.qq.com/miniprogram/dev/api/device/accessibility/wx.checkIsOpenAccessibility.html) | 检测是否开启视觉无障碍功能 | 否[4] |

### [#](#电量) 电量

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.getBatteryInfoSync](https://developers.weixin.qq.com/miniprogram/dev/api/device/battery/wx.getBatteryInfoSync.html) | wx.getBatteryInfo 的同步版本 | 是 |
| [wx.getBatteryInfo](https://developers.weixin.qq.com/miniprogram/dev/api/device/battery/wx.getBatteryInfo.html) | 获取设备电量 | 是 |

### [#](#剪贴板) 剪贴板

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.setClipboardData](https://developers.weixin.qq.com/miniprogram/dev/api/device/clipboard/wx.setClipboardData.html) | 设置系统剪贴板的内容 | 是 |
| [wx.getClipboardData](https://developers.weixin.qq.com/miniprogram/dev/api/device/clipboard/wx.getClipboardData.html) | 获取系统剪贴板的内容 | 是 |

### [#](#NFC-主机卡模拟) NFC 主机卡模拟

- NFC JSAPI 依赖扩展 SDK 「NFC SDK」 ,开发者需在项目中的 `project.miniapp.json` 配置勾选方可生效
- Android SDK >= 1.5.6

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.stopHCE](https://developers.weixin.qq.com/miniprogram/dev/api/device/nfc-hce/wx.stopHCE.html) | 关闭 NFC 模块 | 是 |
| [wx.startHCE](https://developers.weixin.qq.com/miniprogram/dev/api/device/nfc-hce/wx.startHCE.html) | 初始化 NFC 模块 | 是 |
| [wx.sendHCEMessage](https://developers.weixin.qq.com/miniprogram/dev/api/device/nfc-hce/wx.sendHCEMessage.html) | 发送 NFC 消息 | 是 |
| [wx.onHCEMessage](https://developers.weixin.qq.com/miniprogram/dev/api/device/nfc-hce/wx.onHCEMessage.html) | 监听接收 NFC 设备消息事件 | 是 |
| [wx.offHCEMessage](https://developers.weixin.qq.com/miniprogram/dev/api/device/nfc-hce/wx.offHCEMessage.html) | 移除接收 NFC 设备消息事件的监听函数 | 是 |
| [wx.getHCEState](https://developers.weixin.qq.com/miniprogram/dev/api/device/nfc-hce/wx.getHCEState.html) | 判断当前设备是否支持 HCE 能力 | 是 |

### [#](#网络-2) 网络

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.onNetworkWeakChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/network/wx.onNetworkWeakChange.html) | 监听弱网状态变化事件 | 是 |
| [wx.onNetworkStatusChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/network/wx.onNetworkStatusChange.html) | 监听网络状态变化事件 | 是 |
| [wx.offNetworkWeakChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/network/wx.offNetworkWeakChange.html) | 移除弱网状态变化事件的监听函数 | 是 |
| [wx.offNetworkStatusChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/network/wx.offNetworkStatusChange.html) | 移除网络状态变化事件的监听函数 | 是 |
| [wx.getNetworkType](https://developers.weixin.qq.com/miniprogram/dev/api/device/network/wx.getNetworkType.html) | 获取网络类型 | 是 |
| [wx.getLocalIPAddress](https://developers.weixin.qq.com/miniprogram/dev/api/device/network/wx.getLocalIPAddress.html) | 获取局域网 IP 地址 | 否[2] |

### [#](#加密-2) 加密

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.getRandomValues](https://developers.weixin.qq.com/miniprogram/dev/api/device/crypto/wx.getRandomValues.html) | 获取密码学安全随机数 | 是 |

### [#](#屏幕) 屏幕

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.setVisualEffectOnCapture](https://developers.weixin.qq.com/miniprogram/dev/api/device/screen/wx.setVisualEffectOnCapture.html) | 设置截屏/录屏时屏幕表现，仅支持在 Android 端调用 | 否[2] |
| [wx.setScreenBrightness](https://developers.weixin.qq.com/miniprogram/dev/api/device/screen/wx.setScreenBrightness.html) | 设置屏幕亮度 | 是 |
| [wx.setKeepScreenOn](https://developers.weixin.qq.com/miniprogram/dev/api/device/screen/wx.setKeepScreenOn.html) | 设置是否保持常亮状态 | 是 |
| [wx.onUserCaptureScreen](https://developers.weixin.qq.com/miniprogram/dev/api/device/screen/wx.onUserCaptureScreen.html) | 监听用户主动截屏事件 | 是 |
| [wx.onScreenRecordingStateChanged](https://developers.weixin.qq.com/miniprogram/dev/api/device/screen/wx.onScreenRecordingStateChanged.html) | 监听用户录屏事件 | 是 |
| [wx.offUserCaptureScreen](https://developers.weixin.qq.com/miniprogram/dev/api/device/screen/wx.offUserCaptureScreen.html) | 用户主动截屏事件 | 是 |
| [wx.offScreenRecordingStateChanged](https://developers.weixin.qq.com/miniprogram/dev/api/device/screen/wx.offScreenRecordingStateChanged.html) | 移除用户录屏事件的监听函数 | 是 |
| [wx.getScreenRecordingState](https://developers.weixin.qq.com/miniprogram/dev/api/device/screen/wx.getScreenRecordingState.html) | 查询用户是否在录屏 | 是 |
| [wx.getScreenBrightness](https://developers.weixin.qq.com/miniprogram/dev/api/device/screen/wx.getScreenBrightness.html) | 获取屏幕亮度 | 是 |

### [#](#键盘) 键盘

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.onKeyboardHeightChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/keyboard/wx.onKeyboardHeightChange.html) | 监听键盘高度变化事件 | 是 |
| [wx.offKeyboardHeightChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/keyboard/wx.offKeyboardHeightChange.html) | 移除键盘高度变化事件的监听函数 | 是 |
| [wx.hideKeyboard](https://developers.weixin.qq.com/miniprogram/dev/api/device/keyboard/wx.hideKeyboard.html) | 在 input、textarea 等 focus 拉起键盘之后，手动调用此接口收起键盘 | 是 |
| [wx.getSelectedTextRange](https://developers.weixin.qq.com/miniprogram/dev/api/device/keyboard/wx.getSelectedTextRange.html) | 在 input、textarea 等 focus 之后，获取输入框的光标位置 | 是 |

### [#](#电话) 电话

注：此接口在 iOS 多端应用中使用需前往 `project.miniapp.json` 勾选「Others SDK」

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.makePhoneCall](https://developers.weixin.qq.com/miniprogram/dev/api/device/phone/wx.makePhoneCall.html) | 拨打电话 | 是 |

### [#](#加速计) 加速计

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.stopAccelerometer](https://developers.weixin.qq.com/miniprogram/dev/api/device/accelerometer/wx.stopAccelerometer.html) | 停止监听加速度数据 | 是 |
| [wx.startAccelerometer](https://developers.weixin.qq.com/miniprogram/dev/api/device/accelerometer/wx.startAccelerometer.html) | 开始监听加速度数据 | 是 |
| [wx.onAccelerometerChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/accelerometer/wx.onAccelerometerChange.html) | 监听加速度数据事件 | 是 |
| [wx.offAccelerometerChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/accelerometer/wx.offAccelerometerChange.html) | 移除加速度数据事件的监听函数 | 是 |

### [#](#罗盘) 罗盘

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.stopCompass](https://developers.weixin.qq.com/miniprogram/dev/api/device/compass/wx.stopCompass.html) | 停止监听罗盘数据 | 是 |
| [wx.startCompass](https://developers.weixin.qq.com/miniprogram/dev/api/device/compass/wx.startCompass.html) | 开始监听罗盘数据 | 是 |
| [wx.onCompassChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/compass/wx.onCompassChange.html) | 监听罗盘数据变化事件 | 是 |
| [wx.offCompassChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/compass/wx.offCompassChange.html) | 移除罗盘数据变化事件的监听函数 | 是 |

### [#](#设备方向) 设备方向

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.stopDeviceMotionListening](https://developers.weixin.qq.com/miniprogram/dev/api/device/motion/wx.stopDeviceMotionListening.html) | 停止监听设备方向的变化 | 是 |
| [wx.startDeviceMotionListening](https://developers.weixin.qq.com/miniprogram/dev/api/device/motion/wx.startDeviceMotionListening.html) | 开始监听设备方向的变化 | 是 |
| [wx.onDeviceMotionChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/motion/wx.onDeviceMotionChange.html) | 监听设备方向变化事件 | 是 |
| [wx.offDeviceMotionChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/motion/wx.offDeviceMotionChange.html) | 移除设备方向变化事件的监听函数 | 是 |

### [#](#内存) 内存

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.onMemoryWarning](https://developers.weixin.qq.com/miniprogram/dev/api/device/memory/wx.onMemoryWarning.html) | 监听内存不足告警事件 | 是 |
| [wx.offMemoryWarning](https://developers.weixin.qq.com/miniprogram/dev/api/device/memory/wx.offMemoryWarning.html) | 移除内存不足告警事件的监听函数 | 是 |

### [#](#陀螺仪) 陀螺仪

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.stopGyroscope](https://developers.weixin.qq.com/miniprogram/dev/api/device/gyroscope/wx.stopGyroscope.html) | 停止监听陀螺仪数据 | 是 |
| [wx.startGyroscope](https://developers.weixin.qq.com/miniprogram/dev/api/device/gyroscope/wx.startGyroscope.html) | 开始监听陀螺仪数据 | 是 |
| [wx.onGyroscopeChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/gyroscope/wx.onGyroscopeChange.html) | 监听陀螺仪数据变化事件 | 是 |

### [#](#扫码) 扫码

注：

- 此接口在 iOS 多端应用中使用需前往 `project.miniapp.json` 勾选「Others SDK」，并且需要在 `project.miniapp.json` 中配置 `NSCameraUsageDescription`
- 在 Android 端则需要前往 project.miniapp.json 勾选「 Scanner SDK」

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.scanCode](https://developers.weixin.qq.com/miniprogram/dev/api/device/scan/wx.scanCode.html) | 调起客户端扫码界面进行扫码 | 是 |

### [#](#短信) 短信

- 此接口在 iOS 多端应用中使用需前往 `project.miniapp.json` 勾选「Others SDK」

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.sendSms](https://developers.weixin.qq.com/miniprogram/dev/api/device/sms/wx.sendSms.html) | 拉起手机发送短信界面 | 支持 |

### [#](#振动) 振动

注：此接口在 iOS 多端应用中使用需前往 `project.miniapp.json` 勾选「Others SDK」

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.vibrateShort](https://developers.weixin.qq.com/miniprogram/dev/api/device/vibrate/wx.vibrateShort.html) | 使手机发生较短时间的振动（15 ms） | 是 |
| [wx.vibrateLong](https://developers.weixin.qq.com/miniprogram/dev/api/device/vibrate/wx.vibrateLong.html) | 使手机发生较长时间的振动（400 ms) | 是 |

## [#](#AI) AI

### [#](#视觉算法) 视觉算法

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.isVKSupport](https://developers.weixin.qq.com/miniprogram/dev/api/ai/visionkit/wx.isVKSupport.html) | 判断支持版本 | 否[4] |
| [wx.createVKSession](https://developers.weixin.qq.com/miniprogram/dev/api/ai/visionkit/wx.createVKSession.html) | 创建 vision kit 会话对象 | 否[4] |

### [#](#人脸检测) 人脸检测

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.stopFaceDetect](https://developers.weixin.qq.com/miniprogram/dev/api/ai/face/wx.stopFaceDetect.html) | 停止人脸检测 | 否[4] |
| [wx.initFaceDetect](https://developers.weixin.qq.com/miniprogram/dev/api/ai/face/wx.initFaceDetect.html) | 初始化人脸检测 | 否[4] |
| [wx.faceDetect](https://developers.weixin.qq.com/miniprogram/dev/api/ai/face/wx.faceDetect.html) | 人脸检测，使用前需要通过 wx.initFaceDetect 进行一次初始化，推荐使用相机接口返回的帧数据 | 否[4] |

## [#](#Worker) Worker

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.createWorker](https://developers.weixin.qq.com/miniprogram/dev/api/worker/wx.createWorker.html) | 创建一个 [Worker 线程](https://developers.weixin.qq.com/miniprogram/dev/api/worker/Worker.html) | 是 |

## [#](#WXML) WXML

wx.createSelectorQuery 在 Android 端需使用需前往 `project.miniapp.json` 勾选「XWEB SDK」

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.createSelectorQuery](https://developers.weixin.qq.com/miniprogram/dev/api/wxml/wx.createSelectorQuery.html) | 返回一个 [SelectorQuery](https://developers.weixin.qq.com/miniprogram/dev/api/wxml/SelectorQuery.html) 对象实例 | 是 |
| [wx.createIntersectionObserver](https://developers.weixin.qq.com/miniprogram/dev/api/wxml/wx.createIntersectionObserver.html) | 创建并返回一个 [IntersectionObserver](https://developers.weixin.qq.com/miniprogram/dev/api/wxml/IntersectionObserver.html) 对象实例 | 是 |

## [#](#第三方平台) 第三方平台

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.getExtConfigSync](https://developers.weixin.qq.com/miniprogram/dev/api/ext/wx.getExtConfigSync.html) | wx.getExtConfig 的同步版本 | 否[2] |
| [wx.getExtConfig](https://developers.weixin.qq.com/miniprogram/dev/api/ext/wx.getExtConfig.html) | 获取 ext.json 自定义的数据字段 | 否[2] |

## [#](#广告) 广告

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.createRewardedVideoAd](../handbook/devtools/ad) | 创建[激励视频广告组件](https://developers.weixin.qq.com/miniprogram/dev/api/ad/RewardedVideoAd.html) | 是，详情可查看[腾讯优量汇广告使用指南](../handbook/devtools/ad) |
| [wx.createInterstitialAd](https://developers.weixin.qq.com/miniprogram/dev/api/ad/wx.createInterstitialAd.html) | 创建[插屏广告组件](https://developers.weixin.qq.com/miniprogram/dev/api/ad/InterstitialAd.html) | 否[2] |

## [#](#开放接口) 开放接口

### [#](#登录) 登录

| 名称 | 功能说明 | 是否支持 | 备注 |
| --- | --- | --- | --- |
| [wx.pluginLogin](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/login/wx.pluginLogin.html) | **该接口仅在小程序插件中可调用**，调用接口获得插件用户标志凭证（code） | 否[2] |  |
| wx.login | 调用接口获取登录凭证（code） | 是[2] | 需替换新接口，[点击查看接口详情](diffapi/wx.login) |
| [wx.checkSession](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/login/wx.checkSession.html) | 检查登录态是否过期 | 否[1] | 使用多端身份管理 |

### [#](#账号信息) 账号信息

- 与小程序模式下返回的信息有差异，详情看接口文档

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.getAccountInfoSync](diffapi/getAccountInfo) | 获取当前账号信息 | 是 |

### [#](#用户信息) 用户信息

- 在 App 中开发者可以通过对接「微信登录」的接口获取用户微信的头像和昵称，详情可查看[wx.miniapp.login](miniapp/login)

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.getUserProfile](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/user-info/wx.getUserProfile.html) | 获取用户信息 | 否[2] |
| [wx.getUserInfo](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/user-info/wx.getUserInfo.html) | 获取[用户信息](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/user-info/UserInfo.html) | 否[2] |

### [#](#授权) 授权

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.authorizeForMiniProgram](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/authorize/wx.authorizeForMiniProgram.html) | **仅小程序插件中能调用该接口**，用法同 wx.authorize | 否[4] |
| [wx.authorize](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/authorize/wx.authorize.html) | 提前向用户发起授权请求 | 否[4] |

### [#](#设置) 设置

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.openSetting](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/setting/wx.openSetting.html) | 调起客户端小程序设置界面，返回用户设置的操作结果 | 否[4] |
| [wx.getSetting](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/setting/wx.getSetting.html) | 获取用户的当前设置 | 否[4] |
| [AuthSetting](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/setting/AuthSetting.html) | 用户授权设置信息，详情参考[权限](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/authorize) | 否[4] |
| [SubscriptionsSetting](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/setting/SubscriptionsSetting.html) | 订阅消息设置 | 否[4] |

### [#](#收货地址) 收货地址

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.chooseAddress](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/address/wx.chooseAddress.html) | 获取用户收货地址 | 否[4] |

### [#](#卡券) 卡券

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.openCard](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/card/wx.openCard.html) | 查看微信卡包中的卡券 | 否[4] |
| [wx.addCard](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/card/wx.addCard.html) | 批量添加卡券 | 否[4] |

### [#](#发票) 发票

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.chooseInvoiceTitle](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/invoice/wx.chooseInvoiceTitle.html) | 选择用户的发票抬头 | 否[4] |
| [wx.chooseInvoice](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/invoice/wx.chooseInvoice.html) | 选择用户已有的发票 | 否[4] |

### [#](#生物认证) 生物认证

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.startSoterAuthentication](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/soter/wx.startSoterAuthentication.html) | 开始 SOTER 生物认证 | 否[4] |
| [wx.checkIsSupportSoterAuthentication](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/soter/wx.checkIsSupportSoterAuthentication.html) | 获取本机支持的 SOTER 生物认证方式 | 否[4] |
| [wx.checkIsSoterEnrolledInDevice](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/soter/wx.checkIsSoterEnrolledInDevice.html) | 获取设备内是否录入如指纹等生物信息的接口 | 否[4] |

### [#](#微信运动) 微信运动

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.shareToWeRun](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/werun/wx.shareToWeRun.html) | 分享数据到微信运动 | 否[4] |
| [wx.getWeRunData](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/werun/wx.getWeRunData.html) | 获取用户过去三十天微信运动步数 | 否[4] |

### [#](#订阅消息) 订阅消息

- 小程序订阅消息能力在 App 中无法使用；
- App 中支持[一次性订阅消息](miniapp/requestSubscribeMessage)
- App 的消息推送可查看[消息推送使用指南](../handbook/devtools/impush)

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.requestSubscribeMessage](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/subscribe-message/wx.requestSubscribeMessage.html) | 调起客户端小程序订阅消息界面，返回用户订阅消息的操作结果 | 否[4] |
| [wx.requestSubscribeDeviceMessage](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/subscribe-message/wx.requestSubscribeDeviceMessage.html) | 订阅设备消息接口，调用后弹出授权框，用户同意后会允许开发者给用户发送订阅模版消息 | 否[4] |

### [#](#微信红包) 微信红包

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.showRedPackage](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/redpackage/wx.showRedPackage.html) | 拉取h5领取红包封面页 | 否[4] |

### [#](#收藏) 收藏

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.addVideoToFavorites](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/favorites/wx.addVideoToFavorites.html) | 收藏视频 | 否[4] |
| [wx.addFileToFavorites](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/favorites/wx.addFileToFavorites.html) | 收藏文件 | 否[4] |

### [#](#车牌) 车牌

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.chooseLicensePlate](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/license-plate/wx.chooseLicensePlate.html) | 选择车牌号 | 否[4] |

### [#](#视频号) 视频号

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.reserveChannelsLive](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/channels/wx.reserveChannelsLive.html) | 预约视频号直播 | 否[4] |
| [wx.openChannelsUserProfile](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/channels/wx.openChannelsUserProfile.html) | 打开视频号主页 | 否[4] |
| [wx.openChannelsLive](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/channels/wx.openChannelsLive.html) | 打开视频号直播 | 否[4] |
| [wx.openChannelsEvent](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/channels/wx.openChannelsEvent.html) | 打开视频号活动页 | 否[4] |
| [wx.openChannelsActivity](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/channels/wx.openChannelsActivity.html) | 打开视频号视频 | 否[4] |
| [wx.getChannelsShareKey](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/channels/wx.getChannelsShareKey.html) | 获取视频号直播卡片/视频卡片的分享来源，仅当卡片携带了分享信息、同时用户已授权该小程序获取视频号分享信息且启动场景值为 1177、1184、1195、1208 时可用 | 否[4] |
| [wx.getChannelsLiveNoticeInfo](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/channels/wx.getChannelsLiveNoticeInfo.html) | 获取视频号直播预告信息 | 否[4] |
| [wx.getChannelsLiveInfo](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/channels/wx.getChannelsLiveInfo.html) | 获取视频号直播信息 | 否[4] |

### [#](#微信群) 微信群

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.getGroupEnterInfo](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/group/wx.getGroupEnterInfo.html) | 获取微信群聊场景下的小程序启动信息 | 不支持 |

### [#](#微信客服) 微信客服

| 名称 | 功能说明 | 是否支持 |
| --- | --- | --- |
| [wx.openCustomerServiceChat](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/service-chat/wx.openCustomerServiceChat.html) | 打开微信客服，页面产生点击事件（例如 button 上 bindtap 的回调中）后才可调用 | 不支持；可使用 [wx.miniapp.openCustomerServiceChat](miniapp/openCustomerServiceChat) 替代 |

## [#](#多端框架新增-API) 多端框架新增 API

- 即，除了小程序已有的 JSAPI ，多端框架也为 App 的功能开放了更多仅适用于多端应用的 API，包括多端框架的通用 API 和身份管理 API
- API 列表的查看路径如下：

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202503121732616.png)

Incorrect translation.