# [#](#iPad-支持) iPad 支持

iOS App 支持配置开启 iPad 能力。该能力正在内测阶段，部分能力还不稳定，请充分测试后再线上使用。为了让 App 支持 iPad，开发者提交 App Store 的时候需要在苹果后台进行配置。

**注意：** 如果支持过 iPad，后续就不能取消。可能会导致后续如果审核员发现 iPad 的功能问题，导致 iPhone 也无法过审核。

## [#](#一、使用说明) 一、使用说明

1. 开发者需要在 project.miniapp.json 中勾选「启用 iPad (Beta)」。启用后构建出来的 IPA 将支持 iPad/iPhone 机型。不启用的时候只支持 iPhone，在 iPad 使用兼容模式运行。

   ![](https://res.wx.qq.com/op_res/Q_UujdoTnw9RaReJUMSVJna2KAtly6kn1h6MrqlT7GVfBO4bYRB1Y58iT1BNqXt5Gp9WLPnBkUcD6HnJ0Rlixw)
2. iPad 图标配置。开发者必须配置「主图标（iPad 和 iPad Mini）」以及「主图标（iPad Pro）」。

   ![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202407171520279.png)
3. 屏幕适配可以参考[小程序适配文档](https://developers.weixin.qq.com/miniprogram/dev/framework/view/resizable#Media%20Query)。
4. 屏幕旋转，当 app.json 中配置了 `"resizable": true`，iPad 支持横屏（Portrait、Upside Down、Landscape Left、Landscape Right），否则只支持竖屏（Portrait、Upside Down）。

   ![](https://res.wx.qq.com/op_res/Q_UujdoTnw9RaReJUMSVJm0maR6NO5fL-nrVzWiWyTOfDDJb9Xg_IXPdx4ZKqTyahhu2j1jyO9ncZff2PE8Ynw)
5. 自定义屏幕旋转方向。project.miniapp.json 中可以自配置 iPadUISupportedInterfaceOrientations 去设置 iPad 的旋转方向。

```
project.miniapp.json的mini-ios属性下可添加
"iPadUISupportedInterfaceOrientations": [
    "Portrait",
    "PortraitUpsideDown",
    "LandscapeLeft",
    "LandscapeRight"
],
```

6. 不支持广告扩展 SDK。
7. 如果不想开启 iPad multitasking，可以在 project.miniapp.json 可视化中，找到 iOS 的应用配置（info.plist），开启 UIRequiresFullScreen。

   ![](https://res.wx.qq.com/op_res/Q_UujdoTnw9RaReJUMSVJjOrijKo2UrB4zusd803f0wgZFz_alMFEsP5WwKfSmvnpgr1Zx2cPZ-gGWuq7piHwg)

Incorrect translation.