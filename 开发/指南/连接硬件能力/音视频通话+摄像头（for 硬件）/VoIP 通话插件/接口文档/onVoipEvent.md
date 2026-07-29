连接硬件能力/音视频通话+摄像头（for 硬件）/VoIP 通话插件/接口文档/onVoipEvent/
# [\#](https://developers.weixin.qq.com/miniprogram/dev/framework/device/voip-plugin/api/onVoipEvent.html\#function-onVoipEvent-function-listener) function onVoipEvent(function listener)
## [\#](https://developers.weixin.qq.com/miniprogram/dev/framework/device/voip-plugin/api/onVoipEvent.html\#%E5%8A%9F%E8%83%BD%E6%8F%8F%E8%BF%B0) 功能描述
监听 VoIP 通话相关事件。 \*\*事件绑定需要在通话开始前完成\*\*。
\*\*注意：不要在 onLoad、onShow 等生命周期内绑定事件，可能会因为生命周期多次调用而重复绑定。\*\*
## [\#](https://developers.weixin.qq.com/miniprogram/dev/framework/device/voip-plugin/api/onVoipEvent.html\#%E5%8F%82%E6%95%B0) 参数
### [\#](https://developers.weixin.qq.com/miniprogram/dev/framework/device/voip-plugin/api/onVoipEvent.html\#function-listener) function listener
事件监听函数
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/framework/device/voip-plugin/api/onVoipEvent.html\#%E5%9B%9E%E8%B0%83%E5%8F%82%E6%95%B0) 回调参数
##### [\#](https://developers.weixin.qq.com/miniprogram/dev/framework/device/voip-plugin/api/onVoipEvent.html\#Object-event) Object event
| 属性 | 类型 | 说明 | 最低版本 |
| --- | --- | --- | --- |
| eventName | string | 事件名称。请参考后文描述。 | |
| roomId | string | 通话房间号。除 `bindContact`、`callPageOnShow` 事件外提供 | 2.4.0 |
| groupId | string | 与 roomId 相同 | |
| data | Object | 某个事件额外的参数。不同事件的字段不同，请参考后文描述 | |
## [\#](https://developers.weixin.qq.com/miniprogram/dev/framework/device/voip-plugin/api/onVoipEvent.html\#%E8%BF%94%E5%9B%9E%E5%80%BC) 返回值
function
取消监听函数，调用后取消监听事件。该函数无参数，无返回值。
## [\#](https://developers.weixin.qq.com/miniprogram/dev/framework/device/voip-plugin/api/onVoipEvent.html\#%E4%BA%8B%E4%BB%B6%E6%8F%8F%E8%BF%B0) 事件描述
### [\#](https://developers.weixin.qq.com/miniprogram/dev/framework/device/voip-plugin/api/onVoipEvent.html\#\_1-startVoip) 1\. startVoip
通话开始。
### [\#](https://developers.weixin.qq.com/miniprogram/dev/framework/device/voip-plugin/api/onVoipEvent.html\#\_2-abortVoip) 2\. abortVoip
通话异常中断。
\*\*data 参数\*\*
| 属性 | 类型 | 说明 |
| --- | --- | --- |
| keepTime | number | 通话时长 |
| status | string | 异常说明，取值参见后文 |
| error | Object | 错误对象 |
| error.errMsg | Object | 错误信息 |
\*\*status 取值\*\*
| status | 描述 |
| --- | --- |
| abortByListener | 通话因本端异常中断（接听方触发） |
| abortByCaller | 通话因本端异常中断（拨打方触发） |
| unknown | 通话因对端异常中断 |
\*\*常见 errMsg\*\*
- `room status is abort`：status=unknown，接收到对端通话异常时触发，需要根据 roomId 关联对端触发的 abortVoip 事件判断真正的异常原因。
- `listener waitOtherToJoin timeout`：status=abortByListener，接听方加入房间后，拨打方一直未成功加入（可能是网络慢等原因）或异常退出，接听方等待 20s 超时后触发。此时建议分析接听方的情况来排查。
- `call interrupted due to close passive float ball`：用户将小程序切后台后，会展示小程序浮窗，用户通过浮窗关闭小程序时触发。
- `in comming call`：小程序通话被其他来电打断时触发。
- `call interrupted due to native reason`：一般是由于通话过程中一段时间未收到数据包（一般是网络原因），被踢出房间中断通话。
### [\#](https://developers.weixin.qq.com/miniprogram/dev/framework/device/voip-plugin/api/onVoipEvent.html\#\_3-hangOnVoip) 3\. hangOnVoip
通话被接听（仅接听方触发）。
### [\#](https://developers.weixin.qq.com/miniprogram/dev/framework/device/voip-plugin/api/onVoipEvent.html\#\_4-cancelVoip) 4\. cancelVoip
通话未接通，拨打方取消通话。
\*\*data 参数\*\*
| 属性 | 类型 | 说明 |
| --- | --- | --- |
| status | string | 取消原因说明，取值参见后文 |
\*\*status 取值\*\*
| status | 描述 |
| --- | --- |
| manual | 用户点击界面挂断按钮取消通话。（仅拨打方） |
| unloadCallPage | 插件页面被销毁导致取消通话。（仅拨打方） |
| forceFromApp | 小程序调用 `forceHangUpVoip` 取消通话。（仅拨打方） |
| other | 拨打方取消通话。（仅接听方） |
### [\#](https://developers.weixin.qq.com/miniprogram/dev/framework/device/voip-plugin/api/onVoipEvent.html\#\_5-rejectVoip) 5\. rejectVoip
通话未接通，接听方拒接。
\*\*data 参数\*\*
| 属性 | 类型 | 说明 |
| --- | --- | --- |
| status | string | 拒接原因说明，取值参见后文 |
\*\*status 取值\*\*
| status | 描述 |
| --- | --- |
| manual | 用户点击界面挂断按钮拒接通话（仅接听方） |
| unloadCallPage | 插件页面被销毁导致拒接通话（仅接听方） |
| forceFromApp | 小程序调用 `forceHangUpVoip` 拒接通话（仅接听方） |
| other | 接听方拒接（仅拨打方） |
### [\#](https://developers.weixin.qq.com/miniprogram/dev/framework/device/voip-plugin/api/onVoipEvent.html\#\_6-hangUpVoip) 6\. hangUpVoip
通话已接通，拨打方/接听方挂断通话。
\*\*data 参数\*\*
| 属性 | 类型 | 说明 |
| --- | --- | --- |
| keepTime | number | 通话时长 |
| status | string | 挂断方说明，取值参见后文 |
| origin | string | 挂断原因说明，取值参见后文 |
\*\*status 取值\*\*
| status | 描述 |
| --- | --- |
| endByListener | 接听方挂断 |
| endByCaller | 拨打方挂断 |
\*\*origin 取值\*\*
为了保持向下兼容，hangUpVoip 事件额外使用 origin 字段提供具体的挂断原因信息。
| origin | 描述 |
| --- | --- |
| manual | 用户点击界面挂断按钮挂断通话（仅挂断方） |
| unloadCallPage | 插件页面被销毁导致挂断通话（仅挂断方） |
| forceFromApp | 小程序调用 `forceHangUpVoip` 导致挂断通话（仅挂断方） |
| other | 对方挂断通话 |
| timeLimit | 超过最大通话时长 |
### [\#](https://developers.weixin.qq.com/miniprogram/dev/framework/device/voip-plugin/api/onVoipEvent.html\#\_7-endVoip) 7\. endVoip
通话结束。
\*\*data 参数\*\*
| 属性 | 类型 | 说明 |
| --- | --- | --- |
| keepTime | number | 通话时长 |
| callerName | string | 拨打方名字 |
| listenerName | string | 接听方名字 |
| roomType | string | 房间类型 |
| isCaller | boolean | 是否是拨打方 |
| businessType | number | 业务类型 |
### [\#](https://developers.weixin.qq.com/miniprogram/dev/framework/device/voip-plugin/api/onVoipEvent.html\#\_8-busy) 8\. busy
通话未接通，接听方占线（仅拨打方触发）。
### [\#](https://developers.weixin.qq.com/miniprogram/dev/framework/device/voip-plugin/api/onVoipEvent.html\#\_9-calling) 9\. calling
通话过程中, 双方都会每秒触发一次。
\*\*data 参数\*\*
| 属性 | 类型 | 说明 |
| --- | --- | --- |
| keepTime | number | 通话时长 |
### [\#](https://developers.weixin.qq.com/miniprogram/dev/framework/device/voip-plugin/api/onVoipEvent.html\#\_10-timeout) 10\. timeout
通话超时未接听。
### [\#](https://developers.weixin.qq.com/miniprogram/dev/framework/device/voip-plugin/api/onVoipEvent.html\#\_11-joinedRoomByCaller) 11\. joinedRoomByCaller
拨打方加入房间成功（仅拨打方触发）。
### [\#](https://developers.weixin.qq.com/miniprogram/dev/framework/device/voip-plugin/api/onVoipEvent.html\#\_12-joinFailCaller) 12\. joinFailCaller
拨打方加入房间失败（仅拨打方触发）。
\*\*data 参数\*\*
| 属性 | 类型 | 说明 |
| --- | --- | --- |
| errMsg | string | 错误消息 |
| message | string | 由于向下兼容原因，某些情况下 data 是一个 Error 对象 |
### [\#](https://developers.weixin.qq.com/miniprogram/dev/framework/device/voip-plugin/api/onVoipEvent.html\#\_13-joinFailListener) 13\. joinFailListener
接听方加入房间失败（仅接听方触发）。
\*\*data 参数\*\*
| 属性 | 类型 | 说明 |
| --- | --- | --- |
| errMsg | string | 错误消息 |
| message | string | 由于向下兼容原因，某些情况下 data 是一个 Error 对象 |
### [\#](https://developers.weixin.qq.com/miniprogram/dev/framework/device/voip-plugin/api/onVoipEvent.html\#\_14-finishVoip) 14\. finishVoip
通话完成。返回本次通话结算使用的实际时长。
需从后台获取最终时间后触发，触发时机晚于 endVoip。
\*\*data 参数\*\*
| 属性 | 类型 | 说明 |
| --- | --- | --- |
| keepTime | number | 结算用通话时长 |
### [\#](https://developers.weixin.qq.com/miniprogram/dev/framework/device/voip-plugin/api/onVoipEvent.html\#\_15-callPageOnShow) 15\. callPageOnShow
插件通话页面 onShow。
### [\#](https://developers.weixin.qq.com/miniprogram/dev/framework/device/voip-plugin/api/onVoipEvent.html\#\_16-showCustomBox) 16\. showCustomBox
用户点击通话页面自定义按钮，展示自定义组件。
\*\*data 参数\*\*
| 属性 | 类型 | 说明 |
| --- | --- | --- |
| callerId | string | 拨打方 ID |
| listenerId | string | 接听方 ID |
### [\#](https://developers.weixin.qq.com/miniprogram/dev/framework/device/voip-plugin/api/onVoipEvent.html\#\_17-hideCustomBox) 17\. hideCustomBox
用户隐藏自定义组件。
\*\*data 参数\*\*
| 属性 | 类型 | 说明 |
| --- | --- | --- |
| callerId | string | 拨打方 ID |
| listenerId | string | 接听方 ID |
## [\#](https://developers.weixin.qq.com/miniprogram/dev/framework/device/voip-plugin/api/onVoipEvent.html\#%E7%A4%BA%E4%BE%8B%E4%BB%A3%E7%A0%81) 示例代码
```js
const wmpfVoip = requirePlugin('wmpf-voip').default
const offVoipEvent = wmpfVoip.onVoipEvent(event => {
console.info(`onVoipEvent`, event)
})
// 需要取消监听时调用
offVoipEvent()
```