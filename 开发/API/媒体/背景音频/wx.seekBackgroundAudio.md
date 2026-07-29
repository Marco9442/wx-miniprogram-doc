# [#](#wx-seekBackgroundAudio-Object-object) wx.seekBackgroundAudio(Object object)

从基础库 [1.2.0](../../../framework/compatibility.html) 开始，本接口停止维护，请使用 [wx.getBackgroundAudioManager](wx.getBackgroundAudioManager.html) 代替

> **以 [Promise 风格](../../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：支持
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [1.9.6](../../../framework/compatibility.html)
>
> **微信 鸿蒙 OS 版**：支持

## [#](#功能描述) 功能描述

控制音乐播放进度。

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| position | number |  | 是 | 音乐位置，单位：秒 |
| success | function |  | 否 | 接口调用成功的回调函数 |
| fail | function |  | 否 | 接口调用失败的回调函数 |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

## [#](#示例代码) 示例代码

```
wx.seekBackgroundAudio({
  position: 30
})
```

Incorrect translation.