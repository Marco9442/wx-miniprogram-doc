# [#](#小程序-API) 小程序 API

## [#](#API-说明) API 说明

以下所有 API 可通过 `wx.obs` 直接调用，或通过引入 npm 包，以兼容低版本的基础库调用 `wx.obs`。

npm 包接入方式：

1. 安装：在小程序代码根目录下执行 `npm install @wxobs/miniprogram-helper`
2. 构建：在微信开发者工具中，点击左上角菜单栏中“工具” -> “构建npm”
3. 使用：根据项目【设置】->【采集配置】中选择的【启动方式】的不同会有区别：

- 如果使用的默认的`自动启动`：无需 setup，可直接调用自定义用户属性、事件等方法
- 如果是`自定义启动`：在 app.js 文件中引入 setup 函数，并在 onLaunch 中执行即可启动采集。

> 注意：npm 包大小 10k，无需担心影响小程序包大小，此包仅为对基础库接口的简单包装

polyfill 示例代码 ：

```
import '@wxobs/miniprogram-helper';

App({
  onLaunch: async function () {
    ...
  },
});
```

## [#](#接口列表) 接口列表

| helper 接口 | 说明 |
| --- | --- |
| [setup](#启动采集) | 启动采集 |
| [getSessionId](#获取当前会话ID) | 获取当前会话ID |
| [getStatus](#获取当前采集状态) | 获取当前采集状态 |
| [teardown](#停止采集) | 停止采集 |
| [event](#上报自定义事件) | 上报自定义事件 |
| [setCustomId](#设置自定义ID) | 自定义业务标记 |
| [setCustomProperties](#设置自定义属性) | 自定义业务属性 |

## [#](#启动采集) 启动采集

接口：`setup`

**重要**：`setup` 方法仅在【启动方式】选择了【自定义启动】时可用，在【自动启动】模式下调用会出错。

```
await wx.obs.setup({
  maskMode: 'no-mask',
})
```

配置并启动数据采集。**注意**：helper 其他的 api 都必须在 setup 返回的 promise resolve 之后再执行

**参数**

```
{
  maskMode?: 'all-mask' | 'no-mask' // 可选，默认值 'all-mask'，'all-mask'表示采集时默认遮罩所有元素，'no-mask'表示不遮罩。使用 'no-mask' 模式时，请注意遵守《个人隐私保护法》等法规，在用户同意的情况下采集隐私数据。
  isWhitelistMaskMode?: boolean // [已弃用] 可选，默认值 true。true 表示以白名单模式遮罩小程序中的元素，false表以黑名单模式遮罩小程序中的元素。不可和 maskMode 同时使用。
  captureDataAttrs?: boolean // 可选，默认为 true。采集 webview 中的元素时，是否采集以 data-* 为开头的属性
  shouldCapturePage?: (page: string, query: Record<string, string>) => boolean // 可选。用于控制是否采集某页面的回调，page 和 query 是该页面的属性，默认为全部采集。
  shouldCaptureNetwork?: (info: INetworkRequestInfo) => boolean | INetworkRequestInfo // 可选。用于自定义网络请求采集，默认只采集失败的网络的请求的 URL 和状态码。基础库需 >= 3.4.1
  newSessionCallback?: (param: { sessionId: string }) => void // 产生新的会话时的回调
  autoSplitSession?: boolean // 是否自动分片
  onReport?: (param: { timestamp: number; from: 'appservice' | 'webview' }) => void // 上报数据时的回调
  errorCallback?: (param: {
    type: number;
    errMsg: string;
    extra?: string;
  }) => void; // 采集器内部发生错误时的回调
  canvas?: boolean // 是否采集 canvas. default: false。 基础库 >= 3.2.2
  canvasCollectInterval?: number // canvas 采集间隔，单位 ms. default: 100
}
```

**`shouldCaptureNetwork` 参数说明**

> 基础库 >= 3.4.1

该参数为可选参数：

- 如不传，则默认采集失败的网络请求（发起请求失败或响应状态码 >= 400 视为失败）的 URL 和状态码
- 如传，则由开发者决定一个网络请求是否采集 & 采集什么内容
  - 需自定义的场景举例：接口需要通过回包特定字段判断是否成功失败；需要额外上报响应信息等。

传入的自定义回调会在每个网络请求结束时触发，回调会收到一个网络请求信息作为参数，类型为 `INetworkRequestInfo`（结构见下），此时开发者回调的返回值**必须**为以下三种类型之一：

- `false`: 表示不采集该网络请求
- `true`: 表示按默认表现采集该网络请求（即仅失败时采集，仅采集 URL 和状态码）
- 类型为 `INetworkRequestInfo` 的对象: 表示按开发者自定义的内容上报

`INetworkRequestInfo` 结构：

```
interface INetworkRequestInfo {
  // 请求成功还是失败
  success: boolean
  // 请求的 URL
  url: string
  // 请求体
  requestData: string
  // 响应体
  responseData: string
  // 状态码
  statusCode?: number
  // 耗时
  cost: number
  // 请求失败时的错误信息
  errMsg?: string
  // 回调函数的返回值可传入的自定义标签，基础库 >= 3.4.2
  custom?: Record<string, string>
}
```

如果还需要给请求打额外信息，可以在返回值中填入 `custom` 对象，键值对都需为字符串类型。

**返回值**

```
Promise<Result>
```

`Result` 结构:

| 字段 | 类型 | 说明 |
| --- | --- | --- |
| sessionId | string | 可视化日志 Id，正常启动采集时不为空 |
| errMsg | string | 启动异常时的错误消息 |

## [#](#获取当前会话ID) 获取当前会话ID

接口：`getSessionId`

获取当前会话ID，仅当成功启动采集后有值（可以调用 `getStatus` 查看当前采集状态），在自动启动和自定义启动模式下均可调用。

**参数**

无

**返回值**

会话 ID（字符串）

## [#](#获取当前采集状态) 获取当前采集状态

接口: `getStatus`（npm helper 版本 >= 0.4.8 ）

**参数**

无

**返回值**

字符串，表示采集状态，枚举值如下：

| value | 说明 |
| --- | --- |
| NotSetup | 未 setup |
| SettingUp | 开启采集中 |
| WaitingForFirstReport | 采集第一个上报数据中 |
| Collecting | 正常采集中 |
| TearingDown | 停止采集中 |

## [#](#停止采集) 停止采集

接口：`teardown`

```
await wx.obs.teardown()
```

**参数**

无

**返回**

```
Promise<void>
```

## [#](#上报自定义事件) 上报自定义事件

接口：`event`

上报一个业务自定义的事件，上报后可以在控制台根据事件查找到相应的可视化日志、或在热力图 & 转化分析根据事件进行人群分析/对比分析，等等。

```
wx.obs.event('add_cart', {
  goods_id: '123',
  price: 10,
})
```

**参数**

| 字段 | 类型 | 说明 |
| --- | --- | --- |
| eventName | string | 事件名。长度限制 50 字符。 |
| eventProperties | 字段值为字符串或整形数字的对象 | 事件属性。一次上报属性限制 10 个，每个属性 key 需少于 50 字符，value 需少于 255 字符，value 为数字时请传入整形 |

提示：如果希望传入的是小数，可先转换为整数，比如商品价格是 `9.99` 元，可乘以 100 转换为以"分"为单位的 `999` 上报。

**返回值**

函数的返回值为是否通过参数校验，若不通过则会返回 `false`，反之 `true`

**示例**

假设用户在你的小程序上发生了一次购买动作，可以通过如下代码触发一次自定义事件（购买）的上报

```
wx.obs.event('buy_goods',{
  good_id: 'abcdefg123',
  order_id: 'xxxxxxx',
  price: 1024,
})
```

## [#](#设置自定义-ID) 设置自定义 ID

接口：`setCustomId`

自定义业务 ID。设置后统计结果可更贴合业务情况，未设置时，默认按随机生成并缓存的 ID 统计，该缓存会在微信清缓存或退出登录时清空。

**参数**  
自定义 ID 必须为字符串且少于 80 个字符。

**示例**

```
wx.obs.setCustomId('xxxx')
```

## [#](#设置自定义属性) 设置自定义属性

接口：`setCustomProperties`

自定义业务属性。与自定义业务 id 关联，因此调用该方法前应先调用 `setCustomId`。

**参数**  
对象数组，key 为字符串，value 须为字符串或整形数字。一次上报属性限制 10 个，每个属性 key 需少于 50 字符，value 需少于 255 字符，value 为数字时请传入整形。

**示例**

```
wx.obs.setCustomProperties({
  xxx: 'abc',
  yyy: 100
})
```

Incorrect translation.