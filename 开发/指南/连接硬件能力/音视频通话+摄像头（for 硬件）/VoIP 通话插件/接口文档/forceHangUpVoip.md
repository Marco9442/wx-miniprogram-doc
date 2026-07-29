# [#](#void-forceHangUpVoip-string-roomId) void forceHangUpVoip([string roomId])

强制结束通话

## [#](#参数) 参数

### [#](#String-roomId) String roomId

可选。2.3.2 开始支持。

- 不传入时，挂断当前正在进行的通话；
- 传入时，仅在当前通话 roomId 与传入相同时，挂断当前正在进行的通话。（建议）

## [#](#返回值) 返回值

无

## [#](#示例代码) 示例代码

```
const wmpfVoip = requirePlugin('wmpf-voip').default

wmpfVoip.forceHangUpVoip('some group id')
```

Incorrect translation.