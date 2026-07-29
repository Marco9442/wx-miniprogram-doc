开放接口/设置/AuthSetting/
# [\#](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/setting/AuthSetting.html\#AuthSetting) AuthSetting
用户授权设置信息，详情参考 [权限](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/authorize.html)
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/setting/AuthSetting.html\#%E5%B1%9E%E6%80%A7) 属性
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/setting/AuthSetting.html\#boolean-scope-userInfo) boolean scope.userInfo
是否授权用户信息，对应接口 [wx.getUserInfo](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/user-info/wx.getUserInfo.html)
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/setting/AuthSetting.html\#boolean-scope-userLocation) boolean scope.userLocation
是否授权精确地理位置，对应接口 [wx.getLocation](https://developers.weixin.qq.com/miniprogram/dev/api/location/wx.getLocation.html), [wx.chooseLocation](https://developers.weixin.qq.com/miniprogram/dev/api/location/wx.chooseLocation.html)
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/setting/AuthSetting.html\#boolean-scope-userFuzzyLocation) boolean scope.userFuzzyLocation
是否授权模糊地理位置，对应接口 [wx.getFuzzyLocation](https://developers.weixin.qq.com/miniprogram/dev/api/location/wx.getFuzzyLocation.html)
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/setting/AuthSetting.html\#boolean-scope-address) boolean scope.address
是否授权通讯地址，已取消此项授权，会默认返回true
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/setting/AuthSetting.html\#boolean-scope-invoiceTitle) boolean scope.invoiceTitle
是否授权发票抬头，已取消此项授权，会默认返回true
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/setting/AuthSetting.html\#boolean-scope-invoice) boolean scope.invoice
是否授权获取发票，已取消此项授权，会默认返回true
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/setting/AuthSetting.html\#boolean-scope-werun) boolean scope.werun
是否授权微信运动步数，对应接口 [wx.getWeRunData](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/werun/wx.getWeRunData.html)
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/setting/AuthSetting.html\#boolean-scope-record) boolean scope.record
是否授权录音功能，对应接口 [wx.getRecorderManager](https://developers.weixin.qq.com/miniprogram/dev/api/media/recorder/wx.getRecorderManager.html)
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/setting/AuthSetting.html\#boolean-scope-writePhotosAlbum) boolean scope.writePhotosAlbum
是否授权保存到相册 [wx.saveImageToPhotosAlbum](https://developers.weixin.qq.com/miniprogram/dev/api/media/image/wx.saveImageToPhotosAlbum.html), [wx.saveVideoToPhotosAlbum](https://developers.weixin.qq.com/miniprogram/dev/api/media/video/wx.saveVideoToPhotosAlbum.html)
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/setting/AuthSetting.html\#boolean-scope-camera) boolean scope.camera
是否授权摄像头，对应\[ [camera](https://developers.weixin.qq.com/miniprogram/dev/component/camera.html)\]((camera)) 组件
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/setting/AuthSetting.html\#boolean-scope-bluetooth) boolean scope.bluetooth
是否授权蓝牙，对应接口 [wx.openBluetoothAdapter](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth/wx.openBluetoothAdapter.html)、 [wx.createBLEPeripheralServer](https://developers.weixin.qq.com/miniprogram/dev/api/device/bluetooth-peripheral/wx.createBLEPeripheralServer.html)
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/setting/AuthSetting.html\#boolean-scope-addPhoneContact) boolean scope.addPhoneContact
是否添加通讯录联系人，对应接口 [wx.addPhoneContact](https://developers.weixin.qq.com/miniprogram/dev/api/device/contact/wx.addPhoneContact.html)
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/setting/AuthSetting.html\#boolean-scope-addPhoneCalendar) boolean scope.addPhoneCalendar
是否授权系统日历，对应接口 [wx.addPhoneRepeatCalendar](https://developers.weixin.qq.com/miniprogram/dev/api/device/calendar/wx.addPhoneRepeatCalendar.html)、 [wx.addPhoneCalendar](https://developers.weixin.qq.com/miniprogram/dev/api/device/calendar/wx.addPhoneCalendar.html)