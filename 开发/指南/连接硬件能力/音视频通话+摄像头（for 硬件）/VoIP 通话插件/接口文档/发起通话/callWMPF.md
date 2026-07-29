# [#](#callWMPF-Object-req) callWMPF(Object req)

> 本接口为异步接口，返回 `Promise` 对象。
>
> 需插件 2.4.0 版本开始支持

从手机客户端的小程序呼叫运行安卓 WMPF 的设备。调用此接口后，会创建 VoIP 房间，并且向设备推送 WMPF pushMsg 提醒。详情参考[《手机微信呼叫设备(安卓)》](../../voip/call-wmpf)。

**本接口只能在微信客户端内使用，不可在 WMPF 内使用。建议先阅读[接口介绍](call-intro)。**

## [#](#参数) 参数

### [#](#Object-req) Object req

| 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- |
| roomType | string |  | 是 | 通话类型。voice: 音频通话；video: 视频通话 |  |
| sn | string |  | 是 | 接听方设备 SN |  |
| modelId | string |  | 是 | 接听方设备 modelId |  |
| pushToken | string |  | 是 | 从设备获取的 [pushToken](https://developers.weixin.qq.com/doc/oplatform/Miniprogram_Frame/push) |  |
| nickName | string |  | 是 | 设备端显示的微信用户名称 |  |
| deviceName | string |  | 否 | 微信端显示的设备名称 | 2.4.1 |
| chargeType | string | 'license' | 否 | 计费方式。duration: 时长计费；license：license 计费 |  |
| timeLimit | number |  | 否 | 最大通话时长，需为 > 0 的数字 |  |
| enableCallerCamera | boolean | true | 否 | 拨打方是否启用摄像头。 |  |
| enableListenerCamera | boolean | true | 否 | 接听方是否启用摄像头。 |  |
| envVersion | string | 'release' | 否 | 接听方打开的小程序类型。 取值：release: 正式版; trial: 体验版; develop: 开发版。 正式版小程序只能拨打给正式版，设置这一字段无效。 |  |
| customQuery | string |  | 否 | 接听方打开小程序时，会作为 query 拼接到插件页面路径后，格式如 `a=1&b=2`。可在接听端小程序内通过 `getPluginOnloadOptions` 或 `getPluginEnterOptions` 接口获取到 |  |

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
  const { roomId } = await wmpfVoip.callWMPF({
    roomType: 'video',
    sn: '设备 SN',
    modelId: '设备 modelId',
    nickName: '设备端显示的微信用户名称',
    pushToken: 'xxxx*****xxxx',
  })

  if (/* 当前不在插件页面 */) {
    wx.redirectTo({
      url: wmpfVoip.CALL_PAGE_PATH,
    })
  }
} catch (e) {
  console.error('callWMPF failed:', e)
  wx.showToast({
    title: '呼叫失败',
    icon: 'error',
  })
}
```

Incorrect translation.