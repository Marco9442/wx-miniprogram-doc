操作指南/多端应用打包/上传 SDK 运行日志/
# [\#](https://developers.weixin.qq.com/miniprogram/dev/platform-capabilities/miniapp/handbook/build/upload-log.html\#%E4%B8%8A%E4%BC%A0-SDK-%E8%BF%90%E8%A1%8C%E6%97%A5%E5%BF%97) 上传 SDK 运行日志
为了更好地定位关于 SDK 的异常反馈，我们提供了通过使用 SDK 菜单栏将 SDK 运行日志上传至官方后台的能力。开发者可以基于此能力进行问题反馈，同时也可以自定义入口给 App 用户使用。
[前置条件](https://developers.weixin.qq.com/miniprogram/dev/platform-capabilities/miniapp/handbook/build/upload-log.html#%E5%89%8D%E7%BD%AE%E6%9D%A1%E4%BB%B6)
[Android 上传日志步骤](https://developers.weixin.qq.com/miniprogram/dev/platform-capabilities/miniapp/handbook/build/upload-log.html#android-%E4%B8%8A%E4%BC%A0%E6%97%A5%E5%BF%97%E6%AD%A5%E9%AA%A4)
[iOS 上传日志步骤](https://developers.weixin.qq.com/miniprogram/dev/platform-capabilities/miniapp/handbook/build/upload-log.html#ios-%E4%B8%8A%E4%BC%A0%E6%97%A5%E5%BF%97%E6%AD%A5%E9%AA%A4)
[调用 API 自定义上传入口](https://developers.weixin.qq.com/miniprogram/dev/platform-capabilities/miniapp/handbook/build/upload-log.html#%E8%B0%83%E7%94%A8-api-%E8%87%AA%E5%AE%9A%E4%B9%89%E4%B8%8A%E4%BC%A0%E5%85%A5%E5%8F%A3)
## [\#](https://developers.weixin.qq.com/miniprogram/dev/platform-capabilities/miniapp/handbook/build/upload-log.html\#%E5%89%8D%E7%BD%AE%E6%9D%A1%E4%BB%B6) 前置条件
- iOS SDK >= 1.0.3，Android SDK >= 1.0.1
- 开启「内置菜单唤起配置」，默认为开启状态；开启后，则可通过对应的手势在 App 端唤起相关菜单
![](https://res.wx.qq.com/op\_res/etUAKOtizwVohWeVDVXBw5-CZi8URrCqYxZaGMp1HBPVf3WL7Si39wvAh14XW2agoEXF3G1Sz0dfbV3oTTnzrQ)
- 如果是鸿蒙，则需要手动切换 json 模式，添加 `appMenuEnable`，如下截图
![](https://res8.wxqcloud.qq.com.cn/wxdoc/7ae1a0c8-58b2-4cf7-bb37-27154ae03db2.png)
## [\#](https://developers.weixin.qq.com/miniprogram/dev/platform-capabilities/miniapp/handbook/build/upload-log.html\#Android-%E9%B8%BF%E8%92%99%E4%B8%8A%E4%BC%A0%E6%97%A5%E5%BF%97%E6%AD%A5%E9%AA%A4) Android & 鸿蒙上传日志步骤
1. 唤起 SDK 菜单栏
对于 Android 设备，唤起 SDK 菜单栏的手势为： \*\*三指点击五下\*\*
![](https://res.wx.qq.com/op\_res/1G0uDj-sNgUAXACyqvyrwjhus7DUtq5o4\_qvFre77xGV8hr1-y1NXdKVKlKTQAB6sRMK5tIo-KdvxPr71h\_x5A)
2. 点击「上传日志」，获取日志 ID
![](https://res.wx.qq.com/op\_res/1G0uDj-sNgUAXACyqvyrwkV\_N5xdzrWa8vnQ\_M1Mx2\_HqrDvkVdTwDkVC5Vn2R0qB6DNShND1oIEY8Hd7la5\_w)
3. 将日志 ID 与 多端应用账号信息一同反馈给官方技术人员（可前往 [社区](https://developers.weixin.qq.com/community/develop/mixflow) 反馈。）
## [\#](https://developers.weixin.qq.com/miniprogram/dev/platform-capabilities/miniapp/handbook/build/upload-log.html\#iOS-%E4%B8%8A%E4%BC%A0%E6%97%A5%E5%BF%97%E6%AD%A5%E9%AA%A4) iOS 上传日志步骤
1. 在 `project.miniapp.json` 开启 `enableDebugLog`
- 开启 `enableDebugLog`，有助于官方获得更详细的 SDK 运行日志，更好地定位问题，但同时会增加日志占用的存储空间，如担心对 App 性能产生影响，可在开发阶段开启，上线阶段关闭
- 开启 `enableDebugLog`，不会影响 VConsole 正常使用
![](https://res.wx.qq.com/op\_res/g1Q\_GUxzp5zmkHrCYcgkVtyFWq6O3gAc2bhurhMYPB33coXdrl0ffmiJ1Yka8HV6wzVu9tdqqJG0KLYx6GCRlw)
2. 唤起 SDK 菜单栏
对于 iOS 设备，唤起 SDK 菜单栏的手势为： \*\*三指长按五秒\*\*
![](https://res.wx.qq.com/op\_res/1G0uDj-sNgUAXACyqvyrwjhus7DUtq5o4\_qvFre77xGV8hr1-y1NXdKVKlKTQAB6sRMK5tIo-KdvxPr71h\_x5A)
3. 点击「上传日志」，获取日志 ID
![](https://res.wx.qq.com/op\_res/1G0uDj-sNgUAXACyqvyrwkV\_N5xdzrWa8vnQ\_M1Mx2\_HqrDvkVdTwDkVC5Vn2R0qB6DNShND1oIEY8Hd7la5\_w)
4. 将日志 ID 与 多端应用账号信息一同反馈给官方技术人员（可前往 [社区](https://developers.weixin.qq.com/community/develop/mixflow) 反馈。）
## [\#](https://developers.weixin.qq.com/miniprogram/dev/platform-capabilities/miniapp/handbook/build/upload-log.html\#%E8%B0%83%E7%94%A8-API-%E8%87%AA%E5%AE%9A%E4%B9%89%E4%B8%8A%E4%BC%A0%E5%85%A5%E5%8F%A3) 调用 API 自定义上传入口
开发者也可以调用 [wx.miniapp.openSaaAActionSheet](https://developers.weixin.qq.com/miniprogram/dev/platform-capabilities/miniapp/api/miniapp/openSaaAActionSheet) 在自己的小程序代码中自定义「日志上传」的入口，方便排查 App 用户的问题。
### [\#](https://developers.weixin.qq.com/miniprogram/dev/platform-capabilities/miniapp/handbook/build/upload-log.html\#%E4%BB%A3%E7%A0%81%E7%A4%BA%E4%BE%8B) 代码示例
```js
wx.miniapp.openSaaAActionSheet({
success: (res) => {
console.log('openSaaAActionSheet success:', res)
}
})
```