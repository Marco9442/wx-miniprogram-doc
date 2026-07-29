# [#](#BLEPeripheralServer) BLEPeripheralServer

> 基础库 2.10.3 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> 相关文档: [蓝牙介绍](../../../framework/device/bluetooth.html)

外围设备的服务端

## [#](#方法) 方法

### [#](#BLEPeripheralServer-addService-Object-object) [BLEPeripheralServer.addService(Object object)](BLEPeripheralServer.addService.html)

添加服务。

### [#](#BLEPeripheralServer-removeService-Object-object) [BLEPeripheralServer.removeService(Object object)](BLEPeripheralServer.removeService.html)

移除服务。

### [#](#BLEPeripheralServer-startAdvertising-Object-Object) [BLEPeripheralServer.startAdvertising(Object Object)](BLEPeripheralServer.startAdvertising.html)

开始广播本地创建的外围设备。

### [#](#BLEPeripheralServer-stopAdvertising) [BLEPeripheralServer.stopAdvertising()](BLEPeripheralServer.stopAdvertising.html)

停止广播。

### [#](#BLEPeripheralServer-writeCharacteristicValue-Object-Object) [BLEPeripheralServer.writeCharacteristicValue(Object Object)](BLEPeripheralServer.writeCharacteristicValue.html)

往指定特征写入二进制数据值，并通知已连接的主机，从机的特征值已发生变化，该接口会处理是走回包还是走订阅。

### [#](#BLEPeripheralServer-onCharacteristicWriteRequest-function-listener) [BLEPeripheralServer.onCharacteristicWriteRequest(function listener)](./BLEPeripheralServer.onCharacteristicWriteRequest.html)

监听已连接的设备请求写当前外围设备的特征值事件。收到该消息后需要立刻调用 [writeCharacteristicValue](BLEPeripheralServer.writeCharacteristicValue.html) 写回数据，否则主机不会收到响应。

### [#](#BLEPeripheralServer-offCharacteristicWriteRequest-function-listener) [BLEPeripheralServer.offCharacteristicWriteRequest(function listener)](./BLEPeripheralServer.offCharacteristicWriteRequest.html)

移除已连接的设备请求写当前外围设备的特征值事件的监听函数

### [#](#BLEPeripheralServer-onCharacteristicReadRequest-function-listener) [BLEPeripheralServer.onCharacteristicReadRequest(function listener)](./BLEPeripheralServer.onCharacteristicReadRequest.html)

监听已连接的设备请求读当前外围设备的特征值事件。收到该消息后需要立刻调用 [writeCharacteristicValue](BLEPeripheralServer.writeCharacteristicValue.html) 写回数据，否则主机不会收到响应。

### [#](#BLEPeripheralServer-offCharacteristicReadRequest-function-listener) [BLEPeripheralServer.offCharacteristicReadRequest(function listener)](./BLEPeripheralServer.offCharacteristicReadRequest.html)

移除已连接的设备请求读当前外围设备的特征值事件的监听函数

### [#](#BLEPeripheralServer-onCharacteristicSubscribed-function-listener) [BLEPeripheralServer.onCharacteristicSubscribed(function listener)](./BLEPeripheralServer.onCharacteristicSubscribed.html)

监听特征订阅事件，仅 iOS 支持。

### [#](#BLEPeripheralServer-offCharacteristicSubscribed-function-listener) [BLEPeripheralServer.offCharacteristicSubscribed(function listener)](./BLEPeripheralServer.offCharacteristicSubscribed.html)

移除特征订阅事件的监听函数

### [#](#BLEPeripheralServer-onCharacteristicUnsubscribed-function-listener) [BLEPeripheralServer.onCharacteristicUnsubscribed(function listener)](./BLEPeripheralServer.onCharacteristicUnsubscribed.html)

监听取消特征订阅事件，仅 iOS 支持。

### [#](#BLEPeripheralServer-offCharacteristicUnsubscribed-function-listener) [BLEPeripheralServer.offCharacteristicUnsubscribed(function listener)](./BLEPeripheralServer.offCharacteristicUnsubscribed.html)

移除取消特征订阅事件的监听函数

Incorrect translation.