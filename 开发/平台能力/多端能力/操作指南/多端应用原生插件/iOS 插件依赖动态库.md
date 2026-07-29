# [#](#iOS-插件依赖动态库) iOS 插件依赖动态库

多端框架下的 iOS 插件最终将打包成一个动态库供多端 App 使用。在[使用 CocoaPods 开发 iOS 插件](iosPluginCocoapods)中介绍了如何引入静态库，本文将同样使用 CocoaPods 介绍插件动态库如何引入第三方动态库依赖。

本文将以依赖 `AFNetworking` 网络库，实现一个发送 HTTP 请求的功能为例进行示例。

## [#](#一、开发环境准备) 一、开发环境准备

1. 根据[原生插件工具操作指引](plugin_guidelines)生成一个多端插件工程项目
2. 安装 Xcode，准备好 iOS 开发环境
3. 安装 CocoaPods，具体可参看[官网指引](https://cocoapods.org/)

## [#](#二、初始化-CocoaPods) 二、初始化 CocoaPods

1. 在上述 1）创建的多端插件工程项目中，在 `ios` 目录下新建一个 Podfile 文件。文件内容如下：

```
platform :ios, '11.0'
use_frameworks!

# YOUR_PLUGIN_ID 替换成你的插件 id
target 'YOUR_PLUGIN_ID' do
    pod "MyPlugin", :path => "."
end

# 必须 为了调试的时候把依赖的动态库也打入 Frameworks 中
target 'demo' do
    pod 'AFNetworking', '~> 4.0'
end
```

2. 在 `ios` 目录下新建一个 MyPlugin.podspec 文件，并指定引入 `AFNetworking`。文件内容如下：

```
# MyPlugin.podspec

Pod::Spec.new do |spec|
    spec.name         = 'MyPlugin'
    spec.version      = '1.0.0'
    spec.summary      = 'Summary of MyPlugin'
    spec.homepage     = 'https://your-framework-website.com'
    spec.author       = { 'Your Name' => 'your@email.com' }
    spec.source       = { :git => 'https://github.com/your/repo.git', :tag => "#{spec.version}" }
    spec.ios.deployment_target = '11.0'

    # 引入 AFNetworking
    spec.dependency 'AFNetworking', '~> 4.0'
end
```

3. 在 `ios` 目录下执行 `pod install`。命令执行完成以后，你的项目将会是以下的结构，新增了 `Pods`，`NativePlugin.xcworkspace`，`Podfile.lock`

![](https://res.wx.qq.com/op_res/lKYV9xBuMm81tqBwVXkeomUimG_8vfiMTlAQPal4Co946Ma90bVWh-HlHys2If3uosiL4kjrW8g7V6QU8Hmbug)

4. 双击 `NativePlugin.xcworkspace`，打开 Xcode，即可看见创建好的项目工程

![](https://res.wx.qq.com/op_res/lKYV9xBuMm81tqBwVXkeojmGy9RB0BO8rEnHgl97AYkorrOlFxsM5xsp0C3TCR1LhyQwLINvIrzlAnR11ncM8w)

5. 在 `YOUR_PLUGIN_ID` 的 target 下，配置链接依赖的动态库

![](https://res.wx.qq.com/op_res/lKYV9xBuMm81tqBwVXkeoikdeBMr7564Ts1u6W4aVIUyvgd308pnTNjae1J6jXxh9d9T73P4hacriFUkyrQvHQ)

## [#](#实现发送-HTTP-请求) 实现发送 HTTP 请求

在 `MyPlugin.mm` 中添加如下代码，实现插件的异步方法完成 HTTP 请求。

![](https://res.wx.qq.com/op_res/lKYV9xBuMm81tqBwVXkeogPOPEN7sCa8GYMY5q8HQrLay-CPhkKXbZw3Gtx3Fwpr5Q-Rq199BqDDh2ToOTRX2Q)

## [#](#四、运行) 四、运行

开发者在开发调试阶段，运行插件工程的方法与 [iOS 原生插件开发指引](iosPlugin#%E8%BF%90%E8%A1%8C)中的指引无异。需要注意的是，使用 CocoaPods 管理项目，需要通过双击 `NativePlugin.xcworkspace` 打开 Xcode。简单区分就是 Xcode 文件列表中是否有 Pods 的相关内容。

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/202401041038040.png)

真机运行返回

![](https://res.wx.qq.com/op_res/lKYV9xBuMm81tqBwVXkeorKyZmZu_jibaimfUiwIWiD-WQlj5yL_zUxMDb8GeDLT-yIbGx244IIHlWty7lwhMg
)

## [#](#五、构建) 五、构建

> 注：开发者工具`构建 iOS 产物`功能目前并不支持直接打包出所需产物，开发者需自行完成打包。

开发者需要构建出 `PLUGIN_ID.framework` 以及依赖的动态库 framework，并把构建产物放至[对应目录](iosPlugin#%E6%9E%84%E5%BB%BA)下；上传插件，最终应用到多端应用中，具体可查看[指引](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/202401041045638.png)。

以本为例，需要构建出如下图所示的 `PLUGIN_ID.framework` 与 AFNetworking.framework。

![](https://res.wx.qq.com/op_res/lKYV9xBuMm81tqBwVXkeogUq6xvat_dUjYmN746MGHySvJ8aSBG1Guck2wOBVZyiSOXrcyc_zoCym1plhA9_xA)

### [#](#自行构建流程示例) 自行构建流程示例

1. 新建一个 PackageFrameworks target

![](https://res.wx.qq.com/op_res/p3_SIHODqbuJ5zgI3gexTklPN6jniIqUnDN-4wC2XrEFiaAXwlqovfRXY2QQywbCId0ABZuJp5Fkup4T6axfzg)

2. 添加 `PLUGIN_ID.framework` 为 target dependencies

![](https://res.wx.qq.com/op_res/p3_SIHODqbuJ5zgI3gexTmnR7J-0g1oISku4KDBP_rNTTxktBk2NhHqllnCr5gFH8CEcfrUZSsnfWNK9c23Rww
)

3. 新建脚本，将构建产物拷贝至多端项目的插件产物目录

> 如果你的插件包含静态库，这里不应该拷贝静态库。因为静态库已经打包在了 `PLUGIN_ID.framework` 内。

![](https://res.wx.qq.com/op_res/p3_SIHODqbuJ5zgI3gexTo0-m-qG5K-oaV88eYWYQD7g9WZmmCF8YcUhJaDlwx9PDr2qv-kp3KwUJiz2_wOw_Q
)

```
OUTPUT_DIR="${SRCROOT}/../build/ios"

# 创建输出目录
mkdir -p "${OUTPUT_DIR}"

echo "OUTPUT_DIR" $OUTPUT_DIR
echo "BUILT_PRODUCTS_DIR" $BUILT_PRODUCTS_DIR
cp -R "${BUILT_PRODUCTS_DIR}/PLUGIN_ID.framework" "${OUTPUT_DIR}"

# 复制依赖的动态库
cp -R "${BUILT_PRODUCTS_DIR}/AFNetworking/AFNetworking.framework" "${OUTPUT_DIR}"
```

4. 点击运行，构建成功后插件将更新至多端项目的插件产物目录

![](https://res.wx.qq.com/op_res/p3_SIHODqbuJ5zgI3gexTvOQg75B4ajMGFDdEzRwHuAUKqHJr-c7PiCEXEZbyt8TDBkbN83D5VKIFXPYLGZuag
)

## [#](#六、总结) 六、总结

在上文中，我们介绍了如何使用 CocoaPods 来引入动态库依赖。开发者可在该项目结构的基础上，主要通过修改 `MyPlugin.podspec` 文件来引入更多的第三方 SDK，添加更多的自定义配置来完成自身需求。

Incorrect translation.