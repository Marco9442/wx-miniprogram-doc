# [#](#RecorderManager) RecorderManager

全局唯一的录音管理器

## [#](#方法) 方法

### [#](#RecorderManager-start-Object-object) [RecorderManager.start(Object object)](RecorderManager.start.html)

开始录音

### [#](#RecorderManager-pause) [RecorderManager.pause()](RecorderManager.pause.html)

暂停录音

### [#](#RecorderManager-resume) [RecorderManager.resume()](RecorderManager.resume.html)

继续录音

### [#](#RecorderManager-stop) [RecorderManager.stop()](RecorderManager.stop.html)

停止录音

### [#](#RecorderManager-onStart-function-listener) [RecorderManager.onStart(function listener)](./RecorderManager.onStart.html)

监听录音开始事件

### [#](#RecorderManager-onResume-function-listener) [RecorderManager.onResume(function listener)](./RecorderManager.onResume.html)

监听录音继续事件

### [#](#RecorderManager-onPause-function-listener) [RecorderManager.onPause(function listener)](./RecorderManager.onPause.html)

监听录音暂停事件

### [#](#RecorderManager-onStop-function-listener) [RecorderManager.onStop(function listener)](./RecorderManager.onStop.html)

监听录音结束事件

### [#](#RecorderManager-onFrameRecorded-function-listener) [RecorderManager.onFrameRecorded(function listener)](./RecorderManager.onFrameRecorded.html)

监听已录制完指定帧大小的文件事件。如果设置了 frameSize，则会回调此事件。

### [#](#RecorderManager-onError-function-listener) [RecorderManager.onError(function listener)](./RecorderManager.onError.html)

监听录音错误事件

### [#](#RecorderManager-onInterruptionBegin-function-listener) [RecorderManager.onInterruptionBegin(function listener)](./RecorderManager.onInterruptionBegin.html)

监听录音因为受到系统占用而被中断开始事件。以下场景会触发此事件：微信语音聊天、微信视频聊天。此事件触发后，录音会被暂停。pause 事件在此事件后触发

### [#](#RecorderManager-onInterruptionEnd-function-listener) [RecorderManager.onInterruptionEnd(function listener)](./RecorderManager.onInterruptionEnd.html)

监听录音中断结束事件。在收到 interruptionBegin 事件之后，小程序内所有录音会暂停，收到此事件之后才可再次录音成功。

## [#](#示例代码) 示例代码

```
const recorderManager = wx.getRecorderManager()

recorderManager.onStart(() => {
  console.log('recorder start')
})
recorderManager.onPause(() => {
  console.log('recorder pause')
})
recorderManager.onStop((res) => {
  console.log('recorder stop', res)
  const { tempFilePath } = res
})
recorderManager.onFrameRecorded((res) => {
  const { frameBuffer } = res
  console.log('frameBuffer.byteLength', frameBuffer.byteLength)
})

const options = {
  duration: 10000,
  sampleRate: 44100,
  numberOfChannels: 1,
  encodeBitRate: 192000,
  format: 'aac',
  frameSize: 50
}

recorderManager.start(options)
```

Incorrect translation.