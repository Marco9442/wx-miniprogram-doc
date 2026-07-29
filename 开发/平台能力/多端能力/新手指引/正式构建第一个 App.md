# [#](#快速构建多端应用) 快速构建多端应用

小程序多端框架支持使用微信小程序技术和微信开发者工具开发移动应用，开发者可将小程序代码同时发布成 Android、 iOS 以及 HarmonyOS 应用，实现一套代码，多端运行。

为帮助开发者快速上手「多端框架」，本文将开发的各个流程进行了简要归纳，开发者可按需阅读。

- 小程序项目是指支持编译为小程序的项目。
- 多端项目是指支持编译为小程序、Android 应用以及 iOS 应用的项目。
- 多端项目可以直接创建，也可以由已有的小程序项目升级而成。
- 使用小程序原生语法开发或其他第三方开发框架开发的微信小程序项目都支持升级为多端项目（不支持小游戏、小商店等）。
- 使用小程序多端框架与微信开发者工具的开发、编译、调试、构建等基础版功能永久免费，可放心使用。
- 开发过程中遇到问题请先查看[开发常见问题](../troubleshooting/dev)，若问题未能解决或有其他疑问，请前往[微信开放社区](https://developers.weixin.qq.com/community/minihome/mixflow/2889188691586351105)反馈

[第一部分 创建多端项目](#一、创建多端项目)

- 本部分主要介绍了如何创建多端项目、多端项目相对于小程序项目的变化以及项目在适配改造时的一些注意事项。

[第二部分 运行于真机或模拟器](#二、运行于真机或模拟器)

- 本部分主要介绍了如何将多端项目在真机或者模拟器中进行运行调试。

[第三部分 构建安装包](#三、构建安装包)

- 本部分主要介绍了如何将多端应用打包成 Android 安装包 ( APK )或 iOS 安装包 ( IPA )。

[第四部分 上架应用市场](#四、上架应用市场)

- 本部分主要介绍了多端应用打包成正式安装包后，在各大应用市场进行上架时的注意事项。

## [#](#一、创建多端项目) 一、创建多端项目

本部分主要介绍了如何创建多端项目、多端项目相对于小程序项目的变化以及项目在适配改造时的一些注意事项。
注意，多端项目支持由小程序项目升级而成或直接创建。若开发者已有小程序项目，则可以直接将小程序项目升级为多端项目（即1.2），若无，则可以选择直接创建多端项目（即1.3）。

### [#](#_1-1-工具安装) 1.1 工具安装

在电脑端安装 「[微信开发者工具](https://developers.weixin.qq.com/miniprogram/dev/devtools/log)」（开发版 ≥ 1.06.2306272，建议使用最新版）。

### [#](#_1-2-升级为多端项目（适用已有小程序项目的情况）) 1.2 升级为多端项目（适用已有小程序项目的情况）

在「微信开发者工具」中打开小程序项目，并在开发者工具顶部「模式」选择框的下拉列表中，选择「多端应用模式」。

![](https://res.wx.qq.com/op_res/wF70jN3etKFDv9oWtAxLd43fzTraGXuQ5mfxzkUl10ehSON_jgDQIULmg__m9JciJTjrVlmdi7x0gDppQwPH7Q)

若该小程序未绑定过「多端应用」，则会展示如下快速注册码。（若已绑定，则直接跳转到下一步）请用该小程序管理员或开发者的微信扫码创建多端应用并绑定该小程序，手机端按照提示步骤完成创建后，在开发者工具中点击「已绑定」按钮。成功后工具右侧会出现绑定成功提醒以及「绑定成功，请重新操作」的提示。

![](https://res.wx.qq.com/op_res/wF70jN3etKFDv9oWtAxLd8yTX6Pb5A-Un-MkcnBcBFQ_JWrXT-9oJUHNReB-OLvRzBNj48ZBKj1V9zBqJVTNFw) ![](https://res.wx.qq.com/op_res/wF70jN3etKFDv9oWtAxLd54ROmhSvIwugmSvIIBNz6TaQHYBJRR4kJ37ttrUZ6hdsT8_pA91zBC2ixziiDdWxg) ![](https://res.wx.qq.com/op_res/wF70jN3etKFDv9oWtAxLd-77ILA9B4CgAyPGTZTz0GkktYjsLTOXicddVZZ4WFqoOqQidz4QgYLkyM_AlJL1OA)

注意：

- 创建多端应用并绑定小程序有以下三种方式：
  1、在微信开发者工具中，切换开发模式，下拉选择「多端应用模式」，若未绑定则扫码创建多端并绑定小程序即可。
  2、在微信开发者工具中，在菜单栏 - 工具 - 升级为多端项目，若未绑定则扫码创建多端应用并绑定小程序即可。
  3、前往[微信开发者平台](https://developers.weixin.qq.com/platform/)- 创建多端应用 - 选择要绑定的小程序账号 - 创建成功，详情请查看 [多端应用管理](../handbook/web/application_create)。
- 平台暂不支持更换绑定的小程序。有需要请重新创建新的多端应用。详情请查看 [多端应用管理](../handbook/web/application_create)。

当小程序与多端应用完成绑定后，选择「多端应用模式」，出现模式切换提醒，点击「确定」即可成功切换为多端应用模式。

![](https://res.wx.qq.com/op_res/wF70jN3etKFDv9oWtAxLd12EJpBR6lNfB7A534fNUuLX2cINz-j_vppXELGxBWcRlP8tWQPpsfNbEzgc-ymq-g) ![](https://res.wx.qq.com/op_res/3GAFUFD8zl2RgtJJ6JzzAumGP0ZEcuSCQYi1s1DEiz3lDRK8n2sJAVxOR-9yvJ9KIpfP42ogXL9kHfJ4s2c8pw)

升级为多端项目后，项目主要会出现以下两个变化：

1、在根目录中生成了 project.miniapp.json 配置文件，该文件主要用于进行 App 相关的配置。

![](https://res.wx.qq.com/op_res/3GAFUFD8zl2RgtJJ6JzzAv1SYkRD2P1A1JMrl-DlTDyAAnA2tC6qc9azSG-9mTs65wu61mq51o8UXvbzCVg1RQ)

2、在 project.config.json 文件中，添加了 "projectArchitecture": "multiPlatform" 语句。

![](https://res.wx.qq.com/op_res/3GAFUFD8zl2RgtJJ6JzzAmMOOESnQDtxWa_yaYeYjIhrc730mSwvpaRFq6uAzjzhWxPSpTvGGSQddRPIOFt5MQ)

若需复原回小程序项目，只需删除 project.miniapp.json 文件以及 project.config.json 文件中的 "projectArchitecture": "multiPlatform" 语句即可。

### [#](#_1-3-新建多端项目（适用没有小程序项目的情况）) 1.3 新建多端项目（适用没有小程序项目的情况）

打开「微信开发者工具」新建项目，选择多端应用，填写完成项目相关信息，选择初始模板后，点击「创建」即可。注意，新建多端项目要求填写微信小程序 AppID ，若未拥有，请前往[微信公众平台](https://mp.weixin.qq.com/)注册获得。

若该微信小程序尚未绑定多端应用，请点击「去绑定」，扫码新建多端应用进行绑定操作后方可继续创建。

![](https://res.wx.qq.com/op_res/3GAFUFD8zl2RgtJJ6JzzArTNqZKg-v52u7yer1CUOrmALDkt_pcDOCqHu9l8Z5rtSDCI5rVqAySzFtEYmdfh1g)

若该小程序已绑定多端应用，则可直接创建。并按照需求进行开发即可。

![](https://res.wx.qq.com/op_res/3GAFUFD8zl2RgtJJ6JzzAsZg6YapFB91Rl6TtTgVWfsHVtPG7tZyKpM2hUwVgiaWyO8al8Hx2fHUenWxwoYTaw) ![](https://res.wx.qq.com/op_res/3GAFUFD8zl2RgtJJ6JzzAiShNeRibxlYlmCmV-6RA3Z5hMIqOykBRXEXDzoJ4dHvIWwIL0HTcnyzvBL_oRpCKQ)

### [#](#_1-4-适配改造过程（选做）) 1.4 适配改造过程（选做）

由小程序项目升级而成的多端项目，若能正常构建和运行则可跳过本步骤，否则需要进行部分适配改造。请参照以下注意事项进行检查和代码适配：

1、将小程序项目升级为多端项目后，不影响小程序项目，也不占小程序代码包体积。

2、多端应用有部分接口需要兼容，请参考文档 [需适配的 API 汇总](../api/diffapi/adapt_api)。

3、多端应用有部分组件需要兼容，请参考文档 [需适配的组件汇总](../component/adapt_component)。

4、如果小程序项目使用了云开发，请参考文档 [多端应用使用云开发](../new-capability/cloud/cloud)进行适配。

5、若使用了地图相关能力，请参考文档 [位置服务使用指南](../handbook/devtools/lbs)。

6、若想使用流量主广告，请参考文档 [腾讯优量汇广告使用指南](../handbook/devtools/ad)。

7、小程序订阅消息可使用 App 的消息推送代替，请参考文档 [消息推送使用指南](../handbook/devtools/impush)。

8、若要使用 iOS 的虚拟支付，请参考文档 [wx.miniapp.IAP](../api/miniapp/IAP)。

9、若要使用 iOS 的苹果登录，请参考文档 [wx.appleLogin](../api/auth/wx.appleLogin)。

10、多端应用若要正式上架以及使用微信能力（微信登录、微信分享、微信支付等），则需创建移动应用账号并且与多端应用进行绑定。请参考文档 [绑定移动应用](../handbook/web/bind-openapp)。

11、为了保证 SDK 的安全稳定性以及控制 SDK 体积，使得构建出的 App 安装包体积不过于臃肿，平台侧将 SDK 拆分为基础 SDK 与扩展 SDK，开发者可按需勾选并配置所需的扩展 SDK。
例如在 Android 设备中使用微信登录功能，则需要在 project.miniapp.json 中勾选 Android 的 Open SDK。更多 SDK 对应功能请参考文档 [SDK 介绍](../pre-read/sdk/sdk)。

![](https://res.wx.qq.com/op_res/YsurE1diLd5gwqKR-VbLELWZRCMHpMahU9jyPdnYQb4ht4y4FnzQNy6iJPnDc4PgD14nS1i4uNTyV0MhFRCttQ)

12、为实现一套代码同时适配小程序和 App，平台提供「条件编译」来帮助针对不同的设备和运行环境，预期完成不同的逻辑和页面显示。条件编译支持 wxml、wxss、js/ts、json，less/sass 等文件类型，也支持将不同的资源文件发布到不同的平台。以下是在 js/ts 文件中进行条件编译的示例代码，更多详情或其他文件类型的编码格式请查看文档 [条件编译](../pre-read/condition-compile)。

示例代码：

```
// #if MP
console.log('只在微信小程序执行')
// #elif IOS
console.log('只在 iOS 执行')
// #elif ANDROID
console.log('只在 Android 执行')
// #endif
```

## [#](#二、运行于真机或模拟器) 二、运行于真机或模拟器

本部分主要介绍了如何将多端项目在真机或者模拟器中进行运行调试。

### [#](#_2-1-运行于真机) 2.1 运行于真机

成功升级为多端项目且完成所需适配后，可以将多端应用运行于「真机设备」进行预览调试。详细操作步骤请参考文档 [运行于真机](../handbook/test/device)。

使用数据线连接电脑和手机，iOS 设备需开启开发者模式，Android 设备需开启 USB 调试模式。在工具上方选择版本以及运行设备后，点击「运行」按钮，稍等片刻即可。

![](https://res.wx.qq.com/op_res/YsurE1diLd5gwqKR-VbLEDlr9q-fxAqRm6gl435EuydV115N_h-3WhCMK9dGbN9Opy8EVaJYQlgP_S-y1dqIdA)

注意：

- 对于运行于 Android 真机时出现的 “Android 签名管理”弹窗，若非正式上架，可以直接不填写，使用临时证书构建多端应用即可，更多详见 [Android 签名证书管理](../handbook/build/android-certificate)。
- 对于运行于 iOS 真机时出现的 ”iOS 签名管理“弹窗，若非正式上架，可以直接选择临时证书，输入连接设备的 Apple ID 和密码运行多端应用，更多详见 [iOS 证书申请与配置](../handbook/certificate/ios)。

当构建日志出现绿色字提示「构建成功」后即可在连接的设备上安装并运行多端应用。

![](https://res.wx.qq.com/op_res/YsurE1diLd5gwqKR-VbLEMC-ufbWBSncNKMO4BdPQ7UeOBgELh1I_1RKJ9ZcBEVaLuCd5ChHd8XQVDd7KN-pwQ)

### [#](#_2-2-运行于模拟器) 2.2 运行于模拟器

多端应用同时支持运行于模拟器中进行预览调试。详情可查看文档 [运行于模拟器](../handbook/test/simulator)。

开发者需要先在电脑上安装对应的 [Android 模拟器](../handbook/test/android-simulator) 和 [iOS 模拟器](../handbook/test/ios-simulator)。在设备选择处下拉选择期望的模拟器型号，并点击「运行」。

![](https://res.wx.qq.com/op_res/YsurE1diLd5gwqKR-VbLEDwBdi2IOsBuOR5wjYakw5JoMASuB-xuCjiOrmC143kQ0YZzPNO_9vJRr5LF_tvhCg)

## [#](#三、构建安装包) 三、构建安装包

本部分主要介绍了如何将多端应用打包成 Android 安装包（APK）和 iOS 安装包（IPA）。详细信息可查看文档 [打包生成 APK](../handbook/build/build-apk) 以及 [打包生成 IPA](../handbook/build/build-ipa)。

点击开发者工具上方的「构建」按钮，根据需求选择「打包生成APK」或「打包生成 IPA」。

![](https://res.wx.qq.com/op_res/YsurE1diLd5gwqKR-VbLEKmbpgOsy5HLfSeyqma9iGzsLg3K8wjWebK7yZVZwMzvoIu8hd3ehVv2pnIzdzNwnw)

填写 APK 或 IPA 相关配置后，点击「确定」按钮。

- 关于 APK 配置信息填写说明可查看文档 [打包生成 APK](../handbook/build/build-apk)。
- 关于 IPA 配置信息填写说明可查看文档 [打包生成 IPA](../handbook/build/build-ipa)。
- 使用临时签名构建 IPA 时，需要用数据线连接 iOS 设备，并在构建过程弹窗中输入该 iOS 设备绑定的 Apple ID 账号及密码。注意，平台不会收集开发者的 Apple ID 账号及密码，该数据缓存只保存于本地。

![](https://res.wx.qq.com/op_res/Ifssk3xIm0K67g6W8Z0m4akCn1p7qR8TlsOOlsGvkkeet083Uc8SXSDW-m4Y6IfUwDnGOnff0g1rXEhQ9MaoOg) ![](https://res.wx.qq.com/op_res/Ifssk3xIm0K67g6W8Z0m4ZCauga4_BIlM5vsBkzwylBXJE_1fj_bSdoRkv3-jpGbkeJJTYgIzdK-LQAC8gkJxQ) ![](https://res.wx.qq.com/op_res/Ifssk3xIm0K67g6W8Z0m4QC2l3FyxhTDYCFp_nrgpCwVDUFhOB3iWcv-0YYEZUfzp75aHpReuwEwxcJ14dZWcg)

构建成功后，日志面板和工具右侧都会出现相应的构建成功以及存储位置提示。

![](https://res.wx.qq.com/op_res/Ifssk3xIm0K67g6W8Z0m4X4w5-Db3MGxAV5LnsHyuH0lEyVVC9TvUvJPAGl1F5lg6NOnHVRn-LaIKhtPtDQGVg) ![](https://res.wx.qq.com/op_res/Ifssk3xIm0K67g6W8Z0m4TYyFWE9_lLJ-QAT9_xJUqUmPVINtFVrFCbE4Gn8362N3yoS4E1VylVVm7azrmWq9Q)

若为第一次构建，构建过程中需选择安装包存储位置。若需查看或修改存储位置，可点击工具上方「构建」，选择「设置 apk/ipa 导出路径」进行操作。

![](https://res.wx.qq.com/op_res/Ifssk3xIm0K67g6W8Z0m4b66T8_6uE2Z269ws8YgcPOufXXYYottqNAm027Cxs_4RLitXsDdkf_xifa-7OSoJQ) ![](https://res.wx.qq.com/op_res/Ifssk3xIm0K67g6W8Z0m4crFERxl5ZIZ5FhOgzGcJulbx3ZD3OYeepZLBiqRgLT5raTQ4GfBjC5FcbUmnzCJZA)

## [#](#四、上架应用市场) 四、上架应用市场

App 开发完成后，开发者可前往应用市场按照应用市场的要求和规范提交安装包的审核与发布即可。

注意：

- 开发者需构建正式版安装包用于提交应用市场进行审核，需为该多端应用配置正式的 Package Name 和 Bundle ID，详细请查看文档 [多端应用 Bundle ID 配置](../handbook/web/bundleid-guide) 以及 [多端应用包名配置](../handbook/web/packagename-guide)。
- 上架前需完成 App 的备案，Android 的备案需要填写 Android 签名与公钥，操作文档可查看 [生成 Android 签名与公钥](../handbook/build/record)。
- 关于IPA 上架 App Store，可查看 [IPA 上架 App Store](../handbook/build/ios-publish)。
- 而关于 iOS 的 Bundle ID、平台公钥、签名 MD5 值等，可查看 [APP 备案特征信息填写参考规范](https://cloud.tencent.com/document/product/243/97789#b4df5546-b1ab-46cf-9ef0-c984a546a477)。
- 备案完全后，上架 Android 应用市场还需要软著，开发者可自行寻找第三方服务商完成软著办理。
- 其他更多的常见问题可查看 [上架应用市场常见问题](../troubleshooting/publish)。

Incorrect translation.