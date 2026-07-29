# [#](#鸿蒙应用-app-包和-hap-包的区别) 鸿蒙应用 app 包和 hap 包的区别

构建鸿蒙应用时，会有两种格式的产物，分别是 .app 和 .hap 的包，现对两种产物进行解释说明：

- app 包是发布到应用市场的基本单元，不能直接在设备上安装和运行
- hap 包（Harmony Ability Package）是应用安装和运行的基本单元，包含代码、资源、第三方库及配置文件等，主要分为 entry 和 feature 两种类型。
- 更多介绍可查看[如何理解 App、HAP、HAR、HSP 的关系](https://developer.huawei.com/consumer/cn/doc/harmonyos-faqs/faqs-package-structure-5)

## [#](#app-包和-hap-包如何生成) app 包和 hap 包如何生成

- 生成的 app 包，可以查看保存位置所在路径。如下图所示：

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F20251118175552836.png)

- 构建完成后，在构建面板会输出 app 包

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F20251118175727134.png)

- 而 hap 包的则是在「运行于真机」的时候产生的，具体如下：

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F20251118184444055.png) ![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F20251118184510483.png)

Incorrect translation.