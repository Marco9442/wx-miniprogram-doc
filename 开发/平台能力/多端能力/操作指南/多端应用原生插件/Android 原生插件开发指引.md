# [#](#Android-原生插件开发指引) Android 原生插件开发指引

## [#](#一、开发环境准备) 一、开发环境准备

1. 根据[原生插件工具操作指引](plugin_guidelines)生成一个多端插件工程项目
2. 安装 **微信开发者工具**、**JDK** 以及 **Android Studio（Android SDK）**
3. 环境依赖：

   - JAVA 版本：`JAVA8` <= JAVA 版本 <= `JAVA15`
   - Gradle 版本：`6.7.1`
   - [微信开发者工具](https://developers.weixin.qq.com/miniprogram/dev/devtools/log)请使用 `1.06.2311282` 及以上的版本

## [#](#二、插件工程介绍) 二、插件工程介绍

- 下面以工具生成的多端插件工程项目为例：

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/amin/202311291428827.png)

- 根目录下的 Android 目录就是原生插件的项目工程

### [#](#工程目录) 工程目录

```
.
├── app // 示例应用，基本无需改动，也不建议改动（云构建下您无法修改 app 下的逻辑）
├── build.gradle // Gradle 构建脚本
├── compile // 存放了证书
├── gradle // 存储 Gradle Wrapper 的目录
├── gradle.properties // Gradle 属性文件
├── gradlew // Gradle Wrapper 的启动脚本
├── gradlew.bat // Gradle Wrapper 的启动脚本
├── miniapp.json // 运行应用时的一些配置文件，基本可以不用动
├── miniapp.plugin.json // 插件相关配置，后面具体说明
├── plugin // 插件目录，插件开发主要需要修改该目录代码，后面具体说明
└── settings.gradle // Gradle 设置文件
```

#### [#](#miniapp-plugin-json) miniapp.plugin.json

```
{
  "pluginId": "wx45c6d53ff86fd405", // 插件 ID，自动生成
  "pluginVersion": "0.0.1", // 插件 版本，构建时需要用到
  "debugSaaAVersion": "1.0.0", // 依赖的 saaa sdk 版本（该 sdk 仅包含基本渲染功能用于插件开发，进行插件开发时请勿调用除了插件暴露的 jsapi 外的方法，即wx.request等 wx api 均不支持）
  "debugWithAar": false, // 默认为 false，在构建 aar 产物后可以设成 true 进行测试，详情看下方插件构建流程
  "pluginPackageName": "com.donut.wx45c6d53ff86fd405" // 自动生成的插件包名
}
```

#### [#](#plugin-目录) plugin 目录

```
.
├── build.gradle // Gradle 构建脚本
├── consumer-rules.pro
├── gradle.properties
├── libs // 存放依赖的 sdk，sdk 会自动下载
├── proguard-rules.pro
└── src
    └── main
        ├── AndroidManifest.xml
        ├── java
        │   └── com
        │       └── donut
        │           └── wx45c6d53ff86fd405
        │               └── PluginManager.kt // 插件入口文件，后面详细说明
        └── resources
            └── META-INF
                └── services
                    └── com.tencent.luggage.wxa.SaaA.plugin.NativePluginInterface // 声明注册插件，如果上面的PluginManager类有变更，需要同步修改这里
```

## [#](#三、运行多端插件项目) 三、运行多端插件项目

#### [#](#_1-工具上切换到-Android-模式后点运行，会直接拉起-Android-Studio) 1. 工具上切换到 Android 模式后点运行，会直接拉起 Android Studio

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/amin/202311291452329.png)

本地环境要求：

- windows 需要安装在 C 盘（安装在 C 盘以外的目录请手动打开 Android Studio 导入项目）
- mac 可能需要先创建命令行脚本，如下截图

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/amin/202311291501110.png) ![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/amin/202311291502316.png)

如果点运行拉起 Android Studio 失败，你也可以自己手动在 Android Studio 导入打开项目，不影响后续流程

##### [#](#常见问题-1) 常见问题 1

- 导入的时候有可能会报 `unsupported Java` 或者 `We recommend upgrading to Gradle version xx`，如下图：

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/amin/202310261926144.png) ![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202504081222309.png)

- 解决方案：通常是 java home 的问题导致的，因此开发者需确认你的 Android Studio 里使用的 java 版本，参考下图：

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/amin/202310261927557.png)

