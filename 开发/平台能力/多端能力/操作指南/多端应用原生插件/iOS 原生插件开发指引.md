# [#](#iOS-原生插件开发指引) iOS 原生插件开发指引

## [#](#一、开发环境准备) 一、开发环境准备

1. 根据[原生插件工具操作指引](plugin_guidelines)生成一个多端插件工程项目
2. 安装 Xcode，准备好 iOS 开发环境
3. iOS SDK >= 1.1.0
4. 开发者工具 Nightly >= 1.06.2311282

## [#](#二、插件工程介绍) 二、插件工程介绍

- 下面以工具生成的多端插件工程项目为例：

  ![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/202311291043899.png)
- 在 Finder 中打开多端插件工程目录下的 `ios` 文件夹，双击点击 `NativePlugin.xcodeproj` 即可打开插件工程

  ![](https://res.wx.qq.com/op_res/bTqgwxMPWujf-a7HBal5GTjfSfyK3pVUYEocsWxR_B6ObZ-Q_nvafMMc6_3YFdTLuOtQ9wNX4Ppt08YKuMQNyQ)
- 打开后的效果如下：

  ![](https://res.wx.qq.com/op_res/bTqgwxMPWujf-a7HBal5GRJ__eJxwd8nkHrlPDoPsOb7O3k698Wk3TpLO3-uDjmuBOq4W5605c0LzmmxWsE7tw)

### [#](#工程目录结构说明) 工程目录结构说明

```
    |-- demo // 开发插件时的示例 App 工程，但在多端插件开发中并无实际使用到，开发者无需改动此文件夹的内容
    |-- MyPlugin // 插件主要内容，开发者的改动应在此目录下进行
        |-- WeAppNativePlugin.framework // 多端插件与多端核心 SDK 通信依赖的静态库
        |-- MyPlugin.h
        |-- MyPlugin.mm
    |-- resources // 调试插件时需要用到的资源目录
        |-- arm64 // 用于真机调试
        |-- x86 // 用于模拟器调试
        |-- script // 用于开发调试的辅助脚本
```

### [#](#工程-Xcode-配置说明) 工程 Xcode 配置说明

> 以下配置在创建 iOS 插件工程时均已设置完成，开发者不应随意改动

- Demo BundleId：需与对应的多端应用绑定的移动应用的 iOS 信息匹配

  ![](https://res.wx.qq.com/op_res/6tKrdvqlFvyl5UoDsi1XDqpxfa2bAEJo-UZZRGIvZ4y3QXLVyttLjKgMTdx20SiJpPIDGUw4ybxUd5NWCR2j_Q)

  多端应用绑定的移动应用的 iOS 信息如下图：

  ![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202310111056968.png)

  插件的 bundleId 在项目创建时已自动生成，开发者可自定义修改

  ![](https://res.wx.qq.com/op_res/6tKrdvqlFvyl5UoDsi1XDrt0YzDMQOVLf9C0FOERu-85EK2erepoWw49cg_645UdJZ8IV4Hkuo9ogVi_TClc_w)
- Scheme：scheme 名称固定为 `plugin` 以及插件构建产物名称固定格式为 `${pluginId}.framework`

  ![](https://res.wx.qq.com/op_res/bTqgwxMPWujf-a7HBal5GRCZ9Yv7u0p4jODcyK23qzDF0d7Aj1igDaDEMbQBC_1IUhQbESuNp26scSR69x7KsQ)
- Build Phases：Run Script 阶段处理了使用插件构建产物的 demo App，这里的顺序与脚本内容开发者都不应该改动。

  ![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/202311291046239.png)

### [#](#运行) 运行

按照上述的指引完成配置后，即可在微信开发者工具中开始运行和调试。

1. 在微信开发者工具切换至「多端插件模式」后，选择「iOS」点击「运行」。工具将自动打开 Xcode 工程。

   ![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/202311291052831.png)
2. 在打开的 Xcode 中点击「运行」按钮，即可看到示例工程运行效果

   ![](https://res.wx.qq.com/op_res/D8RuSf7bA63aLse3SB_s-rMhLC4yeK7Sn4w_QUlYbwCCdDlrMdJHuGG6CMYNTJ5OnnLHFgbqxATkP4x6UvlLIw)
3. 在 Xcode 模拟器上，先点击「加载多端插件」，加载成功后再点击「调用多端插件」，即可通过 vconsole 看到插件方法的返回。

   ![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/202311291054256.png)

   注：如果遇到 M1 电脑模拟器按钮点击无响应，可查看[指引](../../troubleshooting/dev#_1%E3%80%81ios-m1-%E7%9A%84%E7%94%B5%E8%84%91%E5%87%BA%E7%8E%B0%E6%A8%A1%E6%8B%9F%E5%99%A8%E6%8C%89%E9%92%AE%E7%82%B9%E5%87%BB%E6%97%A0%E5%93%8D%E5%BA%94%E5%A6%82%E4%BD%95%E5%A4%84%E7%90%86)
4. 后续开发者修改小程序代码、project.miniapp.json 中的配置，仅需保持工具开启状态；工具会与 Xcode 通信完成对应的资源替换，开发者只需要专注在 Xcode 重新编译运行即可。在 Xcode build log 中，可以看到 Xcode 与工具通信的日志。

   ![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/202312221144353.png)

   工具的构建面板也有相关的日志输出：

   ![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/202312221143067.png)

   如果开发者发现资源替换未生效，Xcode build log 中与没有工具通信的日志、或者与工具通信失败，请自查：

   - 工具版本 Nightly >= 1.06.2311282
   - 工具「设置」->「安全设置」中已开启多端插件服务端口
   - 插件模板已更新至最新（可重新创建插件项目）

## [#](#三、插件开发) 三、插件开发

### [#](#多端应用与多端插件的调用时序介绍) 多端应用与多端插件的调用时序介绍

在开始 iOS 多端插件的开发前，理解多端应用与多端插件的调用时序将更好帮助开发者进行开发。

sequenceDiagram
participant app as 多端应用
participant plugin as 多端插件
app->>app:wx.miniapp.loadNativePlugin 加载插件
app->>plugin: 加载插件 framework
plugin->>plugin: 载入时即实例化插件对象
app->>plugin: 加载插件，进行一系列初始化操作（包括 id 注册、插件方法注册、插件 initPlugin 方法调用）
app->>app: 持有插件实例 pluginInstance
note over app,plugin: 插件加载完成
app->>plugin: pluginInstance.func() 进行插件方法的调用

### [#](#插件开发) 插件开发

在环境准备中创建的 iOS 插件工程模板，已替开发者完成：

> 以下只有 `插件实例化` 与 `注册插件 Id` 是必需操作，剩余操作开发者可按自身需求进行调整。

#### [#](#_1-插件实例化) 1. 插件实例化

```
__attribute__((constructor))
static void initPlugin() {
    [MyPlugin registerPluginAndInit:[[MyPlugin alloc] init]];
};
```

#### [#](#_2-注册插件-Id) 2. 注册插件 Id

使用宏方法 `WEAPP_DEFINE_PLUGIN_ID(pluginId)` 注册插件 Id

```
WEAPP_DEFINE_PLUGIN_ID(YOUR_PLUGIN_ID)
```

#### [#](#_3-定义插件实例方法-initPlugin) 3. 定义插件实例方法 initPlugin

```
// 插件初始化方法，在注册插件后会被自动调用
- (void)initPlugin {
    NSLog(@"initPlugin");
}
```

#### [#](#_4-注册同步方法) 4. 注册同步方法

- 注册方法

使用宏方法 `WEAPP_EXPORT_PLUGIN_METHOD_SYNC(methodName, methodSelector)` 注册同步方法。

| 参数 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| methodName |  | 是 | 在 js 层可用获取的 pluginInstance.methodName 进行方法调用 |
| methodSelector | SEL | 是 | MyPlugin 定义的插件实例方法 Selector |

- 同步方法的入参与出参

| 参数 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| 入参 | NSDictionary \* | 否 | 在 js 层调用 pluginInstance.methodName 时传入的 Object 类型参数 |
| 出参 | 可序列化类型 | 否 | 在 js 层调用 pluginInstance.methodName 的返回 |

- 代码示例

OC 侧的插件同步方法实现

```
WEAPP_EXPORT_PLUGIN_METHOD_SYNC(mySyncFunc, @selector(mySyncFunc:))

- (id)mySyncFunc:(NSDictionary *)param {
    NSLog(@"mySyncFunc %@", param);
        
    return @"mySyncFunc";
}
```

JS 侧的方法调用

```
wx.miniapp.loadNativePlugin({
    pluginId: 'YOUR_PLUGIN_ID',
    success: (plugin) => {
        console.log('load plugin success')
        const ret = plugin.mySyncFunc({ a: 'hello', b: [1,2] })
        console.log('mySyncFunc ret:', ret)
    },
    fail: (e) => {
        console.log('load plugin fail', e)
    }
})
```

#### [#](#_5-注册异步方法) 5. 注册异步方法

- 注册方法

使用宏方法 `WEAPP_EXPORT_PLUGIN_METHOD_ASYNC(methodName, methodSelector)` 注册异步方法。

| 参数 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| methodName |  | 是 | 在 js 层可用获取的 pluginInstance.methodName 进行方法调用 |
| methodSelector | SEL | 是 | MyPlugin 定义的插件实例方法 Selector |

- 异步方法的入参与出参

| 参数 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| 入参1 | NSDictionary \* | 否 | 在 js 层调用 pluginInstance.methodName 时传入的第 1 个 Object 类型参数 |
| 入参2 | WeAppNativePluginCallback | 否 | 在 js 层调用 pluginInstance.methodName 时传入的第 2 个 Function 类型参数，在 OC 侧可通过该入参回调给 js 层。该回调方法支持一个可序列化类型的参数 |

- 代码示例

OC 侧的插件异步方法实现

```
WEAPP_EXPORT_PLUGIN_METHOD_ASYNC(myAsyncFuncwithCallback, @selector(myAsyncFunc:withCallback:))

- (void)myAsyncFunc:(NSDictionary *)param withCallback:(WeAppNativePluginCallback)callback {
    NSLog(@"myAsyncFunc %@", param);

    callback(@{ @"a": @"1", @"b": @[@1, @2], @"c": @3 });
}
```

JS 侧的方法调用

```
wx.miniapp.loadNativePlugin({
    pluginId: 'YOUR_PLUGIN_ID',
    success: (plugin) => {
        console.log('load plugin success')
        plugin.myAsyncFuncwithCallback({ a: 'hello', b: [1,2] }, (ret) => {
            console.log('myAsyncFuncwithCallback ret:', ret)
        })
    },
    fail: (e) => {
        console.log('load plugin fail', e)
    }
})
```

#### [#](#_6-注册-AppDelegate-方法) 6. 注册 AppDelegate 方法

多端 iOS 插件现在支持监听 AppDelegate 方法

- application:openURL:options:
- application:continueUserActivity:restorationHandler:
- application:didFinishLaunchingWithOptions:
- application:didRegisterForRemoteNotificationsWithDeviceToken:
- application:didFailToRegisterForRemoteNotificationsWithError

使用方法

1. 开发者可通过调用继承于 `WeAppNativePlugin` 的方法 `registerAppDelegateMethod:` 来注册监听。
2. 监听方法是插件对象的实例方法，其中方法签名与需监听方法保持一致。

```
// 在 initPlugin 中注册监听
- (void)initPlugin {
    NSLog(@"initPlugin");
    [self registerAppDelegateMethod:@selector(application:openURL:options:)];
    [self registerAppDelegateMethod:@selector(application:continueUserActivity:restorationHandler:)];
}

// 当 App 通过 URL Scheme 被打开时，将回调到此处
- (void)application:(UIApplication *)app openURL:(NSURL *)url options:(NSDictionary<UIApplicationOpenURLOptionsKey, id> *)options {
    NSLog(@"url scheme");
}

// 当 App 通过 Universal Link 被打开时，将回调到此处
- (void)application:(UIApplication *)application continueUserActivity:(NSUserActivity *)userActivity restorationHandler:(void (^)(NSArray<id<UIUserActivityRestoring>> *__nullable restorableObjects))restorationHandler {
    NSLog(@"universal link");
}
```

#### [#](#_7-插件事件监听) 7. 插件事件监听

从 iOS SDK >= 1.2.5 开始，支持在 JS 侧监听来自 Native 的事件。

- 在 Native 侧通过调用继承于 WeAppNativePlugin 的方法 `sendMiniPluginEvent:` 可向 JS 侧发送事件。

| 参数 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | NSDictionary \* | 是 | 在 js 侧的监听方法获得的入参 |

- 在 JS 侧可使用插件实例的 `onMiniPluginEvent` 方法注册监听

| 参数 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Function | 是 | Native 侧向 JS 侧发送事件时触发的回调，支持注册多个回调 |

- 在 JS 侧可使用插件实例的 `offMiniPluginEvent` 取消监听。

| 参数 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Function | 否 | 取消监听；当未指定需要取消的回调时，取消所有监听回调 |

- 代码示例

OC 侧的插件异步方法实现

```
- (void)sendMsg {
    [self sendMiniPluginEvent:@{ @"msg": @"this is an event from plugin" }];
}
```

JS 侧的方法调用

```
const listener1 = (param) => {
  console.log('onMiniPluginEvent listener1', param)
}

const listener2 = (param) => {
  console.log('onMiniPluginEvent listener2', param)
}

wx.miniapp.loadNativePlugin({
    pluginId: 'YOUR_PLUGIN_ID',
    success: (plugin) => {
        plugin.onMiniPluginEvent(listener1)
        plugin.onMiniPluginEvent(listener2)
    }
})
```

#### [#](#_8-插件资源拷贝到主包) 8. 插件资源拷贝到主包

一般情况下，插件依赖的资源文件是一并打包放置在动态库中。如果开发者有需求将资源文件直接放置在主包中，可在插件项目的 `MiniPlugin.bundle/PluginConfig.plist` 里填写配置项 `CopyResourcesToMainBundle`。如下图所示，在多端应用构建时会把 `MiniPlugin.bundle/resource.txt` 拷贝到构建生成的 IPA 的一级目录下。

> 注：需要拷贝到主包的资源文件需放置在 `MiniPlugin.bundle` 中。

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/202311131046984.png)

#### [#](#_9-将小程序的资源拷贝到插件中) 9. 将小程序的资源拷贝到插件中

使用插件的时候，可以将小程序目录下的资源拷贝到使用的插件内。

project.miniapp.json文件的可视化配置中，在使用的插件下可以看到"将文件添加到原生插件中"，配置相对于小程序项目根路径的相对路径。

#### [#](#_10-启动即加载插件) 10. 启动即加载插件

一般使用插件的时候，只有当loadNativePlugin才会动态连接插件。但是部分场景需要app一启动就加载插件。

**在开发阶段**，在插件的小程序项目project.miniapp.json中，配置loadWhenStart:true。即可模拟App启动即加载

```
  "mini-plugin": {
    "ios": {
      "loadWhenStart": true
    }
  }
```

**在使用阶段**，project.miniapp.json文件的可视化配置中，在使用的插件下可以看到"是否在App启动的时候就自动加载"。

**工具在1.06.2405222版本开始支持**

#### [#](#_11-App-Extensions) 11. App Extensions

多端插件开发支持[App Extensions](https://developer.apple.com/app-extensions/)。比如消息通知扩展，分享组件，桌面小控件等。xcode 的原生开发项目中，[本身支持开发 appex 产物](https://developer.apple.com/library/archive/documentation/General/Conceptual/ExtensibilityPG/ExtensionCreation.html)。

但是为了能在多端框架中使用，需要将 appex 编译的 **scheme** 和 **target** 名字设置为plugin id 开头的内容。在构建plugin的时候会将编译的appex产物上传。

schemes

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202407171623235.png)

targets
![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202407171622948.png)

在最终使用的时候，这些 appex 都需要进行签名。所以使用插件的小程序项目需要去苹果后台配置对应的 bundle id 和 profiles，并添加到project.miniapp.json中。

```
  "mini-plugin": {
    "ios": [
      {
        "open": true,
        "pluginId": "wxaaaaaaaaaaaa",
        "pluginVersion": "1.0.0",
        "isFromLocal": false,
        "loadWhenStart": true,
        "appexProfiles": {
          "NSE": {
            "enable": true,
            "bundleID": "xxxx.xxx.xxx.xxx",
            "profilePath": "xxxx/xxxx/开发用的.mobileprovision",
            "distributeProfilePath": "xxxx/xxxx/分发用的证书.mobileprovision"
          },
          "ShareExt": {
            "enable": true,
            "bundleID": "xxxx.xxx.xxx.xxx",
            "profilePath": "xxxx/xxxx/开发用的.mobileprovision",
            "distributeProfilePath": "xxxx/xxxx/分发用的证书.mobileprovision"
          }
        },
        "resourcePath": "pluginResources/wxaaaaaaaaaaaa.json"
      }
    ],
    "android": []
  }
```

**工具在1.06.2405222版本开始支持**

### [#](#构建) 构建

插件调试完毕之后，开发者需要构建出 `${pluginId}.framework` 动态库供多端应用使用。

工具中提供了「构建 iOS 插件产物」的按钮，用于帮助开发者快速构建支持 arm64 的动态库到规定的上传目录中。iOS 插件产物规定放置于目录 `build/ios` 下，用于后续上传动态库。

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/202311291055798.png)

如开发者有更加个性化的构建流程，可自行构建 iOS 插件产物，并将插件产物置于规定目录下。

### [#](#构建失败定位) 构建失败定位

在工具中使用「构建 iOS 插件产物」，本质是调用 xcode 命令帮助开发者构建。当遇到工具构建失败时，开发者可在 `ios` 目录下使用以下构建脚本自行定位失败原因：

```
# 修改成自己的插件id
PLUGIN_ID="YOUR_PLUGIN_ID"

TEMP_BUILD_DIR=$(mktemp -d)

xcodebuild clean -project NativePlugin.xcodeproj -scheme plugin -derivedDataPath $TEMP_BUILD_DIR

xcodebuild -project NativePlugin.xcodeproj -scheme plugin -destination generic/platform=iOS -derivedDataPath $TEMP_BUILD_DIR -configuration Release ARCHS=arm64 ONLY_ACTIVE_ARCH=NO

xcodebuild -project NativePlugin.xcodeproj -scheme plugin -destination "generic/platform=iOS Simulator" -derivedDataPath $TEMP_BUILD_DIR -configuration Release ARCHS=x86_64 ONLY_ACTIVE_ARCH=NO

FAT_PATH=$TEMP_BUILD_DIR/Build/Products
LINKMAP_PATH=$TEMP_BUILD_DIR/Build/Intermediates.noindex
SIMULATOR_LIB_PATH=$FAT_PATH/Release-iphonesimulator
IPHONE_LIB_PATH=$FAT_PATH/Release-iphoneos

lipo -create $IPHONE_LIB_PATH/$PLUGIN_ID.framework/$PLUGIN_ID $SIMULATOR_LIB_PATH/$PLUGIN_ID.framework/$PLUGIN_ID -output $FAT_PATH/$PLUGIN_ID
```

## [#](#四、使用-CocoaPods-管理项目依赖) 四、使用 CocoaPods 管理项目依赖

开发者可参考[使用 CocoaPods 开发 iOS 插件](iosPluginCocoapods)。

## [#](#五、注意事项) 五、注意事项

- 如果你的插件工程中引入了涉及 iOS 隐私清单的内容，则需要在你的插件工程中引入 `PrivacyInfo.xcprivacy` 文件，可参考[PrivacyInfo.xcprivacy 模板](../../pre-read/sdk/xcprivacy)；否则在提交上架的时候会出现类似下方的报错
- 补充，更多信息可前往苹果官网查看[Privacy manifest files](https://developer.apple.com/documentation/bundleresources/privacy_manifest_files)或者[Upcoming third-party SDK requirements](https://developer.apple.com/support/third-party-SDK-requirements)

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202409231115181.png)

Incorrect translation.