# [#](#打包生成-HarmonyOS-应用) 打包生成 HarmonyOS 应用

完成「多端应用」的模拟器或真机调试后，开发者可构建 HarmonyOS 应用 并安装至 HarmonyOS 设备进一步测试，测试完成后亦可构建正式版的 HarmonyOS 应用包用于提交 AppGallery 进行审核，审核通过后即可上架。

## [#](#一、操作路径) 一、操作路径

前往「微信开发者工具」工具栏，点击「构建 - HarmonyOS 应用」，进入构建面板中完成相关配置，点击确定后即可生成 App。

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F20251118155310217.png)

构建面板的相关配置如下：

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F20251118155420593.png)

## [#](#二、基本信息) 二、基本信息

「构建 HarmonyOS 应用」面板的基本信息来源于 `project.miniapp.json`，如开发者需修改可前往 `project.miniapp.json` 修改。

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F20251118155916078.png)

需注意：图标信息根据打包的类型不同，引用不同的配置，请注意分辨。

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F20251118160038131.png)

## [#](#三、BundleID-信息) 三、BundleID 信息

BundleID 信息来源于多端应用控制台的配置，开发者可在多端应用控制台自定义配置，亦可通过绑定移动应用的方式进行关联，详情可查看[配置鸿蒙应用 BundleID](../ohos/bundleid)

## [#](#四、证书配置) 四、证书配置

详情可查看[鸿蒙证书申请与配置](../ohos/cert)

Incorrect translation.