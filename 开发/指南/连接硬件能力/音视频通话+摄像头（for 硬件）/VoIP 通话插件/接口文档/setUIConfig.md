# [#](#void-setUIConfig-Object-config) void setUIConfig(Object config)

设置插件通话界面，**需保证在通话开始前设置**。

## [#](#参数) 参数

### [#](#Object-req) Object req

| 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- |
| btnText | string |  | 否 | 接听页面按钮文案，与使用<setCustomBtnText> 一致 |  |
| callerUI | UIConfig |  | 否 | caller 通话 UI 设置 |  |
| listenerUI | UIConfig |  | 否 | listener 通话 UI 设置 |  |
| handsFree | boolean | true | 否 | 是否开启免提（true 为扬声器输出，false 为听筒输出）。 **仅在设备端生效** | 插件 2.3.0，WMPF >= 2.0 |
| isSelfWindowMax | boolean | false | 否 | 视频通话时，控制主窗口默认是否显示本端。（true 为本端，false 为对端） | 2.3.4 |
| customBoxHeight | string | '90vh' | 否 | 接听页自定义按钮点击后弹层高度。仅支持 70vh 或 90vh。 | 2.3.10 |

**UIConfig**

| 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- |
| cameraRotation | number | 0 | 否 | 视频画面旋转角度，有效值为 0, 90, 180, 270 |  |
| aspectRatio | number | 4/3 | 否 | 视频画面纵横比，使用方法见示例 |  |
| horMirror | boolean | false | 否 | 视频画面水平镜像 |  |
| vertMirror | boolean | false | 否 | 视频画面垂直镜像 |  |
| enableToggleCamera | boolean | true | 否 | 视频通话是否支持切换摄像头。false 时不显示切换摄像头按钮。 **仅在手机微信内生效**。WMPF 默认开摄像头，且不显示开关按钮。 |  |
| objectFit | string | 'fill' | 否 | 视频画面与容器比例不一致时的表现形式。支持 fill/contain,使用方法见示例 | 2.3.8 |

**aspectRatio 与 objectFit 的设置示例：**

![](https://res8.wxqcloud.qq.com.cn/wxdoc/d2caa0ea-cb95-4e60-822e-5800a6630dfc.png)

## [#](#返回值) 返回值

无

## [#](#示例代码) 示例代码

```
const wmpfVoip = requirePlugin('wmpf-voip').default

wmpfVoip.setUIConfig({
  btnText: '去开门',
  callerUI: {
    aspectRatio: 16 / 9,
  },
  handsFree: false,
})
```

Incorrect translation.