#### [#](#_2-Android-Studio-中点击「运行」按钮，即可看到示例工程运行效果。) 2. Android Studio 中点击「运行」按钮，即可看到示例工程运行效果。

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/amin/202310261935143.png)

#### [#](#_3-先点击「加载多端插件」，加载成功后再点击「调用多端插件」，即可通过-vconsole-看到插件方法的返回。) 3. 先点击「加载多端插件」，加载成功后再点击「调用多端插件」，即可通过 vconsole 看到插件方法的返回。

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/amin/202311291449491.png)

注：`1.06.2311282` 及以上的版本的开发者工具不需要手动构建 Android 资源包，开发者工具保持运行时，在 Android Studio 中点击「运行」时会自动构建最新的小程序代码包资源

构建日志如图：

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/amin/202312071409317.png)

如果这里显示 url 为空，请确保在「设置」->「安全设置」中多端插件服务端口已经开启

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/amin/202311291716730.png)

## [#](#四、插件开发) 四、插件开发

> 根据不同的场景，Android 插件的类型可分为以下几种，具体请查看下方详细介绍

- [NativePlugin 通用拓展插件](androidPluginBase)
- [NativePluginApplication 应用 lifecrycle 插件](androidPluginApplication)
- [NativePrivacyPlugin 隐私授权相关插件](androidPluginPrivacy)

## [#](#五、插件构建) 五、插件构建

### [#](#构建命令) 构建命令

安卓插件必需构建上传后，才能真正使用

在工具点击`构建 -> 构建 Android 插件产物`，会自动执行构建命令`./gradlew :plugin:build`，构建完成后会生成一个 localAar 文件夹，最终把 localAar 文件夹内容 copy 到目录 `build/android` 下，用于后续上传
![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/amin/202310261942706.png)

- 版本号读取的是`miniapp.plugin.json`里的`pluginVersion`字段

### [#](#第三方依赖-sdk-处理) 第三方依赖 sdk 处理

- maven 源

如果用户有第三方依赖 sdk（maven 源），可以配置 pom 文件
![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/amin/202310261943116.png)
格式参考：

```
project.ext.pomDeps = [
    "com.tencent.tpns:tpns" : "1.4.0.1-release",
]
```

> tip: 支持 Maven Central，以及下列仓库

- https://repo1.maven.org/maven2/
- https://dl.google.com/dl/android/maven2
- https://developer.huawei.com/repo/

> libs 或者 不在上述 maven 源列表内的

