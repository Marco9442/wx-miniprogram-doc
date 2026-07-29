# [#](#插件调用-API-的限制) 插件调用 API 的限制

插件可以调用的 API 与小程序不同，主要有两个区别：

- 插件的请求域名列表与小程序相互独立；
- 一些 API 不允许插件调用（这些函数不存在于 `wx` 对象下）。

有些接口虽然在插件中不能使用，但可以通过插件功能页来达到目的，请参考 [插件功能页](functional-pages)。

各接口在插件中的支持情况可以在各接口的文档中确认，接口文档中会有如 *「本接口从基础库 2.1.0 起支持在小程序插件中使用」* 的标识；如果没有标识，说明插件暂未支持，如果有需要的具体使用场景和需求，可以在开发者社区中反馈。

以下表格汇总了目前插件可以调用的 API 及其对应版本要求，**但这份表格已经不再更新，是否可以使用，请以具体接口文档中的说明和真机表现为准**。

插件支持接口情况参考汇总（表格已停止维护）

### [#](#基础) 基础

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.arrayBufferToBase64](https://developers.weixin.qq.com/miniprogram/dev/api/base/wx.arrayBufferToBase64.html) |  |  |
| [wx.base64ToArrayBuffer](https://developers.weixin.qq.com/miniprogram/dev/api/base/wx.base64ToArrayBuffer.html) |  |  |

### [#](#发起请求) 发起请求

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.request](https://developers.weixin.qq.com/miniprogram/dev/api/network/request/wx.request.html) | ['1.9.6'](../compatibility) |  |

### [#](#上传、下载) 上传、下载

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.downloadFile](https://developers.weixin.qq.com/miniprogram/dev/api/network/download/wx.downloadFile.html) | ['1.9.6'](../compatibility) |  |
| [wx.uploadFile](https://developers.weixin.qq.com/miniprogram/dev/api/network/upload/wx.uploadFile.html) | ['1.9.6'](../compatibility) |  |

### [#](#WebSocket) WebSocket

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.connectSocket](https://developers.weixin.qq.com/miniprogram/dev/api/network/websocket/SocketTask.html) | ['1.9.6'](../compatibility) |  |

### [#](#图片) 图片

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.previewImage](https://developers.weixin.qq.com/miniprogram/dev/api/media/image/wx.previewImage.html) | ['1.9.6'](../compatibility) |  |
| [wx.chooseImage](https://developers.weixin.qq.com/miniprogram/dev/api/media/image/wx.chooseImage.html) | ['1.9.6'](../compatibility) |  |
| [wx.getImageInfo](https://developers.weixin.qq.com/miniprogram/dev/api/media/image/wx.getImageInfo.html) | ['1.9.6'](../compatibility) |  |
| [wx.saveImageToPhotosAlbum](https://developers.weixin.qq.com/miniprogram/dev/api/media/image/wx.saveImageToPhotosAlbum.html) | ['1.9.6'](../compatibility) |  |

### [#](#录音) 录音

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.startRecord](https://developers.weixin.qq.com/miniprogram/dev/api/media/recorder/wx.startRecord.html) | ['1.9.6'](../compatibility) |  |
| [wx.stopRecord](https://developers.weixin.qq.com/miniprogram/dev/api/media/recorder/wx.startRecord.html) | ['1.9.6'](../compatibility) |  |

### [#](#实时音视频) 实时音视频

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.createLivePlayerContext](https://developers.weixin.qq.com/miniprogram/dev/api/wxml/NodesRef.context.html) | ['1.9.6'](../compatibility) |  |
| [wx.createLivePusherContext](https://developers.weixin.qq.com/miniprogram/dev/api/media/live/LivePusherContext.html) | ['1.9.6'](../compatibility) |  |

### [#](#录音管理) 录音管理

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.getRecorderManager](https://developers.weixin.qq.com/miniprogram/dev/api/media/recorder/wx.getRecorderManager.html) | ['1.9.94'](../compatibility) |  |

### [#](#音频播放控制) 音频播放控制

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.pauseVoice](https://developers.weixin.qq.com/miniprogram/dev/api/media/audio/wx.pauseVoice.html) | ['1.9.6'](../compatibility) |  |
| [wx.playVoice](https://developers.weixin.qq.com/miniprogram/dev/api/media/audio/wx.playVoice.html) | ['1.9.6'](../compatibility) |  |
| [wx.stopVoice](https://developers.weixin.qq.com/miniprogram/dev/api/media/audio/wx.pauseVoice.html) | ['1.9.6'](../compatibility) |  |

### [#](#音乐播放控制) 音乐播放控制

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.onBackgroundAudioPlay](https://developers.weixin.qq.com/miniprogram/dev/api/media/background-audio/wx.onBackgroundAudioPlay.html) | ['1.9.6'](../compatibility) |  |
| [wx.getBackgroundAudioPlayerState](https://developers.weixin.qq.com/miniprogram/dev/api/media/background-audio/wx.getBackgroundAudioPlayerState.html) | ['1.9.6'](../compatibility) |  |
| [wx.onBackgroundAudioStop](https://developers.weixin.qq.com/miniprogram/dev/api/media/background-audio/wx.onBackgroundAudioStop.html) | ['1.9.6'](../compatibility) |  |
| [wx.stopBackgroundAudio](https://developers.weixin.qq.com/miniprogram/dev/api/media/background-audio/wx.stopBackgroundAudio.html) | ['1.9.6'](../compatibility) |  |
| [wx.onBackgroundAudioPause](https://developers.weixin.qq.com/miniprogram/dev/api/media/background-audio/wx.onBackgroundAudioPause.html) | ['1.9.6'](../compatibility) |  |
| [wx.seekBackgroundAudio](https://developers.weixin.qq.com/miniprogram/dev/api/media/background-audio/wx.seekBackgroundAudio.html) | ['1.9.6'](../compatibility) |  |
| [wx.playBackgroundAudio](https://developers.weixin.qq.com/miniprogram/dev/api/media/background-audio/wx.playBackgroundAudio.html) | ['1.9.6'](../compatibility) |  |
| [wx.pauseBackgroundAudio](https://developers.weixin.qq.com/miniprogram/dev/api/media/background-audio/wx.pauseBackgroundAudio.html) | ['1.9.6'](../compatibility) |  |

### [#](#背景音频播放管理) 背景音频播放管理

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.getBackgroundAudioManager](https://developers.weixin.qq.com/miniprogram/dev/api/media/background-audio/BackgroundAudioManager.html) | ['1.9.6'](../compatibility) |  |

### [#](#音频组件控制) 音频组件控制

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.createInnerAudioContext](https://developers.weixin.qq.com/miniprogram/dev/api/media/audio/InnerAudioContext.onCanplay.html) | ['1.9.6'](../compatibility) |  |
| [wx.createAudioContext](https://developers.weixin.qq.com/miniprogram/dev/api/media/audio/AudioContext.html) | ['1.9.6'](../compatibility) |  |

### [#](#视频) 视频

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.chooseVideo](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/wx.chooseVideo.html) | ['1.9.6'](../compatibility) |  |
| [wx.saveVideoToPhotosAlbum](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/wx.saveVideoToPhotosAlbum.html) | ['1.9.6'](../compatibility) |  |

### [#](#视频组件控制) 视频组件控制

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.createVideoContext](https://developers.weixin.qq.com/miniprogram/dev/api/wxml/NodesRef.context.html) | ['1.9.6'](../compatibility) |  |

### [#](#相机组件控制) 相机组件控制

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.createCameraContext](https://developers.weixin.qq.com/miniprogram/dev/api/media/camera/CameraContext.html) | ['1.9.6'](../compatibility) |  |

### [#](#数据缓存) 数据缓存

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.setStorage](https://developers.weixin.qq.com/miniprogram/dev/api/storage/wx.setStorage.html) | ['1.9.6'](../compatibility) |  |
| [wx.getStorage](https://developers.weixin.qq.com/miniprogram/dev/api/storage/wx.getStorage.html) | ['1.9.6'](../compatibility) |  |
| [wx.removeStorage](https://developers.weixin.qq.com/miniprogram/dev/api/storage/wx.removeStorage.html) | ['1.9.6'](../compatibility) |  |
| [wx.setStorageSync](https://developers.weixin.qq.com/miniprogram/dev/api/storage/wx.setStorageSync.html) | ['1.9.6'](../compatibility) |  |
| [wx.getStorageSync](https://developers.weixin.qq.com/miniprogram/dev/api/storage/wx.getStorageSync.html) | ['1.9.6'](../compatibility) |  |
| [wx.removeStorageSync](https://developers.weixin.qq.com/miniprogram/dev/api/storage/wx.removeStorageSync.html) | ['1.9.6'](../compatibility) |  |

### [#](#获取位置) 获取位置

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.getLocation](https://developers.weixin.qq.com/miniprogram/dev/api/location/wx.getLocation.html) | ['1.9.6'](../compatibility) |  |
| [wx.chooseLocation](https://developers.weixin.qq.com/miniprogram/dev/api/location/wx.chooseLocation.html) | ['1.9.6'](../compatibility) |  |
| [wx.onLocationChange](https://developers.weixin.qq.com/miniprogram/dev/api/location/wx.getLocation.html) | ['2.8.0'](../compatibility) |  |
| [wx.offLocationChange](https://developers.weixin.qq.com/miniprogram/dev/api/location/wx.offLocationChange.html) | ['2.9.1'](../compatibility) |  |
| [wx.stopLocationUpdate](https://developers.weixin.qq.com/miniprogram/dev/api/location/wx.stopLocationUpdate.html) | ['2.8.0'](../compatibility) |  |
| [wx.startLocationUpdate](https://developers.weixin.qq.com/miniprogram/dev/api/location/wx.getLocation.html) | ['2.8.0'](../compatibility) |  |

### [#](#查看位置) 查看位置

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.openLocation](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/MapContext.getCenterLocation.html) | ['1.9.6'](../compatibility) |  |

### [#](#地图组件控制) 地图组件控制

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.createMapContext](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/wx.createMapContext.html) | ['1.9.6'](../compatibility) |  |

### [#](#系统信息) 系统信息

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.getSystemInfoSync](https://developers.weixin.qq.com/miniprogram/dev/api/base/system/wx.getSystemInfoSync.html) | ['1.9.6'](../compatibility) |  |
| [wx.getSystemInfo](https://developers.weixin.qq.com/miniprogram/dev/api/base/system/wx.getSystemInfo.html) | ['1.9.6'](../compatibility) |  |

### [#](#屏幕亮度) 屏幕亮度

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.setKeepScreenOn](https://developers.weixin.qq.com/miniprogram/dev/api/device/screen/wx.setKeepScreenOn.html) | ['1.9.6'](../compatibility) |  |
| [wx.setScreenBrightness](https://developers.weixin.qq.com/miniprogram/dev/api/device/screen/wx.setScreenBrightness.html) | ['1.9.6'](../compatibility) |  |
| [wx.getScreenBrightness](https://developers.weixin.qq.com/miniprogram/dev/api/device/screen/wx.getScreenBrightness.html) | ['1.9.6'](../compatibility) |  |

### [#](#用户截屏事件) 用户截屏事件

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.onUserCaptureScreen](https://developers.weixin.qq.com/miniprogram/dev/api/device/screen/wx.onUserCaptureScreen.html) | ['1.9.6 '](../compatibility) | 仅限插件页面中调用 |
| [wx.offUserCaptureScreen](https://developers.weixin.qq.com/miniprogram/dev/api/device/screen/wx.offUserCaptureScreen.html) | ['2.9.1'](../compatibility) | 仅限插件页面中调用 |

### [#](#振动) 振动

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.vibrateLong](https://developers.weixin.qq.com/miniprogram/dev/api/device/vibrate/wx.vibrateLong.html) | ['1.9.6'](../compatibility) |  |
| [wx.vibrateShort](https://developers.weixin.qq.com/miniprogram/dev/api/device/vibrate/wx.vibrateShort.html) | ['1.9.6'](../compatibility) |  |

### [#](#手机联系人) 手机联系人

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.addPhoneContact](https://developers.weixin.qq.com/miniprogram/dev/api/device/contact/wx.addPhoneContact.html) | ['1.9.6'](../compatibility) |  |

### [#](#NFC) NFC

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.sendHCEMessage](https://developers.weixin.qq.com/miniprogram/dev/api/device/nfc-hce/wx.sendHCEMessage.html) | ['2.1.0'](../compatibility) |  |
| [wx.stopHCE](https://developers.weixin.qq.com/miniprogram/dev/api/device/nfc-hce/wx.stopHCE.html) | ['2.1.0'](../compatibility) |  |
| [wx.onHCEMessage](https://developers.weixin.qq.com/miniprogram/dev/api/device/nfc-hce/wx.onHCEMessage.html) | ['2.1.0'](../compatibility) |  |
| [wx.offHCEMessage](https://developers.weixin.qq.com/miniprogram/dev/api/device/nfc-hce/wx.offHCEMessage.html) | ['2.9.1'](../compatibility) |  |
| [wx.startHCE](https://developers.weixin.qq.com/miniprogram/dev/api/device/nfc-hce/wx.startHCE.html) | ['2.1.0'](../compatibility) |  |
| [wx.getHCEState](https://developers.weixin.qq.com/miniprogram/dev/api/device/nfc-hce/wx.getHCEState.html) | ['2.1.0'](../compatibility) |  |

### [#](#网络状态) 网络状态

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.onNetworkStatusChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/network/wx.onNetworkStatusChange.html) | ['1.9.6'](../compatibility) |  |
| [wx.offNetworkStatusChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/network/wx.offNetworkStatusChange.html) | ['2.9.1'](../compatibility) |  |
| [wx.getNetworkType](https://developers.weixin.qq.com/miniprogram/dev/api/device/network/wx.getNetworkType.html) | ['1.9.6'](../compatibility) |  |

### [#](#加速度计) 加速度计

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.startAccelerometer](https://developers.weixin.qq.com/miniprogram/dev/api/device/accelerometer/wx.startAccelerometer.html) | ['1.9.6'](../compatibility) |  |
| [wx.stopAccelerometer](https://developers.weixin.qq.com/miniprogram/dev/api/device/accelerometer/wx.stopAccelerometer.html) | ['1.9.6'](../compatibility) |  |
| [wx.onAccelerometerChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/accelerometer/wx.onAccelerometerChange.html) | ['1.9.6'](../compatibility) |  |
| [wx.offAccelerometerChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/accelerometer/wx.offAccelerometerChange.html) | ['2.9.1'](../compatibility) |  |

### [#](#设备方向) 设备方向

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.startDeviceMotionListening](https://developers.weixin.qq.com/miniprogram/dev/api/device/motion/wx.startDeviceMotionListening.html) | ['2.9.1'](../compatibility) |  |
| [wx.stopDeviceMotionListening](https://developers.weixin.qq.com/miniprogram/dev/api/device/motion/wx.stopDeviceMotionListening.html) | ['2.9.1'](../compatibility) |  |
| [wx.offDeviceMotionChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/motion/wx.offDeviceMotionChange.html) | ['2.9.1'](../compatibility) |  |
| [wx.onDeviceMotionChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/motion/wx.onDeviceMotionChange.html) | ['2.9.1'](../compatibility) |  |

### [#](#陀螺仪) 陀螺仪

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.startGyroscope](https://developers.weixin.qq.com/miniprogram/dev/api/device/gyroscope/wx.startGyroscope.html) | ['2.9.1'](../compatibility) |  |
| [wx.stopGyroscope](https://developers.weixin.qq.com/miniprogram/dev/api/device/gyroscope/wx.stopGyroscope.html) | ['2.9.1'](../compatibility) |  |
| [wx.offGyroscopeChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/gyroscope/wx.offGyroscopeChange.html) | ['2.9.1'](../compatibility) |  |
| [wx.onGyroscopeChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/gyroscope/wx.onGyroscopeChange.html) | ['2.9.1'](../compatibility) |  |

### [#](#罗盘) 罗盘

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.onCompassChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/compass/wx.onCompassChange.html) | ['1.9.6'](../compatibility) |  |
| [wx.offCompassChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/compass/wx.offCompassChange.html) | ['2.9.1'](../compatibility) |  |
| [wx.stopCompass](https://developers.weixin.qq.com/miniprogram/dev/api/device/compass/wx.stopCompass.html) | ['1.9.6'](../compatibility) |  |
| [wx.startCompass](https://developers.weixin.qq.com/miniprogram/dev/api/device/compass/wx.startCompass.html) | ['1.9.6'](../compatibility) |  |

### [#](#拨打电话) 拨打电话

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.makePhoneCall](https://developers.weixin.qq.com/miniprogram/dev/api/device/phone/wx.makePhoneCall.html) | ['1.9.6'](../compatibility) |  |

### [#](#扫码) 扫码

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.scanCode](https://developers.weixin.qq.com/miniprogram/dev/api/device/scan/wx.scanCode.html) | ['1.9.6'](../compatibility) |  |

### [#](#剪贴板) 剪贴板

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.setClipboardData](https://developers.weixin.qq.com/miniprogram/dev/api/device/clipboard/wx.setClipboardData.html) | ['1.9.6'](../compatibility) |  |
| [wx.getClipboardData](https://developers.weixin.qq.com/miniprogram/dev/api/device/clipboard/wx.getClipboardData.html) | ['1.9.6'](../compatibility) |  |

### [#](#蓝牙) 蓝牙

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.writeBLECharacteristicValue](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth-ble/wx.writeBLECharacteristicValue.html) | ['1.9.6'](../compatibility) |  |
| [wx.startBluetoothDevicesDiscovery](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth/wx.startBluetoothDevicesDiscovery.html) | ['1.9.6'](../compatibility) |  |
| [wx.getConnectedBluetoothDevices](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth/wx.getConnectedBluetoothDevices.html) | ['1.9.6'](../compatibility) |  |
| [wx.notifyBLECharacteristicValueChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth-ble/wx.notifyBLECharacteristicValueChange.html) | ['1.9.6'](../compatibility) |  |
| [wx.onBluetoothDeviceFound](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth/wx.onBluetoothDeviceFound.html) | ['1.9.6'](../compatibility) |  |
| [wx.offBluetoothDeviceFound](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth/wx.offBluetoothDeviceFound.html) | ['2.9.1'](../compatibility) |  |
| [wx.readBLECharacteristicValue](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth-ble/wx.readBLECharacteristicValue.html) | ['1.9.6'](../compatibility) |  |
| [wx.openBluetoothAdapter](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth/wx.closeBluetoothAdapter.html) | ['1.9.6'](../compatibility) |  |
| [wx.getBLEDeviceCharacteristics](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth-ble/wx.getBLEDeviceCharacteristics.html) | ['1.9.6'](../compatibility) |  |
| [wx.stopBluetoothDevicesDiscovery](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth/wx.startBluetoothDevicesDiscovery.html) | ['1.9.6'](../compatibility) |  |
| [wx.onBLEConnectionStateChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth-ble/wx.onBLEConnectionStateChange.html) | ['1.9.6'](../compatibility) |  |
| [wx.getBluetoothDevices](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth/wx.getBluetoothDevices.html) | ['1.9.6'](../compatibility) |  |
| [wx.getBluetoothAdapterState](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth/wx.getBluetoothAdapterState.html) | ['1.9.6'](../compatibility) |  |
| [wx.onBluetoothAdapterStateChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth/wx.onBluetoothAdapterStateChange.html) | ['1.9.6'](../compatibility) |  |
| [wx.offBluetoothAdapterStateChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth/wx.offBluetoothAdapterStateChange.html) | ['2.9.1'](../compatibility) |  |
| [wx.getBLEDeviceServices](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth-ble/wx.getBLEDeviceServices.html) | ['1.9.6'](../compatibility) |  |
| [wx.onBLECharacteristicValueChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth-ble/wx.onBLECharacteristicValueChange.html) | ['1.9.6'](../compatibility) |  |
| [wx.offBLECharacteristicValueChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth-ble/wx.offBLECharacteristicValueChange.html) | ['2.9.1'](../compatibility) |  |
| [wx.createBLEConnection](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth/wx.makeBluetoothPair.html) | ['1.9.6'](../compatibility) |  |
| [wx.closeBluetoothAdapter](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth/wx.closeBluetoothAdapter.html) | ['1.9.6'](../compatibility) |  |
| [wx.closeBLEConnection](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth-ble/wx.closeBLEConnection.html) | ['1.9.6'](../compatibility) |  |
| [wx.notifyBLECharacteristicValueChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth-ble/wx.notifyBLECharacteristicValueChange.html) | ['1.9.6'](../compatibility) |  |
| [wx.onBLEConnectionStateChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth-ble/wx.onBLEConnectionStateChange.html) | ['1.9.6'](../compatibility) |  |
| [wx.offBLEConnectionStateChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth-ble/wx.offBLEConnectionStateChange.html) | ['2.9.1'](../compatibility) |  |

### [#](#iBeacon) iBeacon

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.getBeacons](https://developers.weixin.qq.com/miniprogram/dev/api/device/ibeacon/wx.getBeacons.html) | ['1.9.6'](../compatibility) |  |
| [wx.startBeaconDiscovery](https://developers.weixin.qq.com/miniprogram/dev/api/device/ibeacon/wx.startBeaconDiscovery.html) | ['1.9.6'](../compatibility) |  |
| [wx.onBeaconServiceChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/ibeacon/wx.onBeaconServiceChange.html) | ['1.9.6'](../compatibility) |  |
| [wx.offBeaconServiceChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/ibeacon/wx.offBeaconServiceChange.html) | ['2.9.1'](../compatibility) |  |
| [wx.onBeaconUpdate](https://developers.weixin.qq.com/miniprogram/dev/api/device/ibeacon/wx.onBeaconUpdate.html) | ['1.9.6'](../compatibility) |  |
| [wx.offBeaconUpdate](https://developers.weixin.qq.com/miniprogram/dev/api/device/ibeacon/wx.offBeaconUpdate.html) | ['2.9.1'](../compatibility) |  |
| [wx.stopBeaconDiscovery](https://developers.weixin.qq.com/miniprogram/dev/api/device/ibeacon/wx.stopBeaconDiscovery.html) | ['1.9.6'](../compatibility) |  |

### [#](#Wi-Fi) Wi-Fi

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.connectWifi](https://developers.weixin.qq.com/miniprogram/dev/api/device/wifi/wx.connectWifi.html) | ['2.9.1'](../compatibility) |  |
| [wx.getConnectedWifi](https://developers.weixin.qq.com/miniprogram/dev/api/device/wifi/wx.getConnectedWifi.html) | ['2.9.1'](../compatibility) |  |
| [wx.getWifiList](https://developers.weixin.qq.com/miniprogram/dev/api/device/wifi/wx.getWifiList.html) | ['2.9.1'](../compatibility) |  |
| [wx.offGetWifiList](https://developers.weixin.qq.com/miniprogram/dev/api/device/wifi/wx.offGetWifiList.html) | ['2.9.1'](../compatibility) |  |
| [wx.offWifiConnected](https://developers.weixin.qq.com/miniprogram/dev/api/device/wifi/wx.offWifiConnected.html) | ['2.9.1'](../compatibility) |  |
| wx.onEvaluateWifi | ['2.9.1'](../compatibility) |  |
| [wx.onGetWifiList](https://developers.weixin.qq.com/miniprogram/dev/api/device/wifi/wx.getWifiList.html) | ['2.9.1'](../compatibility) |  |
| [wx.onWifiConnected](https://developers.weixin.qq.com/miniprogram/dev/api/device/wifi/wx.onWifiConnected.html) | ['2.9.1'](../compatibility) |  |
| wx.presetWifiList | ['2.9.1'](../compatibility) |  |
| [wx.setWifiList](https://developers.weixin.qq.com/miniprogram/dev/api/device/wifi/wx.setWifiList.html) | ['2.9.1'](../compatibility) |  |
| [wx.startWifi](https://developers.weixin.qq.com/miniprogram/dev/api/device/wifi/wx.startWifi.html) | ['2.9.1'](../compatibility) |  |
| [wx.stopWifi](https://developers.weixin.qq.com/miniprogram/dev/api/device/wifi/wx.stopWifi.html) | ['2.9.1'](../compatibility) |  |

### [#](#交互反馈) 交互反馈

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.hideLoading](https://developers.weixin.qq.com/miniprogram/dev/api/ui/interaction/wx.showLoading.html) | ['1.9.6'](../compatibility) |  |
| [wx.showActionSheet](https://developers.weixin.qq.com/miniprogram/dev/api/ui/interaction/wx.showActionSheet.html) | ['1.9.6'](../compatibility) |  |
| [wx.showLoading](https://developers.weixin.qq.com/miniprogram/dev/api/ui/interaction/wx.showLoading.html) | ['1.9.6'](../compatibility) |  |
| [wx.hideToast](https://developers.weixin.qq.com/miniprogram/dev/api/ui/interaction/wx.hideToast.html) | ['1.9.6'](../compatibility) |  |
| [wx.showToast](https://developers.weixin.qq.com/miniprogram/dev/api/ui/interaction/wx.showToast.html) | ['1.9.6'](../compatibility) |  |
| [wx.showModal](https://developers.weixin.qq.com/miniprogram/dev/api/ui/interaction/wx.showModal.html) | ['1.9.6'](../compatibility) |  |

### [#](#设置导航条) 设置导航条

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.showNavigationBarLoading](https://developers.weixin.qq.com/miniprogram/dev/api/ui/navigation-bar/wx.showNavigationBarLoading.html) | ['2.1.0 '](../compatibility) | 仅限插件页面中调用 |
| [wx.hideNavigationBarLoading](https://developers.weixin.qq.com/miniprogram/dev/api/ui/navigation-bar/wx.hideNavigationBarLoading.html) | ['2.1.0 '](../compatibility) | 仅限插件页面中调用 |
| [wx.setNavigationBarColor](https://developers.weixin.qq.com/miniprogram/dev/api/ui/navigation-bar/wx.setNavigationBarColor.html) | ['2.1.0 '](../compatibility) | 仅限插件页面中调用 |
| [wx.setNavigationBarTitle](https://developers.weixin.qq.com/miniprogram/dev/api/ui/navigation-bar/wx.setNavigationBarTitle.html) | ['2.1.0 '](../compatibility) | 仅限插件页面中调用 |

### [#](#背景) 背景

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.setBackgroundColor](https://developers.weixin.qq.com/miniprogram/dev/api/ui/background/wx.setBackgroundColor.html) | ['2.4.0 '](../compatibility) | 仅限插件页面中调用 |
| [wx.setBackgroundTextStyle](https://developers.weixin.qq.com/miniprogram/dev/api/ui/background/wx.setBackgroundTextStyle.html) | ['2.4.0 '](../compatibility) | 仅限插件页面中调用 |

### [#](#WXML-节点信息) WXML 节点信息

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.createSelectorQuery](https://developers.weixin.qq.com/miniprogram/dev/api/media/map/wx.createMapContext.html) | ['1.9.6'](../compatibility) |  |

### [#](#WXML-节点布局相交状态) WXML 节点布局相交状态

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.createIntersectionObserver](https://developers.weixin.qq.com/miniprogram/dev/api/wxml/wx.createIntersectionObserver.html) | ['1.9.6'](../compatibility) |  |

### [#](#导航) 导航

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.navigateBack](https://developers.weixin.qq.com/miniprogram/dev/api/navigate/wx.navigateBackMiniProgram.html) | ['2.1.0 '](../compatibility) | 仅限插件页面中调用 |
| [wx.navigateTo](https://developers.weixin.qq.com/miniprogram/dev/api/navigate/wx.navigateToMiniProgram.html) | ['2.2.2'](../compatibility) | 仅限插件页面中调用 |
| [wx.redirectTo](https://developers.weixin.qq.com/miniprogram/dev/api/route/wx.redirectTo.html) | ['2.2.2'](../compatibility) | 仅限插件页面中调用 |
| [wx.switchTab](https://developers.weixin.qq.com/miniprogram/dev/api/route/wx.switchTab.html) | ['2.3.1 '](../compatibility) | 仅限插件页面中调用 |
| [wx.reLaunch](https://developers.weixin.qq.com/miniprogram/dev/api/route/wx.reLaunch.html) | ['2.3.1 '](../compatibility) | 仅限插件页面中调用 |

### [#](#动画) 动画

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.createAnimation](https://developers.weixin.qq.com/miniprogram/dev/api/ui/animation/wx.createAnimation.html) | ['1.9.6'](../compatibility) |  |

### [#](#位置) 位置

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.pageScrollTo](https://developers.weixin.qq.com/miniprogram/dev/api/ui/scroll/wx.pageScrollTo.html) | ['2.1.0 '](../compatibility) | 仅限插件页面中调用 |

### [#](#绘图) 绘图

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.createOffscreenCanvas](https://developers.weixin.qq.com/miniprogram/dev/api/canvas/OffscreenCanvas.html) | ['2.7.1'](../compatibility) |  |
| [wx.canvasPutImageData](https://developers.weixin.qq.com/miniprogram/dev/api/canvas/wx.canvasPutImageData.html) | ['1.9.6'](../compatibility) |  |
| [wx.canvasToTempFilePath](https://developers.weixin.qq.com/miniprogram/dev/api/canvas/wx.canvasToTempFilePath.html) | ['1.9.6'](../compatibility) |  |
| [wx.createCanvasContext](https://developers.weixin.qq.com/miniprogram/dev/api/canvas/wx.createCanvasContext.html) | ['1.9.6'](../compatibility) |  |
| [wx.canvasGetImageData](https://developers.weixin.qq.com/miniprogram/dev/api/canvas/wx.canvasGetImageData.html) | ['1.9.6'](../compatibility) |  |

### [#](#下拉刷新) 下拉刷新

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.stopPullDownRefresh](https://developers.weixin.qq.com/miniprogram/dev/api/ui/pull-down-refresh/wx.stopPullDownRefresh.html) | ['2.1.0 '](../compatibility) | 仅限插件页面中调用 |
| [wx.startPullDownRefresh](https://developers.weixin.qq.com/miniprogram/dev/api/ui/pull-down-refresh/wx.startPullDownRefresh.html) | ['2.1.0 '](../compatibility) | 仅限插件页面中调用 |

### [#](#当前账号信息) 当前账号信息

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.getAccountInfoSync](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/account-info/wx.getAccountInfoSync.html) | ['2.2.2'](../compatibility) |  |

### [#](#转发) 转发

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.hideShareMenu](https://developers.weixin.qq.com/miniprogram/dev/api/share/wx.hideShareMenu.html) | ['2.1.0 '](../compatibility) | 仅限插件页面中调用 |
| [wx.getShareInfo](https://developers.weixin.qq.com/miniprogram/dev/api/share/wx.getShareInfo.html) | ['2.1.0 '](../compatibility) | 仅限插件页面中调用 |
| [wx.showShareMenu](https://developers.weixin.qq.com/miniprogram/dev/api/share/wx.showShareMenu.html) | ['2.1.0 '](../compatibility) | 仅限插件页面中调用 |
| [wx.updateShareMenu](https://developers.weixin.qq.com/miniprogram/dev/api/share/wx.updateShareMenu.html) | ['2.1.0 '](../compatibility) | 仅限插件页面中调用 |

### [#](#实时日志) 实时日志

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.getRealtimeLogManager](https://developers.weixin.qq.com/miniprogram/dev/api/base/debug/wx.getRealtimeLogManager.html) | ['2.16.0'](../compatibility) |  |

### [#](#其他) 其他

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.getSetting](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/subscribe-message/wx.requestSubscribeDeviceMessage.html) | ['2.6.3'](../compatibility) |  |
| [wx.openSetting](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/setting/wx.openSetting.html) | ['2.10.3'](../compatibility) |  |
| [wx.reportAnalytics](https://developers.weixin.qq.com/miniprogram/dev/api/data-analysis/wx.reportAnalytics.html) | ['1.9.6 '](../compatibility) | 见下方备注 |

### [#](#登录和获取用户信息) 登录和获取用户信息

**这一组接口仅限在用户信息功能页中获得用户授权之后调用。否则将返回 fail 。详见 [用户信息功能页](functional-pages/user-info) 。**

| API | 最低版本 | 备注 |
| --- | --- | --- |
| [wx.login](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/login/wx.login.html) | ['2.3.1'](../compatibility) |  |
| [wx.getUserInfo](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/user-info/wx.getUserInfo.html) | ['2.3.1 '](../compatibility) |  |

## [#](#Bugs-Tips) Bugs & Tips

- [wx.reportAnalytics](https://developers.weixin.qq.com/miniprogram/dev/api/data-analysis/wx.reportAnalytics.html) 可以被正常调用，但目前不会进行统计展示。

Incorrect translation.