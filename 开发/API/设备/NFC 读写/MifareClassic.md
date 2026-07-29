# [#](#MifareClassic) MifareClassic

> 基础库 2.11.2 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> 相关文档: [近场通信 (NFC)](../../../framework/device/nfc.html)

MifareClassic 标签

## [#](#方法) 方法

### [#](#MifareClassic-connect) [MifareClassic.connect()](MifareClassic.connect.html)

连接 NFC 标签

### [#](#MifareClassic-close) [MifareClassic.close()](MifareClassic.close.html)

断开连接

### [#](#MifareClassic-setTimeout-Object-object) [MifareClassic.setTimeout(Object object)](MifareClassic.setTimeout.html)

设置超时时间

### [#](#MifareClassic-isConnected) [MifareClassic.isConnected()](MifareClassic.isConnected.html)

检查是否已连接

### [#](#MifareClassic-getMaxTransceiveLength) [MifareClassic.getMaxTransceiveLength()](MifareClassic.getMaxTransceiveLength.html)

获取最大传输长度

### [#](#MifareClassic-transceive-Object-object) [MifareClassic.transceive(Object object)](MifareClassic.transceive.html)

发送数据

对于MifareClassic的分块读写

- 指令 0x30 + 块号 可以用于读取某个块的数据
- 指令 0xA0 + 块号 + 待写入数据 可以用于往某个块写入数据

Incorrect translation.