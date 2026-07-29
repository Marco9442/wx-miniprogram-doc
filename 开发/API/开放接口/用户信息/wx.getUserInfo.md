# [#](#wx-getUserInfo-Object-object) wx.getUserInfo(Object object)

用户头像昵称获取规则已调整，参考 [用户信息接口调整说明](https://developers.weixin.qq.com/community/develop/doc/000cacfa20ce88df04cb468bc52801)、[小程序用户头像昵称获取规则调整公告](https://developers.weixin.qq.com/community/develop/doc/00022c683e8a80b29bed2142b56c01)

> **以 [Promise 风格](../../../framework/app-service/api.html#异步-API-返回-Promise) 调用**：不支持
>
> **[用户授权](../../../framework/open-ability/authorize.html)**：需要 scope.userInfo。
>
> **小程序插件**：支持，需要小程序基础库版本不低于 [2.3.1](../../../framework/compatibility.html)
>
> 在小程序插件中使用时，需要在用户信息功能页中获得用户授权或满足一定条件后调用。否则将返回 fail。详见 [用户信息功能页](../../../framework/plugin/functional-pages/user-info.html)
>
> **微信 Windows 版**：支持
>
> **微信 Mac 版**：支持
>
> **微信 鸿蒙 OS 版**：支持

> 相关文档: [接口调用频率规范](../../../framework/performance/api-frequency.html)

## [#](#功能描述) 功能描述

获取用户信息。

## [#](#参数) 参数

### [#](#Object-object) Object object

|  | 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- | --- |
|  | withCredentials | boolean |  | 否 | 是否带上登录态信息。当 withCredentials 为 true 时，要求此前有调用过 wx.login 且登录态尚未过期，此时返回的数据会包含 encryptedData, iv 等敏感信息；当 withCredentials 为 false 时，不要求有登录态，返回的数据不包含 encryptedData, iv 等敏感信息。 |
|  | lang | string | en | 否 | 显示用户信息的语言 |
|  | | 合法值 | 说明 | | --- | --- | | en | 英文 | | zh\_CN | 简体中文 | | zh\_TW | 繁体中文 | | | | | |
|  | success | function |  | 否 | 接口调用成功的回调函数 |
|  | fail | function |  | 否 | 接口调用失败的回调函数 |
|  | complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

| 属性 | 类型 | 说明 | 最低版本 |
| --- | --- | --- | --- |
| userInfo | [UserInfo](UserInfo.html) | 用户信息对象，不包含 openid 等敏感信息 |  |
| rawData | string | 不包括敏感信息的原始数据字符串，用于计算签名 |  |
| signature | string | 使用 sha1( rawData + sessionkey ) 得到字符串，用于校验用户信息，详见 [用户数据的签名验证和加解密](../../../framework/open-ability/signature.html) |  |
| encryptedData | string | 包括敏感数据在内的完整用户信息的加密数据，详见 [用户数据的签名验证和加解密](../../../framework/open-ability/signature.html#加密数据解密算法) |  |
| iv | string | 加密算法的初始向量，详见 [用户数据的签名验证和加解密](../../../framework/open-ability/signature.html#加密数据解密算法) |  |
| cloudID | string | 敏感数据对应的云 ID，开通[云开发](../../../wxcloudservice/wxcloud/basis/getting-started.html)的小程序才会返回，可通过云调用直接获取开放数据，详细见[云调用直接获取开放数据](../../../framework/open-ability/signature.html#method-cloud) | [2.7.0](../../../framework/compatibility.html) |

## [#](#示例代码) 示例代码

```
// 必须是在用户已经授权的情况下调用
wx.getUserInfo({
  success: function(res) {
    var userInfo = res.userInfo
    var nickName = userInfo.nickName
    var avatarUrl = userInfo.avatarUrl
    var gender = userInfo.gender //性别 0：未知、1：男、2：女
    var province = userInfo.province
    var city = userInfo.city
    var country = userInfo.country
  }
})
```

敏感数据有两种获取方式：

1. 使用 [加密数据解密算法](../../../framework/open-ability/signature.html#加密数据解密算法)
2. 使用 [云调用直接获取开放数据](../../../framework/open-ability/signature.html#云调用直接获取开放数据)
   获取得到的开放数据为以下 json 结构：

```
{
  "openId": "OPENID",
  "nickName": "NICKNAME",
  "gender": GENDER,
  "city": "CITY",
  "province": "PROVINCE",
  "country": "COUNTRY",
  "avatarUrl": "AVATARURL",
  "unionId": "UNIONID",
  "watermark": {
    "appid":"APPID",
    "timestamp":TIMESTAMP
  }
}
```

## [#](#小程序用户信息组件示例代码) 小程序用户信息组件示例代码

```
<!-- 如果只是展示用户头像昵称，可以使用 <open-data /> 组件 -->
<open-data type="userAvatarUrl"></open-data>
<open-data type="userNickName"></open-data>
<!-- 需要使用 button 来授权登录 -->
<button wx:if="{{canIUse}}" open-type="getUserInfo" bindgetuserinfo="bindGetUserInfo">授权登录</button>
<view wx:else>请升级微信版本</view>
```

```
Page({
  data: {
    canIUse: wx.canIUse('button.open-type.getUserInfo')
  },
  onLoad: function() {
    // 查看是否授权
    wx.getSetting({
      success (res){
        if (res.authSetting['scope.userInfo']) {
          // 已经授权，可以直接调用 getUserInfo 获取头像昵称
          wx.getUserInfo({
            success: function(res) {
              console.log(res.userInfo)
            }
          })
        }
      }
    })
  },
  bindGetUserInfo (e) {
    console.log(e.detail.userInfo)
  }
})
```

Incorrect translation.