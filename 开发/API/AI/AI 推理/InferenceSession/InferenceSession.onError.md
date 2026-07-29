# [#](#InferenceSession-onError-function-callback) InferenceSession.onError(function callback)

> 基础库 2.30.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：支持，需要小程序基础库版本不低于 [2.30.0](../../../framework/compatibility.html)

## [#](#功能描述) 功能描述

监听模型加载失败事件

## [#](#参数) 参数

### [#](#function-callback) function callback

模型加载失败回调函数

## [#](#示例代码) 示例代码

```
// 创建会话，加载模型
const session = wx.createInferenceSession({
  model: `${wx.env.USER_DATA_PATH}/MNIST.onnx`,
  precisionLevel: 4,
  typicalShape:{input1:[1, 3, 224, 224], input2:[1, 1, 224, 224]},  //除非使用动态轴，一般不用显式指定
  allowNPU: false,
  allowQuantize: false
})

// 监听error事件
session.onError(err => {
  console.error(err)
})
```

Incorrect translation.