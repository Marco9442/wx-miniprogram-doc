# [#](#NFCAdapter) NFCAdapter

> 基础库 2.11.2 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> 相关文档: [近场通信 (NFC)](../../../framework/device/nfc.html)

## [#](#属性) 属性

### [#](#Object-tech) Object tech

标签类型枚举

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| ndef | string | 对应Ndef实例，实例支持对NDEF格式的NFC标签上的NDEF数据的读写 |
| nfcA | string | 对应NfcA实例，实例支持NFC-A (ISO 14443-3A)标准的读写 |
| nfcB | string | 对应NfcB实例，实例支持NFC-B (ISO 14443-3B)标准的读写 |
| isoDep | string | 对应IsoDep实例，实例支持ISO-DEP (ISO 14443-4)标准的读写 |
| nfcF | string | 对应NfcF实例，实例支持NFC-F (JIS 6319-4)标准的读写 |
| nfcV | string | 对应NfcV实例，实例支持NFC-V (ISO 15693)标准的读写 |
| mifareClassic | string | 对应MifareClassic实例，实例支持MIFARE Classic标签的读写 |
| mifareUltralight | string | 对应MifareUltralight实例，实例支持MIFARE Ultralight标签的读写 |

## [#](#方法) 方法

### [#](#NFCAdapter-startDiscovery) [NFCAdapter.startDiscovery()](NFCAdapter.startDiscovery.html)

### [#](#NFCAdapter-stopDiscovery) [NFCAdapter.stopDiscovery()](NFCAdapter.stopDiscovery.html)

### [#](#Ndef-NFCAdapter-getNdef) [Ndef NFCAdapter.getNdef()](NFCAdapter.getNdef.html)

获取Ndef实例，实例支持对NDEF格式的NFC标签上的NDEF数据的读写

### [#](#NfcA-NFCAdapter-getNfcA) [NfcA NFCAdapter.getNfcA()](NFCAdapter.getNfcA.html)

获取NfcA实例，实例支持NFC-A (ISO 14443-3A)标准的读写

### [#](#NfcB-NFCAdapter-getNfcB) [NfcB NFCAdapter.getNfcB()](NFCAdapter.getNfcB.html)

获取NfcB实例，实例支持NFC-B (ISO 14443-3B)标准的读写

### [#](#IsoDep-NFCAdapter-getIsoDep) [IsoDep NFCAdapter.getIsoDep()](NFCAdapter.getIsoDep.html)

获取IsoDep实例，实例支持ISO-DEP (ISO 14443-4)标准的读写

### [#](#NfcF-NFCAdapter-getNfcF) [NfcF NFCAdapter.getNfcF()](NFCAdapter.getNfcF.html)

获取NfcF实例，实例支持NFC-F (JIS 6319-4)标准的读写

### [#](#NfcV-NFCAdapter-getNfcV) [NfcV NFCAdapter.getNfcV()](NFCAdapter.getNfcV.html)

获取NfcV实例，实例支持NFC-V (ISO 15693)标准的读写

### [#](#MifareClassic-NFCAdapter-getMifareClassic) [MifareClassic NFCAdapter.getMifareClassic()](NFCAdapter.getMifareClassic.html)

获取MifareClassic实例，实例支持MIFARE Classic标签的读写

### [#](#MifareUltralight-NFCAdapter-getMifareUltralight) [MifareUltralight NFCAdapter.getMifareUltralight()](NFCAdapter.getMifareUltralight.html)

获取MifareUltralight实例，实例支持MIFARE Ultralight标签的读写

### [#](#NFCAdapter-onDiscovered-function-listener) [NFCAdapter.onDiscovered(function listener)](./NFCAdapter.onDiscovered.html)

监听 NFC Tag

### [#](#NFCAdapter-offDiscovered-function-listener) [NFCAdapter.offDiscovered(function listener)](./NFCAdapter.offDiscovered.html)

移除 NFC Tag的监听函数

Incorrect translation.