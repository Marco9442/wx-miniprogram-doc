# [#](#openApi管理-接口列表) openApi管理 接口列表

| 接口名称 | 请求路径 | 描述 |
| --- | --- | --- |
| [查询API调用额度](./api_getapiquota) | /cgi-bin/openapi/quota/get | 本接口用于查询服务端接口的的每日调用接口的额度，调用次数，频率限制 |
| [重置API调用次数](./api_clearquota) | /cgi-bin/clear\_quota | 本接口是通过access\_token清空服务端接口的每日调用接口次数 |
| [重置指定API调用次数](./api_clearapiquota) | /cgi-bin/openapi/quota/clear | 本接口使用 access\_token 来重置指定接口的每日调用次数 |
| [使用AppSecret重置API调用次数](./api_clearquotabyappsecret) | /cgi-bin/clear\_quota/v2 | 本接口是通过AppSecret清空服务端接口的每日调用接口次数 |
| [查询rid信息](./api_getridinfo) | /cgi-bin/openapi/rid/get | 本接口用于查询调用服务端接口报错返回的rid详情信息，辅助开发者高效定位问题 |
| [网络通信检测](./api_callbackcheck) | /cgi-bin/callback/check | 为了帮助开发者排查回调连接失败的问题，提供这个网络检测的API |
| [获取微信API服务器IP](./api_getapidomainip) | /cgi-bin/get\_api\_domain\_ip | 该接口用于获取微信 api 服务器 ip 地址（开发者服务器主动访问 api.weixin.qq.com 的远端地址） |
| [获取微信推送服务器IP](./api_getcallbackip) | /cgi-bin/getcallbackip | 该接口用于获取微信推送服务器 ip 地址（向开发者服务器推送信息的微信服务器来源地址） |

Incorrect translation.