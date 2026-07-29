# [#](#callDevice-Object-req) callDevice(Object req)

> 本接口为异步接口，返回 `Promise` 对象。
>
> 需插件 2.4.0 版本开始支持

从手机客户端的小程序呼叫 Linux 设备、RTOS 设备。调用此接口后，会创建 VoIP 房间。开发者应自行向设备端推送通话提醒。详情参考[《手机微信呼叫设备(Linux 直连)》](../../voip/call-device)。

**本接口只能在微信客户端内使用，不可在 WMPF 内使用。建议先阅读[接口介绍](call-intro)。**

## [#](#参数) 参数

### [#](#Object-req) Object req

| 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- |
| roomType | string |  | 是 | 通话类型。voice: 音频通话；video: 视频通话 |  |
| sn | string |  | 是 | 接听方设备 SN |  |
| modelId | string |  | 是 | 接听方设备 modelId |  |
| chargeType | string | 'license' | 否 | 计费方式。duration: 时长计费；license：license 计费 |  |
| timeLimit | number |  | 否 | 最大通话时长，需为 > 0 的数字 |  |
| enableCallerCamera | boolean | true | 否 | 拨打方是否启用摄像头 |  |
| enableListenerCamera | boolean | true | 否 | 接听方是否启用摄像头 |  |
| nickName | string |  | 否 | 设备端显示的微信用户名称，仅记录 |  |
| deviceName | string |  | 否 | 微信端显示的设备名称 | 2.4.1 |
| isCloud | boolean | false | 否 | 如果是呼叫 RTOS 设备，设置为 true 以触发消息回调 |  |
| payload | string |  | 否 | 呼叫 RTOS 时，可以带 payload 到回调消息中 |  |
| encodeVideoFixedLength | number | 0 | 否 | 编码的长边值，可取 320、480、640 |  |
| encodeVideoRotation | number | 0 | 否 | 编码的视频旋转方向。1: 发出正向流. 2: 保持发出旋转流 |  |
| encodeVideoRatio | number | 0 | 否 | 视频的比例, 宽/高\*100 |  |
| encodeVideoMaxFPS | number | 0 | 否 | 视频的最大 FPS, 8-15 |  |

## [#](#返回值) 返回值

**本接口调用失败会抛出[异常](errCode)。**

### [#](#Object) Object

接口调用成功时，返回如下：

| 属性 | 类型 | 说明 | 最低版本 |
| --- | --- | --- | --- |
| roomId | string | 本次通话的房间号 |  |

## [#](#示例代码) 示例代码

```
const wmpfVoip = requirePlugin('wmpf-voip').default

try {
  const { roomId } = await wmpfVoip.callDevice({
    roomType: 'video',
    sn: '设备 SN',
    modelId: '设备 modelId',
    nickName: '设备端显示的微信用户名称',
  })

  if (/* 当前不在插件页面 */) {
    wx.redirectTo({
      url: wmpfVoip.CALL_PAGE_PATH,
    })
  }
} catch (e) {
  console.error('callDevice failed:', e)
  wx.showToast({
    title: '呼叫失败',
    icon: 'error',
  })
}
```

Incorrect translation.