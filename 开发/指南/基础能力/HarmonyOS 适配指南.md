# [#](#HarmonyOS-适配指南) HarmonyOS 适配指南

基础库从 3.7.0 起正式支持 HarmonyOS 平台，后续与其它平台一致，通过后台灰度更新[基础库](../client-lib/index)，开发者工具可在详情 - 本地设置 - 调试基础库切到 3.7.0 版本进行开发调试。

## [#](#架构概览) 架构概览

小程序在 HarmonyOS 平台的[运行环境](../runtime/env)与安卓类似，即逻辑层的 JavaScript 代码运行在 v8 中，视图层是基于 HarmonyOS 原生的 ArkWeb 引擎来渲染，而 Skyline 渲染引擎在支持中，暂未提供。

此外，小程序的运行机制、更新机制、组件框架等均保持一致，但在一些特性支持度上会有区别。

## [#](#适配方式) 适配方式

目前小程序在 HarmonyOS 平台与其它平台的区别主要是 HarmonyOS 的 WebView 引擎及涉及原生能力的特性上。

前者在 HarmonyOS 上使用的是 ArkWeb 引擎，可能存在一些依赖 WebView 的特性上的差异，如 CSS 样式相关，这类问题需按实际情况兼容；

后者大多是与组件/接口相关，可通过 `wx.canIUse` 接口或者通过 `wx.getDeviceInfo().platform === 'ohos'` 判断，对业务逻辑做必要的兼容。

> 注意：如在微信开发者工具中模拟鸿蒙，则需判断 wx.getDeviceInfo().system=='HarmonyOS' (工具中 platform 为 devtools)

## [#](#调试方式) 调试方式

- 通过开发者工具调试

1. 下载最新的 nightly 版开发者工具，通过最新开发者工具调试
2. 调试基础库版本选择 3.7.0+
3. 选择「小程序模式」，并选择华为鸿蒙机型
4. 支持使用 wx.canIUse 判断接口是否可使用

- 通过真机调试

在 HarmonyOS 的应用商店下载，安装后即可正常打开小程序进行调试。

## [#](#支持情况) 支持情况

以下罗列出暂未支持的特性，对使用到未支持的特性需做好兼容。其中组件/接口具体的支持情况可跳转至对应文档查看，**部分支持的一般代表少数高阶功能不支持**。

#### [#](#框架) 框架

| 特性 | 支持情况 |
| --- | --- |
| [Skyline 渲染引擎](../runtime/skyline/introduction) | 支持中 |
| 初始渲染缓存 | 不支持 |
| 暗黑模式 | 不支持 |
| 周期性更新 | 不支持 |
| 数据预拉取 | 不支持 |
| 无障碍访问 | 不支持 |
| 分享朋友圈 | 不支持 |

#### [#](#组件) 组件

| 组件 | 支持情况 |
| --- | --- |
| 无障碍访问 | 不支持 |
| keyboard-accessory | 不支持 |
| channel-live | 不支持 |
| channel-video | 不支持 |
| voip-room | 不支持 |
| map | 部分支持 |
| canvas | 部分支持 |
| ad/ad-custom | 不支持 |
| official-account | 不支持 |
| xr-frame | 不支持 |
| web-view | 部分支持 |

#### [#](#接口) 接口

| 模块 | 接口 | 支持情况 |
| --- | --- | --- |
| 基础-生命周期 | wx.onApiCategoryChange / wx.offApiCategoryChange / wx.getApiCategory | 不支持 |
| 基础-应用级事件 | wx.onThemeChange / wx.offThemeChange / wx.onAudioInterruptionEnd / wx.onAudioInterruptionBegin / wx.offAudioInterruptionEnd / wx.offAudioInterruptionBegin | 不支持 |
| 基础-性能 | wx.preloadWebview / wx.preloadSkylineView | 不支持 |
| 路由-自定义路由 | - | 支持中 |
| 跳转 | wx.openEmbeddedMiniProgram / wx.onEmbeddedMiniProgramHeightChange / wx.offEmbeddedMiniProgramHeightChange | 不支持 |
| 转发 | wx.showShareImageMenu / wx.onCopyUrl / wx.offCopyUrl | 不支持 |
| 界面-交互 | wx.enableAlertBeforeUnload / wx.disableAlertBeforeUnload | 支持中 |
| 界面-滚动 | ScrollViewContext | 不支持 |
| 界面-置顶 | wx.setTopBarText | 不支持 |
| 界面-窗口 | - | 不支持 |
| 界面-worklet动画 | - | 支持中 |
| 支付 | wx.requestCommonPayment / wx.requestVirtualPayment / wx.openHKOfflinePayView | 不支持 |
| 数据缓存-数据预拉取和周期性更新 | wx.getBackgroundFetchData / wx.onBackgroundFetchData / wx.setBackgroundFetchToken / wx.getBackgroundFetchToken | 不支持 |
| 数据缓存-缓存管理器 | - | 不支持 |
| 画布 | - | 部分支持 |
| 媒体-视频 | wx.openVideoEditor | 不支持 |
| 媒体-音频 | 只支持 WebAudio | 不支持 |
| 媒体-音视频合成 | - | 不支持 |
| 媒体-画面录制器 | - | 不支持 |
| 媒体-视频解码器 | - | 不支持 |
| 开放接口-卡券 | - | 不支持 |
| 开放接口-发票 | - | 不支持 |
| 开放接口-生物认证 | - | 不支持 |
| 开放接口-车牌 | - | 不支持 |
| 开放接口-视频号 | wx.openChannelsEvent | 不支持 |
| 开放接口-微信客服 | - | 不支持 |
| 设备-联系人 | wx.addPhoneContact | 不支持 |
| 设备-无障碍 | - | 不支持 |
| 设备-电量 | wx.onBatteryInfoChange / wx.offBatteryInfoChange | 不支持 |
| 设备-网络 | wx.onNetworkWeakChange / wx.offNetworkWeakChange / wx.offNetworkStatusChange | 不支持 |
| 设备-屏幕 | wx.onScreenRecordingStateChanged / wx.offScreenRecordingStateChanged / wx.getScreenRecordingState | 不支持 |
| 设备-内存 | - | 不支持 |
| AI | - | 不支持 |
| Worker | - | 部分支持 |
| 广告 | - | 不支持 |
| Skyline | - | 支持中 |
| XR-FRAME | - | 不支持 |

Incorrect translation.