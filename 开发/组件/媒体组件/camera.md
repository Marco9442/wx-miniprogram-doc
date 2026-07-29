# [#](#camera) camera

> 基础库 1.6.0 开始支持，低版本需做[兼容处理](../framework/compatibility.html)。

> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [wx.createCameraContext](../api/media/camera/wx.createCameraContext.html)

渲染框架支持情况：Skyline （使用最新 [Nightly](/miniprogram/dev/devtools/nightly.html) 工具调试）、WebView

## [#](#功能描述) 功能描述

系统相机。扫码二维码功能，需升级微信客户端至6.7.3。需要[用户授权](../framework/open-ability/authorize.html) `scope.camera`。
[2.10.0](../framework/compatibility.html)起 initdone 事件返回 maxZoom，最大变焦范围，相关接口 [CameraContext.setZoom](../api/media/camera/CameraContext.setZoom.html)。

## [#](#通用属性) 通用属性

|  | 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- | --- |
|  | mode | string | normal | 否 | 应用模式，只在初始化时有效，不能动态变更 | [2.1.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | normal | 相机模式 | | scanCode | 扫码模式 | | | | | | |
|  | resolution | string | medium | 否 | 分辨率，不支持动态修改 | [2.10.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | low | 低 | | medium | 中 | | high | 高 | | | | | | |
|  | device-position | string | back | 否 | 摄像头朝向 | [1.0.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | front | 前置 | | back | 后置 | | | | | | |
|  | flash | string | auto | 否 | 闪光灯，值为auto, on, off | [1.0.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | 最低版本 | | --- | --- | --- | | auto | 自动 |  | | on | 打开 |  | | off | 关闭 |  | | torch | 常亮 | [2.8.0](../framework/compatibility.html) | | | | | | |
|  | frame-size | string | medium | 否 | 指定期望的相机帧数据尺寸 | [2.7.0](../framework/compatibility.html) |
|  | | 合法值 | 说明 | | --- | --- | | small | 小尺寸帧数据 | | medium | 中尺寸帧数据 | | large | 大尺寸帧数据 | | | | | | |
|  | bindstop | eventhandle |  | 否 | 摄像头在非正常终止时触发，如退出后台等情况 | [1.0.0](../framework/compatibility.html) |
|  | binderror | eventhandle |  | 否 | 用户不允许使用摄像头时触发 | [1.0.0](../framework/compatibility.html) |
|  | bindinitdone | eventhandle |  | 否 | 相机初始化完成时触发，`e.detail = {maxZoom}` | [2.7.0](../framework/compatibility.html) |
|  | bindscancode | eventhandle |  | 否 | 在扫码识别成功时触发，仅在 mode="scanCode" 时生效 | [2.1.0](../framework/compatibility.html) |

## [#](#Bug-Tip) Bug & Tip

1. `tip`: 同一页面只能插入一个 `camera` 组件
2. `tip`:请注意[原生组件使用限制](native-component.html#原生组件的使用限制)
3. `tip`:onCameraFrame 接口根据 frame-size 返回不同尺寸的原始帧数据，与 Camera 组件展示的图像不同，其实际像素值由系统决定

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/VBZ3Jim26zYu "在开发者工具中预览效果")

```
<!-- camera.wxml -->
<camera device-position="back" flash="off" binderror="error" style="width: 100%; height: 300px;"></camera>
<button type="primary" bindtap="takePhoto">拍照</button>
<view>预览</view>
<image mode="widthFix" src="{{src}}"></image>
```

```
// camera.js
Page({
  takePhoto() {
    const ctx = wx.createCameraContext()
    ctx.takePhoto({
      quality: 'high',
      success: (res) => {
        this.setData({
          src: res.tempImagePath
        })
      }
    })
  },
  error(e) {
    console.log(e.detail)
  }
})
```

Incorrect translation.