# [\#](https://developers.weixin.qq.com/miniprogram/dev/server/API/mp-message-management/updatable-message/api\_createactivityid.html\#%E5%88%9B%E5%BB%BAactivity-id) 创建activity\\_id
[调试诊断](https://developers.weixin.qq.com/console/devtools/debug?utm\_source=api\_tools)
> 接口应在服务器端调用，不可在前端（小程序、网页、APP等）直接调用，具体可参考 [接口调用指南](https://developers.weixin.qq.com/doc/oplatform/developers/dev/guide)。
接口英文名：createActivityId
该接口用于创建被分享动态消息或私密消息的 activity\\_id。详见 [动态消息](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/share/updatable-message)
## [\#](https://developers.weixin.qq.com/miniprogram/dev/server/API/mp-message-management/updatable-message/api\_createactivityid.html\#\_1-%E8%B0%83%E7%94%A8%E6%96%B9%E5%BC%8F) 1\. 调用方式
### [\#](https://developers.weixin.qq.com/miniprogram/dev/server/API/mp-message-management/updatable-message/api\_createactivityid.html\#HTTPS-%E8%B0%83%E7%94%A8) HTTPS 调用
```bash
GET https://api.weixin.qq.com/cgi-bin/message/wxopen/activityid/create?access\_token=ACCESS\_TOKEN&unionid=UNIONID&openid=OPENID
```
### [\#](https://developers.weixin.qq.com/miniprogram/dev/server/API/mp-message-management/updatable-message/api\_createactivityid.html\#%E4%BA%91%E8%B0%83%E7%94%A8) 云调用
- 调用方法：updatableMessage.createActivityId
- 出入参和 HTTPS 调用相同，调用方式可查看 [云调用](https://developers.weixin.qq.com/doc/oplatform/developers/dev/cloudCall) 说明文档。
### [\#](https://developers.weixin.qq.com/miniprogram/dev/server/API/mp-message-management/updatable-message/api\_createactivityid.html\#%E7%AC%AC%E4%B8%89%E6%96%B9%E8%B0%83%E7%94%A8) 第三方调用
- 本接口支持第三方平台代商家调用。
- 该接口所属的权限集 id 为：18
- 服务商获得其中之一权限集授权后，可通过使用 [authorizer\\_access\\_token](https://developers.weixin.qq.com/doc/oplatform/developers/dev/AuthorizerAccessToken) 代商家进行调用，具体可查看 [第三方调用](https://developers.weixin.qq.com/doc/oplatform/Third-party\_Platforms/2.0/Before\_Develop/call\_interface) 说明文档。
## [\#](https://developers.weixin.qq.com/miniprogram/dev/server/API/mp-message-management/updatable-message/api\_createactivityid.html\#\_2-%E8%AF%B7%E6%B1%82%E5%8F%82%E6%95%B0) 2\. 请求参数
### [\#](https://developers.weixin.qq.com/miniprogram/dev/server/API/mp-message-management/updatable-message/api\_createactivityid.html\#%E6%9F%A5%E8%AF%A2%E5%8F%82%E6%95%B0-Query-String-Parameters) 查询参数 `Query String Parameters`
| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| access\\_token | string | 是 | 接口调用凭证，可使用 [access\\_token](https://developers.weixin.qq.com/miniprogram/dev/server/API/mp-access-token/api\_getaccesstoken)、 [authorizer\\_access\\_token](https://developers.weixin.qq.com/doc/oplatform/openApi/ticket-token/api\_getauthorizeraccesstoken) |
| unionid | string | 否 | 为私密消息创建activity\\_id时，指定分享者为unionid用户。其余用户不能用此activity\\_id分享私密消息。 \*\*openid与unionid填一个即可。\*\* 私密消息暂不支持云函数生成activity id。 |
| openid | string | 否 | 为私密消息创建activity\\_id时，指定分享者为openid用户。其余用户不能用此activity\\_id分享私密消息。 \*\*openid与unionid填一个即可。\*\* 私密消息暂不支持云函数生成activity id。 |
### [\#](https://developers.weixin.qq.com/miniprogram/dev/server/API/mp-message-management/updatable-message/api\_createactivityid.html\#%E8%AF%B7%E6%B1%82%E4%BD%93-Request-Payload) 请求体 `Request Payload`
无
## [\#](https://developers.weixin.qq.com/miniprogram/dev/server/API/mp-message-management/updatable-message/api\_createactivityid.html\#\_3-%E8%BF%94%E5%9B%9E%E5%8F%82%E6%95%B0) 3\. 返回参数
### [\#](https://developers.weixin.qq.com/miniprogram/dev/server/API/mp-message-management/updatable-message/api\_createactivityid.html\#%E8%BF%94%E5%9B%9E%E4%BD%93-Response-Payload) 返回体 `Response Payload`
| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| activity\\_id | string | 动态消息的 ID |
| expiration\\_time | number | activity\\_id 的过期时间戳。默认24小时后过期。 |
| errcode | number | [错误码](https://developers.weixin.qq.com/miniprogram/dev/server/API/mp-message-management/updatable-message/api\_createactivityid.html#apierrcode) |
| errmsg | string | [错误信息](https://developers.weixin.qq.com/miniprogram/dev/server/API/mp-message-management/updatable-message/api\_createactivityid.html#apierrcode) |
## [\#](https://developers.weixin.qq.com/miniprogram/dev/server/API/mp-message-management/updatable-message/api\_createactivityid.html\#\_4-%E6%B3%A8%E6%84%8F%E4%BA%8B%E9%A1%B9) 4\. 注意事项
本接口无特殊注意事项
## [\#](https://developers.weixin.qq.com/miniprogram/dev/server/API/mp-message-management/updatable-message/api\_createactivityid.html\#\_5-%E4%BB%A3%E7%A0%81%E7%A4%BA%E4%BE%8B) 5\. 代码示例
### [\#](https://developers.weixin.qq.com/miniprogram/dev/server/API/mp-message-management/updatable-message/api\_createactivityid.html\#\_5-1-HTTPS%E8%B0%83%E7%94%A8) 5.1 HTTPS调用
请求示例
```json
{
"unionid": "oHAUs6LSuwgHq-mlnFrffKXw3QYM",
"openid": "OPENID"
}
```
返回示例
```json
{
"errcode": "42001",
"errmsg": "access\_token 过期"
}
```
### [\#](https://developers.weixin.qq.com/miniprogram/dev/server/API/mp-message-management/updatable-message/api\_createactivityid.html\#\_5-2-%E4%BA%91%E8%B0%83%E7%94%A8%E7%A4%BA%E4%BE%8B) 5.2 云调用示例
请求示例
```js
const cloud = require('wx-server-sdk');
cloud.init({
env: cloud.DYNAMIC\_CURRENT\_ENV,
});
exports.main = async (event, context) => {
try {
const result = await cloud.openapi.updatableMessage.createActivityId({
"unionid": "oHAUs6LSuwgHq-mlnFrffKXw3QYM",
"openid": "OPENID"
});
return result;
} catch (err) {
return err;
}
};
```
返回示例
```json
{
"errcode": "42001",
"errmsg": "access\_token 过期"
}
```
## [\#](https://developers.weixin.qq.com/miniprogram/dev/server/API/mp-message-management/updatable-message/api\_createactivityid.html\#\_6-%E9%94%99%E8%AF%AF%E7%A0%81) 6\. 错误码
以下是本接口的错误码列表，其他错误码可参考 [通用错误码](https://developers.weixin.qq.com/doc/oplatform/developers/errCode/)；调用接口遇到报错，可使用官方提供的 [API 诊断工具](https://developers.weixin.qq.com/console/devtools/debug?utm\_source=api\_errcode) 辅助定位和分析问题。
| 错误码 | 错误描述 | 解决方案 |
| --- | --- | --- |
| -1 | system error | 系统繁忙，此时请开发者稍候再试 |
| 40001 | invalid credential  access\\_token isinvalid or not latest | 获取 access\\_token 时 AppSecret 错误，或者 access\\_token 无效。请开发者认真比对 AppSecret 的正确性，或查看是否正在为恰当的公众号调用接口 |
## [\#](https://developers.weixin.qq.com/miniprogram/dev/server/API/mp-message-management/updatable-message/api\_createactivityid.html\#\_7-%E9%80%82%E7%94%A8%E8%8C%83%E5%9B%B4) 7\. 适用范围
本接口在不同账号类型下的可调用情况：
| 小程序 | 小游戏 |
| --- | --- |
| ✔ | ✔ |
- ✔：该账号可调用此接口。
- 其他未明确声明的账号类型，如无特殊说明，均不可调用此接口。