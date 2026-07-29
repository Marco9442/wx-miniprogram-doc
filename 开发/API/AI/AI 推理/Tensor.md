# [#](#Tensor) Tensor

> 基础库 2.30.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

Tensor

## [#](#属性) 属性

### [#](#Array-number-shape) Array.<number> shape

Tensor shape （Tensor 形状，例如 `[1, 3, 224, 224]` 即表示一个4唯Tensor，每个维度的长度分别为1, 3, 224, 224）

### [#](#ArrayBuffer-data) ArrayBuffer data

Tensor 值，一段 ArrayBuffer

### [#](#string-type) string type

ArrayBuffer 值的类型，合法值有 `uint8`, `int8`, `uint32`, `int32`, `float32`

```
session.run({
  input1: {
    type: 'float32',
    data: new Float32Array(3 * 224 * 224).buffer,
    shape: [1, 3, 224, 224] // NCHW 顺序
  },
  input2: {
    type: 'uint8',
    data: new Uint8Array(224 * 224).buffer,
    shape: [1, 1, 224, 224]
  },
}).then(res => {
  console.log(res.output0)
  // output0 结构如下：
  // {
  //   type: 'uint8',
  //   data: new Uint8Array(224 * 224).buffer,
  //   shape: [1, 1, 224, 224]
  // }
})
```

Incorrect translation.