请参考使用(fat-aar-android)[https://github.com/kezong/fat-aar-android]把依赖 embed 进 aar 包

### [#](#apply-gradle-plugin) apply gradle plugin

接安卓的厂商推送时可能会需要厂商的插件，例如华为厂商可能需要`apply plugin: 'com.huawei.agconnect'`，远程构建时可以在`project.miniapp.json`通过`pluginConfigPath`配置
![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/amin/202407181107064.png)
该路径的配置文件需要是一个合法 **json** 文件（该文件在云构建时使用），参考格式如下

```
{
    "project": {
        // 依赖的配置，可选，构建 app 时会合并到项目根目录build.gradle中（使用时不要复制注释）
        "dependencies": [
          "com.huawei.agconnect:agcp:1.6.0.300"
        ]
    },
    "app": {
        // 需要使用的gradle plugin，可选，构建 app 时会生效 （使用时不要复制注释）
       "plugins": [
          "com.huawei.agconnect"
       ]
    }
}
```

添加后，会在项目根目录的build.gradle的顶部添加gradle插件的依赖

```
buildscript {
    dependencies {
        classpath 'com.huawei.agconnect:agcp:1.6.0.300'
    }
}
```

在 app 目录 build.gradle 文件底部添加 apply plugin

```
apply plugin: 'com.huawei.agconnect'
```

如果需要配套上传其他文件，可以参考 [Android 配置原生资源](../devtools/android-native-resource)

## [#](#六、插件上传) 六、插件上传

安卓原生插件必须上传后才能在云构建的项目中使用
![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/amin/202312071418366.png)

- 为了云构建使用插件能正常运行，请在上传前先使用`构建产物`测试一下

1. 确保 `localAar` 文件夹里已经有构建产物
2. `miniapp.plugin.json`文件里新增一个`debugWithAar`字段，设置为 true
   ![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/amin/202311291707010.png)
3. Android Studio 中点击「运行」，在 `build` 日志里能看见 `Use Aar` 的输出
   ![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/amin/%E4%BC%81%E4%B8%9A%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_f1b633ce-407d-46cc-ba39-412d32baee6c.png)
4. 自测，确保使用构建产物下，逻辑也符合预期(使用了第三方依赖的尤其注意是否已经处理)

请注意:

1. 上传时会上传 `build/android` 和 `android/plugin` 两个文件夹
2. 上传的时候版本号必须和构建版本号(`miniapp.plugin.json`里的`pluginVersion`)一致，否则使用会有问题
   ![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/amin/202310261945902.png)

## [#](#七、云构建使用插件) 七、云构建使用插件

在你多端应用的项目里配置需要使用使用的插件 ID
![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/amin/202310261946380.png)

- 在使用插件的多端应用的项目里，Android Sdk 版本需要 `>= 1.1.0`
- 如果需要 `activity` 或者 `事件通知`，Android Sdk 版本请选择 `1.1.9` 及以上

## [#](#debugSaaAVersion-版本更新) debugSaaAVersion 版本更新

Android Sdk 所有版本请查看[Android SDK 更新日志](../../changelog/android/changelog)

### [#](#_1-0-6) 1.0.6

> 对应最小Android Sdk Version：1.3.13

1. `A` 新增 允许[在主进程执行代码](#在主进程执行代码)
2. `A` 新增 [requestPermission](#requestPermission)

### [#](#_1-0-7) 1.0.7

> 对应最小Android Sdk Version：1.3.27

1. `A` 新增 支持[application 生命周期](androidPluginApplication)

### [#](#_1-0-8) 1.0.8

> 对应最小Android Sdk Version：1.3.28

1. `A` 新增 支持[startactivityForResult](#startactivityForResult)

### [#](#_1-0-10) 1.0.10

> 对应最小Android Sdk Version：1.5.2

1. `U` 更新 对齐云构建逻辑，如果低于该版本，建议重新生成插件项目

## [#](#常见问题) 常见问题

#### [#](#Q：调试的时候可以，上传之后使用云构建就失败了) Q：调试的时候可以，上传之后使用云构建就失败了

0. 请先检查是否改动过`app`目录（云构建您无法直接修改 app 目录下逻辑，只能读到插件构建产物）
1. 请务必先保证使用**构建产物**自测过(`miniapp.plugin.json`文件`debugWithAar`为`true`)
2. 检查下混淆配置有没有问题，可以构建一个 release 版本的 apk 自测下
   - 先 clean project(`./gradlew clean`)
   - `./gradlew :app:assembleRelease` 然后看 `build/outpus/apk/arm64/release`下的 apk
   - 如果需要新增混淆配置，可以在`plugin/consumer-rules.pro`文件内处理（请勿删除该文件原有配置）
3. adb logcat 或者 Android Studio 可以看错误信息，可以看下抛出的错误信息是否有用

#### [#](#Q：调试时正常，上传后使用闪退报-java-lang-NoClassDefFoundError) Q：调试时正常，上传后使用闪退报 java.lang.NoClassDefFoundError

建议检查混淆配置或者第三方依赖配置

#### [#](#Q：-Execution-failed-for-task-plugin-generatePom) Q： Execution failed for task ':plugin:generatePom'

请参考文档检查你的 pom 配置是否配置正确

#### [#](#Q：为什么工程改变源码无效也无法断点？) Q：为什么工程改变源码无效也无法断点？

- 请确认(`miniapp.plugin.json`文件`debugWithAar`是不是被设成了`true`)
- 请确认断点进程是不是选择的是`:wxa_container0`

#### [#](#Q：为什么小程序代码修改后在插件工程里看不到更新？) Q：为什么小程序代码修改后在插件工程里看不到更新？

- 请查看构建日志，更新资源是否成功，如不成功，请参考[文档](#三、运行多端插件项目)确认工具端口是否打开

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/amin/202312071409317.png)

- 确认端口打开后，若还更新失败，可以检查微信开发者工具里的构建面板，查看具体编译报错

#### [#](#Q：上传时报错提醒上传的版本与构建版本不一致) Q：上传时报错提醒上传的版本与构建版本不一致

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/amin/202409121532023.png)

- 请确认`build/android`文件夹下是否有符合命名规范的文件

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/amin/202310261942706.png)

- 确保上传的时候版本号和构建版本号一致，也就是说需要存在以下文件：`build/android/{miniAppPluginId}/${version}/${miniAppPluginId}-${version}.aar`

Incorrect translation.