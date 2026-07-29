# [#](#MediaRecorder) MediaRecorder

> 基础库 2.11.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

可通过 [wx.createMediaRecorder](wx.createMediaRecorder.html) 创建。

[MediaRecorder](MediaRecorder.html) WebGL 画面录制器，可以进行录制相关操作，在结束录制时导出视频文件

## [#](#方法) 方法

### [#](#Promise-MediaRecorder-pause) [Promise MediaRecorder.pause()](MediaRecorder.pause.html)

暂停录制

### [#](#Promise-MediaRecorder-resume) [Promise MediaRecorder.resume()](MediaRecorder.resume.html)

恢复录制

### [#](#Promise-MediaRecorder-start) [Promise MediaRecorder.start()](MediaRecorder.start.html)

开始录制

### [#](#Promise-MediaRecorder-stop) [Promise MediaRecorder.stop()](MediaRecorder.stop.html)

结束录制

### [#](#Promise-MediaRecorder-requestFrame-function-callback) [Promise MediaRecorder.requestFrame(function callback)](MediaRecorder.requestFrame.html)

请求下一帧录制，在 callback 里完成一帧渲染后开始录制当前帧

### [#](#MediaRecorder-on-string-eventName-function-callback) [MediaRecorder.on(string eventName, function callback)](MediaRecorder.on.html)

注册监听录制事件的回调函数。当对应事件触发时，回调函数会被执行。

### [#](#MediaRecorder-off-string-eventName-function-callback) [MediaRecorder.off(string eventName, function callback)](MediaRecorder.off.html)

取消监听录制事件。当对应事件触发时，该回调函数不再执行。

### [#](#Promise-MediaRecorder-destroy) [Promise MediaRecorder.destroy()](MediaRecorder.destroy.html)

销毁录制器

Incorrect translation.