基础/加密/UserCryptoManager/UserCryptoManager.getLatestUserKey/
# [\#](https://developers.weixin.qq.com/miniprogram/dev/api/base/crypto/UserCryptoManager.getLatestUserKey.html\#UserCryptoManager-getLatestUserKey-Object-object) UserCryptoManager.getLatestUserKey(Object object)
> 基础库 2.17.3 开始支持，低版本需做 [兼容处理](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html)。
> \*\*以 [Promise 风格](https://developers.weixin.qq.com/miniprogram/dev/framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用\*\*：不支持
>
> \*\*小程序插件\*\*：不支持
>
> \*\*微信 Windows 版\*\*：支持
>
> \*\*微信 Mac 版\*\*：支持
> 相关文档: [小程序加密网络通道](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/user-encryptkey.html)
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/base/crypto/UserCryptoManager.getLatestUserKey.html\#%E5%8A%9F%E8%83%BD%E6%8F%8F%E8%BF%B0) 功能描述
获取最新的用户加密密钥
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/base/crypto/UserCryptoManager.getLatestUserKey.html\#%E5%8F%82%E6%95%B0) 参数
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/base/crypto/UserCryptoManager.getLatestUserKey.html\#Object-object) Object object
| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| success | function | | 否 | 接口调用成功的回调函数 |
| fail | function | | 否 | 接口调用失败的回调函数 |
| complete | function | | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/base/crypto/UserCryptoManager.getLatestUserKey.html\#object-success-%E5%9B%9E%E8%B0%83%E5%87%BD%E6%95%B0) object.success 回调函数
##### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/base/crypto/UserCryptoManager.getLatestUserKey.html\#%E5%8F%82%E6%95%B0-2) 参数
###### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/base/crypto/UserCryptoManager.getLatestUserKey.html\#Object-res) Object res
| 属性 | 类型 | 说明 |
| --- | --- | --- |
| encryptKey | string | 用户加密密钥 |
| iv | string | 密钥初始向量 |
| version | number | 密钥版本 |
| expireTime | number | 密钥过期时间 |
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/base/crypto/UserCryptoManager.getLatestUserKey.html\#%E7%A4%BA%E4%BE%8B%E4%BB%A3%E7%A0%81) 示例代码
```js
const userCryptoManager = wx.getUserCryptoManager()
userCryptoManager.getLatestUserKey({
success: res => {
const {encryptKey, iv, version, expireTime} = res
console.log(encryptKey, iv, version, expireTime)
}
})
```