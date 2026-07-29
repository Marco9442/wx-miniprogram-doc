# [#](#API) API

小程序开发框架提供丰富的微信原生 API，可以方便的调起微信提供的能力，如获取用户信息，本地存储，支付功能等。详细介绍请参考 [API 文档](/miniprogram/dev/api/)。

通常，在小程序 API 有以下几种类型：

## [#](#事件监听-API) 事件监听 API

我们约定，以 `on` 开头的 API 用来监听某个事件是否触发，如：[wx.onSocketOpen](https://developers.weixin.qq.com/miniprogram/dev/api/network/websocket/wx.sendSocketMessage.html)，[wx.onCompassChange](https://developers.weixin.qq.com/miniprogram/dev/api/device/compass/wx.onCompassChange.html) 等。

这类 API 接受一个回调函数作为参数，当事件触发时会调用这个回调函数，并将相关数据以参数形式传入。

**代码示例**

```
wx.onCompassChange(function (res) {
  console.log(res.direction)
})
```

## [#](#同步-API) 同步 API

我们约定，以 `Sync` 结尾的 API 都是同步 API， 如 [wx.setStorageSync](https://developers.weixin.qq.com/miniprogram/dev/api/storage/wx.setStorageSync.html)，[wx.getSystemInfoSync](https://developers.weixin.qq.com/miniprogram/dev/api/base/system/wx.getSystemInfoSync.html) 等。此外，也有一些其他的同步 API，如 [wx.createWorker](https://developers.weixin.qq.com/miniprogram/dev/api/worker/Worker.html)，[wx.getBackgroundAudioManager](https://developers.weixin.qq.com/miniprogram/dev/api/media/background-audio/BackgroundAudioManager.html) 等，详情参见 API 文档中的说明。

同步 API 的执行结果可以通过函数返回值直接获取，如果执行出错会抛出异常。

**代码示例**

```
try {
  wx.setStorageSync('key', 'value')
} catch (e) {
  console.error(e)
}
```

## [#](#异步-API) 异步 API

大多数 API 都是异步 API，如 [wx.request](https://developers.weixin.qq.com/miniprogram/dev/api/network/request/wx.request.html)，[wx.login](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/login/wx.login.html) 等。这类 API 接口通常都接受一个 `Object` 类型的参数，这个参数都支持按需指定以下字段来接收接口调用结果：

**Object 参数说明**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| success | function | 否 | 接口调用成功的回调函数 |
| fail | function | 否 | 接口调用失败的回调函数 |
| complete | function | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |
| 其他 | Any | - | 接口定义的其他参数 |

**回调函数的参数**

`success`，`fail`，`complete` 函数调用时会传入一个 `Object` 类型参数，包含以下字段：

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| errMsg | string | 错误信息，如果调用成功返回 `${apiName}:ok` |
| errCode | number | 错误码，仅部分 API 支持，具体含义请参考对应 API 文档，成功时为 `0`。 |
| 其他 | Any | 接口返回的其他数据 |

异步 API 的执行结果需要通过 `Object` 类型的参数中传入的对应回调函数获取。部分异步 API 也会有返回值，可以用来实现更丰富的功能，如 [wx.request](https://developers.weixin.qq.com/miniprogram/dev/api/network/request/wx.request.html)，[wx.connectSocket](https://developers.weixin.qq.com/miniprogram/dev/api/network/websocket/SocketTask.html) 等。

**代码示例**

```
wx.login({
  success(res) {
    console.log(res.code)
  }
})
```

## [#](#异步-API-返回-Promise) 异步 API 返回 Promise

基础库 [2.10.2](../compatibility) 版本起，异步 API 支持 callback & promise 两种调用方式。当接口参数 Object 对象中不包含 success/fail/complete 时将默认返回 promise，否则仍按回调方式执行，无返回值。

### [#](#注意事项) 注意事项

1. 部分接口如 `downloadFile`, `request`, `uploadFile`, `connectSocket`, `createCamera`（小游戏）本身就有返回值， 它们的 promisify 需要开发者自行封装。
2. 当没有回调参数时，异步接口返回 promise。此时若函数调用失败进入 fail 逻辑， 会报错提示 `Uncaught (in promise)`，开发者可通过 catch 来进行捕获。
3. [wx.onUnhandledRejection](https://developers.weixin.qq.com/miniprogram/dev/api/base/app/app-event/wx.onUnhandledRejection.html) 可以监听未处理的 Promise 拒绝事件。

**代码示例**

```
// callback 形式调用
wx.chooseImage({
  success(res) {
    console.log('res:', res)
  }
})

// promise 形式调用
wx.chooseImage().then(res => console.log('res: ', res))
```

## [#](#云开发-API) 云开发 API

开通并使用[微信云开发](https://developers.weixin.qq.com/miniprogram/dev/wxcloudservice/wxcloud/basis/getting-started)，即可使用云开发API，在小程序端直接调用服务端的[云函数](https://developers.weixin.qq.com/miniprogram/dev/wxcloudservice/wxcloud/guide/functions#云函数)。

**代码示例**

```
wx.cloud.callFunction({
  // 云函数名称
  name: 'cloudFunc',
  // 传给云函数的参数
  data: {
    a: 1,
    b: 2,
  },
  success: function(res) {
    console.log(res.result) // 示例
  },
  fail: console.error
})

// 此外，云函数同样支持promise形式调用
```

Incorrect translation.