# [#](#LivePusherContext) LivePusherContext

> 相关文档: [live-pusher 组件](../../../component/live-pusher.html)

LivePusherContext 实例，可通过 [wx.createLivePusherContext](wx.createLivePusherContext.html) 获取。

[LivePusherContext](LivePusherContext.html) 与页面内唯一的 [live-pusher](../../../component/live-pusher.html) 组件绑定，操作对应的 [live-pusher](../../../component/live-pusher.html) 组件。

## [#](#方法) 方法

### [#](#LivePusherContext-start) [LivePusherContext.start()](LivePusherContext.start.html)

开始推流，同时开启摄像头预览

### [#](#LivePusherContext-stop) [LivePusherContext.stop()](LivePusherContext.stop.html)

停止推流，同时停止摄像头预览

### [#](#LivePusherContext-pause) [LivePusherContext.pause()](LivePusherContext.pause.html)

暂停推流

### [#](#LivePusherContext-resume) [LivePusherContext.resume()](LivePusherContext.resume.html)

恢复推流

### [#](#LivePusherContext-switchCamera) [LivePusherContext.switchCamera()](LivePusherContext.switchCamera.html)

切换前后摄像头

### [#](#LivePusherContext-snapshot-Object-object) [LivePusherContext.snapshot(Object object)](LivePusherContext.snapshot.html)

快照

### [#](#LivePusherContext-toggleTorch) [LivePusherContext.toggleTorch()](LivePusherContext.toggleTorch.html)

切换手电筒

### [#](#LivePusherContext-playBGM-Object-object) [LivePusherContext.playBGM(Object object)](LivePusherContext.playBGM.html)

播放背景音

### [#](#LivePusherContext-stopBGM) [LivePusherContext.stopBGM()](LivePusherContext.stopBGM.html)

停止背景音

### [#](#LivePusherContext-pauseBGM) [LivePusherContext.pauseBGM()](LivePusherContext.pauseBGM.html)

暂停背景音

### [#](#LivePusherContext-resumeBGM) [LivePusherContext.resumeBGM()](LivePusherContext.resumeBGM.html)

恢复背景音

### [#](#LivePusherContext-setBGMVolume-Object-object) [LivePusherContext.setBGMVolume(Object object)](LivePusherContext.setBGMVolume.html)

设置背景音音量

### [#](#LivePusherContext-setMICVolume-Object-object) [LivePusherContext.setMICVolume(Object object)](LivePusherContext.setMICVolume.html)

设置麦克风音量

### [#](#LivePusherContext-startPreview) [LivePusherContext.startPreview()](LivePusherContext.startPreview.html)

开启摄像头预览

### [#](#LivePusherContext-stopPreview) [LivePusherContext.stopPreview()](LivePusherContext.stopPreview.html)

关闭摄像头预览

### [#](#LivePusherContext-sendMessage-Object-object) [LivePusherContext.sendMessage(Object object)](LivePusherContext.sendMessage.html)

发送SEI消息

### [#](#LivePusherContext-exitPictureInPicture) [LivePusherContext.exitPictureInPicture()](LivePusherContext.exitPictureInPicture.html)

退出小窗，该方法可在任意页面调用

### [#](#LivePusherContext-setZoom-Object-object) [LivePusherContext.setZoom(Object object)](LivePusherContext.setZoom.html)

设置缩放级别

### [#](#LivePusherContext-getMaxZoom) [LivePusherContext.getMaxZoom()](LivePusherContext.getMaxZoom.html)

获取最大缩放级别

### [#](#LivePusherContext-applyFilter-Object-object) [LivePusherContext.applyFilter(Object object)](LivePusherContext.applyFilter.html)

添加滤镜效果

### [#](#LivePusherContext-clearFilters) [LivePusherContext.clearFilters()](LivePusherContext.clearFilters.html)

清除所有滤镜效果

### [#](#LivePusherContext-applySticker-Object-object) [LivePusherContext.applySticker(Object object)](LivePusherContext.applySticker.html)

添加贴纸特效

### [#](#LivePusherContext-clearStickers) [LivePusherContext.clearStickers()](LivePusherContext.clearStickers.html)

清除所有贴纸特效

### [#](#LivePusherContext-applyLipStickMakeup-Object-object) [LivePusherContext.applyLipStickMakeup(Object object)](LivePusherContext.applyLipStickMakeup.html)

添加口红美妆特效

### [#](#LivePusherContext-applyEyeShadowMakeup-Object-object) [LivePusherContext.applyEyeShadowMakeup(Object object)](LivePusherContext.applyEyeShadowMakeup.html)

添加眼影美妆特效

### [#](#LivePusherContext-applyBlusherStickMakeup-Object-object) [LivePusherContext.applyBlusherStickMakeup(Object object)](LivePusherContext.applyBlusherStickMakeup.html)

添加腮红美妆特效

### [#](#LivePusherContext-applyFaceContourMakeup-Object-object) [LivePusherContext.applyFaceContourMakeup(Object object)](LivePusherContext.applyFaceContourMakeup.html)

添加修容美妆特效

### [#](#LivePusherContext-applyEyeBrowMakeup-Object-object) [LivePusherContext.applyEyeBrowMakeup(Object object)](LivePusherContext.applyEyeBrowMakeup.html)

添加眉毛美妆特效

### [#](#LivePusherContext-clearMakeups) [LivePusherContext.clearMakeups()](LivePusherContext.clearMakeups.html)

清除所有美妆特效

### [#](#LivePusherContext-onCustomRendererEvent-string-event-LivePusherContext-customRendererFrameEventCallback-LivePusherContext-customRendererUpdateEventCallback-callback) [LivePusherContext.onCustomRendererEvent(string event, LivePusherContext.customRendererFrameEventCallback|LivePusherContext.customRendererUpdateEventCallback callback)](LivePusherContext.onCustomRendererEvent.html)

开启自定义渲染时，开发者通过此方法订阅相关事件，客户端 8.0.31 版本开始支持。

### [#](#LivePusherContext-createOffscreenCanvas-object-options) [LivePusherContext.createOffscreenCanvas(object options)](LivePusherContext.createOffscreenCanvas.html)

创建一个能够承接 LivePusher 采集纹理的离屏 Canvas，客户端 8.0.31 版本开始支持。

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/KvWD9mmA62Yk "在开发者工具中预览效果")

Incorrect translation.