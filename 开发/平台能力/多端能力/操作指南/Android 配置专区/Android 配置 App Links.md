# [#](#Android-配置-App-Links) Android 配置 App Links

多端框架已经支持开发者配置 [Android App Links](https://developer.android.com/studio/write/app-link-indexing?hl=zh-cn)，操作步骤如下：

**版本要求**

- 开发者工具版本需 >= 1.06.2504212（建议使用最新的 nightly）
- Android SDK 需 >= 1.6.9

**步骤 1：前往 project.miniapp.json 配置**

- 在开发者工具中，将 `project.miniapp.json` 切换至 json 模式
- 然后，在 "appLink" 中添加下方内容

```
"schemes": {
      "scheme": "uchi,weauth",
      "appLink":[{
        "scheme": "http,https",
        "host": "www.mulilab.cn",
        "pathPrefix": "/amin,/amin2/"
      }]
  }
```

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202504231122589.png)

**步骤 2：配置 assetlinks.json**

- 将 assetlinks.json 文件上传到你的网站并允许所有人读取，网址为 https://yoursite/.well-known/assetlinks.json
- 重要提示：系统会通过加密的 HTTPS 协议验证 Digital Asset Links 文件。请确保无论应用的 intent 过滤器是否包括 https，均可通过 HTTPS 连接访问 assetlinks.json 文件。
- 详情可查看[添加 Android App Links](https://developer.android.com/studio/write/app-link-indexing?hl=zh-cn)
- assetlinks.json 示例如下：

```
[{
"relation": ["delegate_permission/common.handle_all_urls"],
"target": {
"namespace": "android_app",
"package_name": "你的包名",
"sha256_cert_fingerprints":
["应用签名证书的 SHA256 指纹"]
}
}]
```

Incorrect translation.