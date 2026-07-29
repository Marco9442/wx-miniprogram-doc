# [#](#跨端-JS-SDK) 跨端 JS SDK

微信云托管团队提供了Web SDK，支持在 Web 中访问云托管资源。 但 Web SDK 只支持常规 Web 应用（即浏览器环境）的开发，不兼容其他类 Web 平台。由于类 Web 平台在网络络请求、本地存储等特性上与浏览器环境有明显差异，现提供 [@wxcloud/cloud-sdk](https://www.npmjs.com/package/@wxcloud/cloud-sdk) 以支持跨端适配的能力。在传入不同平台适配对象之后，在其他类 Web 平台也可以 callContainer 的形式访问微信云托管资源。

## [#](#目的) 目的

目前市面上大部分的轻应用、小程序包括移动应用APP都是采用JS来作为开发语言的，所以我们可以对websdk进行轻微改造，就可以轻松使用在各种平台中。

但是单独改造SDK包会有些许风险，比如在原SDK包升级时需要重新构造，就造成了无穷无尽的麻烦，改造成本相当大。

基于这个问题，我们提供一套完整的适配扩展方案，遵循此方案规范可开发对应平台的适配器，然后搭配 @wxcloud/cloud-sdk 和适配器实现平台的兼容性。

不了解的小伙伴肯定会有些茫然，我来用浅显的语言解释一下，就是@wxcloud/cloud-sdk 将底层的网络请求以及相关基础需求以接口的形式暴露出来，我们按照平台的特殊API来补充这些接口，sdk就可以根据这些补充的接口，无障碍的运行在平台中了。

## [#](#安装) 安装

```
npm install @wxcloud/cloud-sdk --save
```

## [#](#使用) 使用

[@wxcloud/cloud-sdk](https://www.npmjs.com/package/@wxcloud/cloud-sdk) 导出了 `useAdapter` 和 `initCloud` 方法。先通过 `useAdapter` 传入跨端的适配对象，然后调用 `initCloud` 获取 cloud 对象，即引入 Web SDK 时自动挂载在 window 下的 cloud 。

```
const { useAdapter, initCloud } = require('@wxcloud/cloud-sdk')
import { adapters } from './example/adapters'

// platform 可传入标识平台的字符
useAdapter({ adapters, platform: 'platform' })
const cloud = initCloud()
```

在浏览器环境中使用可以不调用 useAdapter。

```
const { initCloud } = require('@wxcloud/cloud-sdk')

const cloud = initCloud()
```

具体使用以及适配器需要实现的细节，请移步[npm文档](https://www.npmjs.com/package/@wxcloud/cloud-sdk)

我们已经实现了uni-app的适配器，可以参考[此项目](https://github.com/WeixinCloud/wxcloud-websdk-uniapp)。

## [#](#注意事项) 注意事项

1. downloadFile、uploadFile 暂不支持适配。
2. 公众号登录相关的 api 在微信客户端之外调用无法正常完成相应逻辑。
3. 对于 [@wxcloud/cloud-sdk](https://www.npmjs.com/package/@wxcloud/cloud-sdk) 的问题，欢迎在微信开放社区发帖提问。

Incorrect translation.