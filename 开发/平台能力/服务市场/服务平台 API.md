## [#](#服务平台-API) 服务平台 API

> [2.9.4](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility)

API 均在 `wx.serviceMarket` 对象下。`invokeService` 方法可以通过兼容性配置，无需依赖 `2.9.4` 即可使用，配置方法见底部 `兼容性配置` 章节说明。

从 `2.11.1` 开始，插件内也可以使用 `wx.serviceMarket` API，在调用时，消耗的是宿主的资源而不是插件方的资源。

## [#](#一、invokeService) 一、invokeService

调用服务提供商提供的 API：`wx.serviceMarket.invokeService`

### [#](#_1-1-入参) 1.1 入参

接收一个对象，对象下有如下定义的字段：

| 字段名 | 类型 | 必填 | 默认值 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- |
| service | string | 是 |  | 服务提供商 ID |  |
| api | string | 是 |  | 服务 API 名 |  |
| data | Object | 否 |  | 传递给服务 API 的 JSON 数据 |  |
| async | boolean | 否 |  | 是否是异步长任务 |  |
| consumeType | number | 否 |  | 小程序或者公众号发起调用并且扣除自身的资源包不填写。2 代表小程序或者公众号调用并且扣除 open 账号的资源包 | 2.20.1 |
| consumeAppid | string | 否 |  | consume\_type 不填写则同样不填写；consume\_type 填写 2 时填写 openid 的 appid | 2.20.1 |

> consumeType 和 consumeAppid 仅使用于「服务商批发-商家调用」和「KA 内购-open 绑定的应用调用」两种模式，不支持「服务商批发-服务商调用」

### [#](#_1-2-返回值) 1.2 返回值

返回一个 `Promise`，如调用失败，则 `reject` 一个 `Error` 对象，如调用成功，则 `resolve` 结果为如下定义的对象：

| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| data | Object/String | 是 |  | 服务 API 的返回结果，2.9.4 返回的是序列化后的 JSON 字符串，2.10.0 起返回的是 JS 对象 |
| requestID | Object/String | 是 |  | 仅在入参传入 async: true 时返回，拿到后需通过 getAsyncResult 方法轮询结果 |

在 `data` 中，如果服务提供商要求其中某个字段为文件 URL、并且此时希望将本地文件/大数据上传成 URL 作为字段值传入，则可以使用我们提供的 [`CDN`](#CDN) 方法对相应值进行标记，微信会自动在调用服务 API 的时候将其转换成 CDN URL 给到服务提供方。

### [#](#_1-3-错误码) 1.3 错误码

| 错误码 | 含义 |
| --- | --- |
| -1 | 入参错误 |
| -2 | 调用失败 |
| -3 | 逻辑失败 |
| -6 | appid 错误 |
| -7 | api 信息错误 |
| -8 | api 信息错误 |
| -10 | api 扣费失败 |
| -11 | 命中频率 |

### [#](#_1-4-示例代码) 1.4 示例代码

#### [#](#_1-4-1-示例代码-1：OCR-示例) 1.4.1 示例代码 1：OCR 示例

从手机选择图片后，调用 [OCR 服务](https://developers.weixin.qq.com/community/servicemarket/detail/000ce4cec24ca026d37900ed551415)。

OCR 服务要求调用方传图片，接收图片的方式是图片 URL。

OCR 服务要求调用方的 data 结构如下：

| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| img\_url | string | 是 |  | 图片 URL |
| data\_type | number | 是 |  | 固定为 3，表示 URL 形式的图片 |
| ocr\_type | number | 是 |  | OCR 类型，1 为身份证识别 |

OCR 的接口需要传入图片 URL，如果需要将手机本地选择的图片上传转换成 URL，可以使用 [`CDN`](#CDN) 方法对文件路径进行标记（或用任意的存储服务和自建的存储服务，也可以使用[云开发](https://developers.weixin.qq.com/miniprogram/dev/wxcloudservice/wxcloud/basis/getting-started)的云文件存储服务，但都没有 `CDN` 方法便捷），以下给出使用 `CDN` 方法的示例：

```
// 选择图片
wx.chooseImage({
  count: 1,
  success: async function(res) {
    try {
      const invokeRes = await wx.serviceMarket.invokeService({
        service: 'wx79ac3de8be320b71',
        api: 'OcrAllInOne',
        data: {
          // 用 CDN 方法标记要上传并转换成 HTTP URL 的文件
          img_url: new wx.serviceMarket.CDN({
            type: 'filePath',
            filePath: res.tempFilePaths[0],
          }),
          data_type: 3,
          ocr_type: 1
        },
      })

      console.log('invokeService success', invokeRes)
      wx.showModal({
        title: 'success',
        content: JSON.stringify(invokeRes),
      })
    } catch (err) {
      console.error('invokeService fail', err)
      wx.showModal({
        title: 'fail',
        content: err,
      })
    }
  },
  fail: function(res) {},
  complete: function(res) {},
})
```

#### [#](#_1-4-2-示例代码-2-普通-JSON-协议接口) 1.4.2 示例代码 2: 普通 JSON 协议接口

有些服务不需要用到 CDN 辅助接口，可以直接 JSON 调用，以下任意举例：

```
// 选择图片
wx.chooseImage({
  count: 1,
  success: function(res) {
    // 调用 OCR 服务
    wx.serviceMarket.invokeService({
      service: 'some_service_id',
      api: 'test',
      data: {
        type: 'x',
        name: 'y',
      },
    }).then(res => {
      console.log('invokeService success', res)
    }).catch(err => {
      console.error('invokeService fail', err)
    })
  },
  fail: function(err) {
    console.error(err)
  },
})
```

## [#](#二、getAsyncResult) 二、getAsyncResult

查询异步接口调用的结果

### [#](#_2-1-入参) 2.1 入参

接收一个对象，对象下有如下定义的字段：

| 字段名 | 类型 | 必填 | 默认值 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- |
| requestId | string | 是 |  | 调用服务端接口 [invokeService](https://developers.weixin.qq.com/miniprogram/dev/server/API/wx-service-market/api_invokeservice) 接口返回的 request\_id |  |

### [#](#_2-2-返回值) 2.2 返回值

返回一个 `Promise`，如调用失败，则 `reject` 一个 `Error` 对象，如调用成功，则 `resolve` 结果为如下定义的对象：

| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| status | String | 异步接口的处理状态，1 表示还没有结果，需要继续轮询，0 表示已有结果 |
| data | String | 服务 API 的返回结果，status = 0 时会返回 |
| providerErrMsg | String | 异步接口调用失败时服务提供商返回的错误信息 |

## [#](#三、CDN) 三、CDN

标记需要上传到 CDN 的文件/大字符串然后转换成 HTTP URL 的数据，必须在 `invokeService` 中使用。

CDN 方法可以接收三种参数类型：

- String
- ArrayBuffer
- 文件路径定义对象

当使用文件路径定义对象时，将在调用服务 API 时自动将相应文件路径对应的文件内容上传至 CDN 并转换成 CDN URL，对象定义如下：

| 字段名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 定义对象的类型，必填 filePath |
| filePath | string | 是 | 文件路径 |

## [#](#四、兼容性配置) 四、兼容性配置

可以通过兼容性配置让 `wx.serviceMarket.invokeService` API 的使用不受基础库版本约束，配置方式是：在 `app.json` / `game.json` 中指定顶层字段 `"servicemarket": true`，在预览发布时小程序代码包会自动包含此 API 的兼容代码，在 `2.9.4` 以下也可使用。

仅在手机上使用，工具中调试请选择 `2.9.4` 基础库。

Incorrect translation.