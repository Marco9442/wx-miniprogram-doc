# [#](#wx-onBLECharacteristicValueChange-function-listener) wx.onBLECharacteristicValueChange(function listener)

> 基础库 1.1.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：支持，需要小程序基础库版本不低于 [2.9.1](../../../framework/compatibility.html)
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [蓝牙低功耗 (BLE)](../../../framework/device/ble.html)

## [#](#功能描述) 功能描述

监听蓝牙低功耗设备的特征值变化事件。必须先调用 [wx.notifyBLECharacteristicValueChange](wx.notifyBLECharacteristicValueChange.html) 接口才能接收到设备推送的 notification。

## [#](#参数) 参数

### [#](#function-listener) function listener

蓝牙低功耗设备的特征值变化事件的监听函数

#### [#](#参数-2) 参数

##### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| deviceId | string | 蓝牙设备 id |
| serviceId | string | 蓝牙特征对应服务的 UUID |
| characteristicId | string | 蓝牙特征的 UUID |
| value | ArrayBuffer | 特征最新的值 |

## [#](#示例代码) 示例代码

[在开发者工具中预览效果](https://developers.weixin.qq.com/s/pQU51zmz7a3K "在开发者工具中预览效果")

```
// ArrayBuffer转16进制字符串示例
function ab2hex(buffer) {
  let hexArr = Array.prototype.map.call(
    new Uint8Array(buffer),
    function(bit) {
      return ('00' + bit.toString(16)).slice(-2)
    }
  )
  return hexArr.join('');
}
wx.onBLECharacteristicValueChange(function(res) {
  console.log(`characteristic ${res.characteristicId} has changed, now is ${res.value}`)
  console.log(ab2hex(res.value))
})
```

Incorrect translation.