# [#](#WifiInfo) WifiInfo

> 相关文档: [无线局域网 (Wi-Fi)](../../../framework/device/wifi.html)

Wifi 信息

## [#](#属性) 属性

### [#](#string-SSID) string SSID

Wi-Fi 的 SSID

### [#](#string-BSSID) string BSSID

Wi-Fi 的 BSSID

### [#](#boolean-secure) boolean secure

Wi-Fi 是否安全

### [#](#number-signalStrength) number signalStrength

Wi-Fi 信号强度, 安卓取值 0 ～ 100 ，iOS 取值 0 ～ 1 ，值越大强度越大

### [#](#number-frequency) number frequency

> 基础库 2.12.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

Wi-Fi 频段单位 MHz

## [#](#注意) 注意

- 安卓 wx.connectWifi / wx.getConnectedWifi 若设置了 partialInfo:true ，或者调用了 wx.onWifiConnectedWithPartialInfo 事件。将会返回只包含 SSID 属性的 WifiInfo 对象。
- iOS wx.getConnectedWifi 若设置了 partialInfo:true ，将会返回只包含 SSID、BSSID 属性的 WifiInfo 对象，且需要用户开启微信定位权限才能正确返回结果。
- 在某些情况下，可能 Wi-Fi 已经连接成功，但会因为获取不到完整的 WifiInfo 对象报错。具体错误信息为 errCode: 12010, errMsg: can't gain current wifi 或 no wifi is connected 。如果开发者不需要完整的 WifiInfo 对象，则可以通过采取上述策略解决报错问题。

Incorrect translation.