# [#](#MediaContainer) MediaContainer

> 基础库 2.9.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

可通过 [wx.createMediaContainer](wx.createMediaContainer.html) 创建。

[MediaContainer](MediaContainer.html) 音视频处理容器，可以进行音频混音等操作

## [#](#方法) 方法

### [#](#MediaContainer-extractDataSource-Object-object) [MediaContainer.extractDataSource(Object object)](MediaContainer.extractDataSource.html)

将传入的视频源分离轨道。不会自动将轨道添加到待合成的容器里。

### [#](#MediaContainer-addTrack-MediaTrack-track) [MediaContainer.addTrack(MediaTrack track)](MediaContainer.addTrack.html)

将音频或视频轨道添加到容器

### [#](#MediaContainer-removeTrack-MediaTrack-track) [MediaContainer.removeTrack(MediaTrack track)](MediaContainer.removeTrack.html)

将音频或视频轨道从容器中移除

### [#](#MediaContainer-export) [MediaContainer.export()](MediaContainer.export.html)

将容器内的轨道合并并导出视频文件

### [#](#MediaContainer-destroy) [MediaContainer.destroy()](MediaContainer.destroy.html)

将容器销毁，释放资源

Incorrect translation.