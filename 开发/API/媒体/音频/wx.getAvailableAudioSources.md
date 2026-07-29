# [#](#wx-getAvailableAudioSources-Object-object) wx.getAvailableAudioSources(Object object)

> 基础库 2.1.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **以 [Promise 风格](../../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：支持
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [2.15.0](../../../framework/compatibility.html)

## [#](#功能描述) 功能描述

获取当前支持的音频输入源

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

|  | 属性 | 类型 | 说明 |
| --- | --- | --- | --- |
|  | audioSources | Array.<string> | 支持的音频输入源列表，可在 [RecorderManager.start()](../recorder/RecorderManager.start.html) 接口中使用。返回值定义参考 https://developer.android.com/reference/kotlin/android/media/MediaRecorder.AudioSource |
|  | | 合法值 | 说明 | | --- | --- | | auto | 自动设置，默认使用手机麦克风，插上耳麦后自动切换使用耳机麦克风，所有平台适用 | | buildInMic | 手机麦克风，仅限 iOS | | headsetMic | 耳机麦克风，仅限 iOS | | mic | 麦克风（没插耳麦时是手机麦克风，插耳麦时是耳机麦克风），仅限 Android | | camcorder | 同 mic，适用于录制音视频内容，仅限 Android | | voice\_communication | 同 mic，适用于实时沟通，仅限 Android | | voice\_recognition | 同 mic，适用于语音识别，仅限 Android | | | |

Incorrect translation.