# [#](#WEB-H5-使用微信网关) WEB & H5 使用微信网关

本文介绍如何在 WEB 应用中接入微信网关。

**注意：** WEB 应用接入仅支持基础版套餐及以上使用。

## [#](#一、接入步骤) 一、接入步骤

### [#](#_1-微信扫码登录-微信网关控制台) 1. 微信扫码登录 [微信网关控制台](https://developers.weixin.qq.com/console/services/donut?donut=%2Fconsole%2Fmanager%2Fgateway%3Futm_source%3Dgateway_homepage_hero&csrfRand=1875100942)

同意微信网关服务协议并同意即完成开通。在「微信网关-业务配置」页面，点击添加业务，开始配置。

![](https://res.wx.qq.com/op_res/fthUPxST1LROJ7U2seHT1NJ6WtkgItIkYAAhigxHUg7yJM0JQrhEGR25D6XJ4r8kMaw0Pr4b-_xg7h0eLMvj1A)

### [#](#_2-添加业务页面，选择业务类型为「Web」，随后填写业务名称（自行填写）和源站域名。) 2. 添加业务页面，选择业务类型为「Web」，随后填写业务名称（自行填写）和源站域名。

这里的源站域名是网页向服务发起 API 调用时的 API 域名。比如你在 `https://weixin.example.com` 网页中发起请求，到 `https://api.exapmple.com`，那么配置里应该填写 `api.exapmple.com`

![](https://res.wx.qq.com/op_res/fthUPxST1LROJ7U2seHT1MzjouRkXSaXC8Sb8acF5vZAzKpzZLsDO6PicIMZceDl35JOEA3U-sydFkCnC8N74w)

### [#](#_3-在你自己的-web-应用中，引入微信网关-Web-SDK) 3. 在你自己的 web 应用中，引入微信网关 Web SDK

```
<script src="https://该地址隐藏，请前往控制台获取/cloud.js"></script>

<!-- 下面是 eruda 调试工具，仅供开发时使用，上线前需删除 -->
<script src="//cdn.jsdelivr.net/npm/eruda"></script>
<script>eruda.init();</script>
```

注意 2.0.3 版本以上的 SDK 不再允许打开 DevTools 调试工具，否则请求将被拦截。可以使用 eruda 等调试工具查看 console 日志

### [#](#_4-初始化网关对象和实例) 4. 初始化网关对象和实例

```
const c1 = new cloud.Cloud({
  identityless: true,
  resourceAppid: 'wx069a87eae381af2b', // appid，填入接入的小程序 appid
  config: {
    customDomain: 'https://a224faf18-wx66e29c62636ff9e5.preview.wxcloudrun.com' // 网关接入节点域名,需要完整填入
  }
})
c1.init() // 初始化实例

const gateway = c1.services.Gateway({ domain: 'a224faf18-wx66e29c62636ff9e5.preview.wxcloudrun.com' }) // 网关接入节点域名，不包含协议头
```

### [#](#_5-请求网关地址) 5. 请求网关地址

```
gateway.call({
path: 'https://httpbin.org/post',
    header:{
      'X-WX-HTTP-MODE': 'REROUTE', // 必填
      'Content-Type':'application/json'
    },
method: 'post',
    data: { foo: 'bar' }
}).then(res => {
    console.log(res) // 网关返回结果
})
```

## [#](#二、能力拓展) 二、能力拓展

微信网关支持 H5 结合不同的请求库，可参考如下文档

[使用 Axios 结合微信网关](axios)

[hook xhr 结合微信网关](hookxhr)

## [#](#三、完整示例) 三、完整示例

以下是简单的示例 html，请在测试后根据自身业务自行改造。

```
<script src="https://该地址隐藏，请前往控制台获取/cloud.js" importance="VeryHigh"></script>
<script src="https://cdn.jsdelivr.net/npm/eruda"></script>
<script>
    const DOMAIN = 'XXXXXXXXXX.sh.wxgateway.com' // 网关域名
    const URL = 'https://www.testtest.com' // 你的业务 URL，可自行改造

    window.onload = async function () {
        eruda.init({tool:['console', 'network', 'info'],theme:'Arc Dark', autoScale:true, defaults:{displaySize: 90, transparency: 0.94}});
        const c1 = new window.cloud.Cloud({
            identityless: true,
            config: {
                customDomain: `https://${DOMAIN}`,
            }
        });
        await c1.init()
        const gateway = c1.services.Gateway({ domain: DOMAIN })
        window.gateway = gateway
        window.test()
    }
    window.test = function () {
        window.gateway.call({
            path: URL,
            header: {
                'X-WX-HTTP-MODE': 'REROUTE',
                'Content-Type': 'application/json'
            },
            method: 'GET',
            data: { foo: 'bar' }
        }).then(res => {
            const { callID, data, errMsg, statusCode } = res
            if(statusCode === 200) {
                console.log(`[${callID}] 网关请求成功`, data)
            } else {
                console.log(`[${callID}] 网关请求失败`, errMsg)
            }
        }).catch(err => {
            err = err.toString()
            if(err.includes('base_resp.ret 102006')) {
                console.log(`[${err.match(/callId: ([\w\-]+)/)[1]}] 网关请求非法（开启控制台调试或代理），信息：base_resp.ret 102006`)
            } else if(err.includes('errCode: 102016')){
                console.log(`[${err.match(/callId: ([\w\-]+)/)[1]}] 请求地址不在微信网关的小程序 URL 里，或者网关到期，信息：base_resp.ret 102016`)
            } else if(err.includes('gateway.call:fail 0')){
                console.error('网关请求失败，网络出现问题，受跨域限制或路径不可访问')
            } else {
                console.error('网关请求失败，其他原因：', err)
            }
        })
    }
</script>
<button onclick="window.test()">测试</button>
```

Incorrect translation.