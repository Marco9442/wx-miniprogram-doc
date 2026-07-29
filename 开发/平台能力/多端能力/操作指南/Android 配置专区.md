# [#](#多端应用包名配置) 多端应用包名配置

- 如果多端应用绑定了移动应用账号，那么多端应用的包名（PackageName）同步于微信开放平台移动应用，因此，在多端应用绑定了移动应用账号的情况下，如果开发者需自定义 Android 应用的包名，需前往「微信开放平台-管理中心-移动应用」进行修改并提交审核，待审核通过即可同步到多端应用。
- 如果多端应用未绑定移动应用账号，那么多端应用的包名（PackageName）在多端应用的控制台直接修改即可（默认情况下平台分配的是 "com.tencent.weauth"，该包名仅用于测试）

### [#](#规则说明) 规则说明

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202504222107395.png)

- 「复用移动应用账号」的包名和 Bundle ID 信息与「自定义配置」这两种方式是互斥的，不能同时使用，但是可以随时更换
- 例如，如果开发者选择了「复用移动应用账号」，如果需要选择「自定义配置」，那么需要将移动应用账号解绑了（但是，解绑的瞬间会影响已构建的安装包的使用，需要马上就将包名配置回去）
- 如果开发者选择了「自定义配置」，如果需要选择「复用移动应用账号」，那么只需要将移动应用账号绑定即可，绑定后就会将移动应用账号的包名信息覆盖已经配置的包名信息（即，如果移动应用的包名信息和已配置的包名信息不一致的话，更换了之后也会影响已构建的安装包的使用，开发者需注意）

**即，APP 运行启动的时候会检验构建安装包的时候后台配置的包名信息与当前配置的包名信息是否一致，如果不一致，则会启动失败。因此，开发者在进行包名变更的时候务必要知晓相关风险。**

## [#](#一、自定义包名的操作步骤) 一、自定义包名的操作步骤

- 点击「修改」，选择「自定义配置」

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202504222101441.png) ![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202504222101922.png)

- 然后，填入自定义的包名信息，点击确定即可

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202504222102337.png)

**注意**

- iOS Bundle ID 和 Android 包名不可以同时为空
- 且 Android 包名不可再使用官方分配的测试包名 "com.tencent.weauth"

## [#](#二、包名同步于移动应用的操作步骤) 二、包名同步于移动应用的操作步骤

### [#](#_2-1-注册微信开放平台账号) 2.1 注册微信开放平台账号

前往[微信开放平台](https://open.weixin.qq.com/)注册账号，详细操作步骤可查看[注册开放平台](https://developers.weixin.qq.com/doc/oplatform/Third-party_Platforms/2.0/operation/open/create)。

### [#](#_2-2-完成微信开发者账号认证) 2.2 完成微信开发者账号认证

登录[微信开放平台](https://open.weixin.qq.com/)，前往「账号中心 - 开发者资质认证」完成认证。

注意：未完成认证的微信开放平台账号所创建的移动应用账号无法与多端账号绑定。

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202402291927823.png)

### [#](#_2-3-创建移动应用账号并提交审核) 2.3 创建移动应用账号并提交审核

登录[微信开放平台](https://open.weixin.qq.com/)，前往「管理中心 - 移动应用」创建移动应用账号，并提交审核，详情可查看[创建移动应用](open_application_create)。

注意：未审核通过的移动应用账号无法与多端账号绑定。

创建移动应用过程中即可配置 Android 的包名信息，将移动应用账号与多端账号绑定后，多端应用会将此自定义的包名同步过去。

![](https://res.wx.qq.com/op_res/pdYYUaoqDOCyAzyPGV3vKuIO6iDtQDCdVmOoPwy0PVhW4-_OI7nXrTk7WAmXwRTz7liGkNjVkP2HNxL04h1PHQ)

### [#](#_2-4-修改移动应用包名信息并提交审核) 2.4 修改移动应用包名信息并提交审核

若已有移动应用账号，且需要进行包名信息修改，可按照以下方式进行操作。

登录[微信开放平台](https://open.weixin.qq.com/)，前往「管理中心 - 移动应用」，选择要操作的移动应用，点击「查看」进入详情页。

![](https://res.wx.qq.com/op_res/7ydWCU4N969GCTonD-y95Qx9HelYxRCC1dBisVQjjv3X-x9ZfbQbdq1rggQ62sm1Ayl-pzfch6oDjobrijJu9Q)

在详情页中选择「开发配置」，点击「编辑」。

![](https://res.wx.qq.com/op_res/7ydWCU4N969GCTonD-y95czwfUF6n8yQGz9p_yZFHesqFYiWtpfx_F3ehCpoHWCoYLD51Jf2v4ZNmpFJNBtYKQ)

基本信息可按需修改后点击「保存，下一步」。进入「修改应用平台信息」进行应用包名修改并提交审核。

![](https://res.wx.qq.com/op_res/7ydWCU4N969GCTonD-y95dOEegDV6u7te8ZPcmA_EWj84jBTFVVqKPO0gzVoQeZsYE3zJFsYuls-2lxKaz_mRQ)

### [#](#_2-5-审核通过后，将移动应用与多端应用绑定) 2.5 审核通过后，将移动应用与多端应用绑定

登录[多端应用控制台](https://developers.weixin.qq.com/platform/)，前往「多端应用 - 详情 - 移动应用信息」然后点击「立即绑定移动应用账号」，操作详情可查看[绑定移动应用账号](bind-openapp)。

![](https://res.wx.qq.com/op_res/qu4BW3-JYa-KlWfAdFqtlSkq5ggixgmXiGXdHA127eDRG5cKGDY_XOsEBbYY9KKcY2ERy90EUV7y8NR4zo2BbQ)

### [#](#_2-6-查看已配置成功的包名信息) 2.6 查看已配置成功的包名信息

绑定成功后，可以在[多端应用控制台](https://developers.weixin.qq.com/platform/)的「多端应用 - 详情 - 移动应用信息」中查看，也可在「微信开发者工具 - 构建 - 打包生成 APK」中查看自定义的包名信息。

![](https://res.wx.qq.com/op_res/7ydWCU4N969GCTonD-y95QYRu5gVTBHfewpFasv9nG58A2bPH-KbZjdzknNNreLacoXAHg-PSM4PmMlzhAotkw) ![](https://res.wx.qq.com/op_res/7ydWCU4N969GCTonD-y95Qr_AgPSWoYKfgOb2NfvxtFEj9m79HIzbrHTRDIunnRcV-pcBM6hUi_B9qGlmEHzOA)

Incorrect translation.