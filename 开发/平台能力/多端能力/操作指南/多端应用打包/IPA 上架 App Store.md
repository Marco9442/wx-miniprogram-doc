# [#](#IPA-上架-App-Store) IPA 上架 App Store

编译生成的 IPA 可上传到 App Store Connect，从而将安装包提交到 App Store 进行审核以及发布。

- 开发者可通过如 `Application Loader`, `Transporter` 等工具完成相关操作，本文以 `Transporter` 为例供参考：

## [#](#Transporter-操作指引) Transporter 操作指引

- 步骤 1，下载 Transporter，此应用为 Mac 系统程序。（Windows/Linux 系统无法使用）

![](https://github.com/yujon/ipa-mac-builder/assets/16963584/39757c14-d2b7-460f-bef8-c9521c9825cd)

- 步骤 2，安装 Transporter，并使用已经注册为苹果开发者的 Apple ID 登录。

![](https://res.wx.qq.com/op_res/9UKRl7HHJAOMUo6h-v1v-R8sYxD9CZGE1IWZivTf6AkJ3TA9H7WG0K9fSxBpFnQN_WlpB4n9Iw69FsRw7PyoXg)

- 步骤 3，将已经打包好的 .ipa 文件拖入到 Transporter 中，点击交付（也可以点击验证没问题后再交付）。

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202306122303347.png)

- 步骤 4，登录 [App Store Connect](https://appstoreconnect.apple.com/)，在构建版本中选择提交的包，填写信息然后提交。

> 通常情况下，刚提交的包不会立即出现在构建版本里，大概 30 分钟左右会出现在构建版本中。如果构建版本选择列表中依然没有，登录绑定 Apple ID 所用的邮箱，查看是否有苹果发送的邮件，通常情况下是有的，根据提示的错误修改。

Incorrect translation.