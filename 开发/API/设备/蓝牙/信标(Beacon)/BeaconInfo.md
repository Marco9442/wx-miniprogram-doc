# [#](#BeaconInfo) BeaconInfo

> 相关文档: [蓝牙信标 (Beacon)](../../../framework/device/beacon.html)

Beacon 设备

## [#](#属性) 属性

### [#](#string-uuid) string uuid

Beacon 设备广播的 UUID

### [#](#number-major) number major

Beacon 设备的主 ID

### [#](#number-minor) number minor

Beacon 设备的次 ID

### [#](#number-proximity) number proximity

表示设备距离的枚举值（仅iOS）

**proximity 的合法值**

| 值 | 说明 | 最低版本 |
| --- | --- | --- |
| 0 | 信号太弱不足以计算距离，或非 iOS 设备 |  |
| 1 | 十分近 |  |
| 2 | 比较近 |  |
| 3 | 远 |  |

### [#](#number-accuracy) number accuracy

Beacon 设备的距离，单位 m。iOS 上，proximity 为 0 时，accuracy 为 -1。

### [#](#number-rssi) number rssi

表示设备的信号强度，单位 dBm

Incorrect translation.