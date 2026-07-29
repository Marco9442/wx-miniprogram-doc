# [#](#使用-CocoaPods-开发-iOS-插件) 使用 CocoaPods 开发 iOS 插件

CocoaPods 是 iOS 项目的依赖管理工具，开发者在开发 iOS 插件的过程中需要引入第三方 SDK 时，可以选择使用 CocoaPods 来管理项目依赖。本文将以 iOS 插件引入微信 Open SDK 并实现拉起小程序为例，指导开发者搭建插件项目。

`注`：

1. 多端框架现已支持[集成微信 Open SDK](../../pre-read/sdk/sdk#%E4%BA%8C%E3%80%81%E6%89%A9%E5%B1%95-sdk) 并有对应的 [JSAPI](../../api/miniapp/launchMiniProgram) 支持跳转小程序。本文仅以示例为目的在多端插件中实现微信 Open SDK 的引入、实现插件方法完成小程序跳转
2. Open SDK 接入流程详解可具体查看[官方文档](https://developers.weixin.qq.com/doc/oplatform/Mobile_App/Access_Guide/iOS)

## [#](#一、开发环境准备) 一、开发环境准备

1. 根据[原生插件工具操作指引](plugin_guidelines)生成一个多端插件工程项目
2. 安装 Xcode，准备好 iOS 开发环境
3. 安装 CocoaPods，具体可参看[官网指引](https://cocoapods.org/)

## [#](#二、初始化-CocoaPods) 二、初始化 CocoaPods

1. 在上述 1）创建的多端插件工程项目中，在 `ios` 目录下新建一个 Podfile 文件。文件内容如下：

```
# YOUR_PLUGIN_ID 替换成你的插件 id
target 'YOUR_PLUGIN_ID' do
  pod "MyPlugin", :path => "."
end
```

2. 在 `ios` 目录下新建一个 MyPlugin.podspec 文件，并指定引入微信 Open SDK。文件内容如下：

```
# MyPlugin.podspec

Pod::Spec.new do |spec|
  spec.name         = 'MyPlugin'
  spec.version      = '1.0.0'
  spec.summary      = 'Summary of MyPlugin'
  spec.homepage     = 'https://your-framework-website.com'
  spec.author       = { 'Your Name' => 'your@email.com' }
  spec.source       = { :git => 'https://github.com/your/repo.git', :tag => "#{spec.version}" }

  # Set your deployment target
  spec.ios.deployment_target = '11.0'
  
  # 引入 Open SDK
  spec.dependency 'WechatOpenSDK-XCFramework'

end
```

3. 在 `ios` 目录下执行 `pod install`。命令执行完成以后，你的项目将会是以下的结构，新增了 `Pods`，`NativePlugin.xcworkspace`，`Podfile.lock`

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/202401031857650.png)

4. 双击 `NativePlugin.xcworkspace`，打开 Xcode，即可看见创建好的项目工程。

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/202401041023464.png)

5. 如开发者在上述 `3` 中看见提示，可按下图添加 `$(inherited)` 到 `Other Linker Flags` 的 Debug 与 Release 配置中。

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/202401041101059.png) ![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/202401041109470.png)

然后重新执行 `pod install`，可看见对应提示消失。

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/202401041111362.png)

## [#](#三、实现跳转小程序) 三、实现跳转小程序

分别在 `MyPlugin.h` 与 `MyPlugin.mm` 添加代码，引入并初始化 Open SDK，实现插件同步方法完成跳转小程序。

```
// MyPlugin.h

#import <Foundation/Foundation.h>
#import <WXApi.h>

NS_ASSUME_NONNULL_BEGIN

@interface MyPlugin: WeAppNativePlugin<WXApiDelegate>

@end

NS_ASSUME_NONNULL_END
```

```
// MyPlugin.mm
#import <Foundation/Foundation.h>
#import <UIKit/UIKit.h>
#import <WXApi.h>
#import "WeAppNativePlugin.framework/WeAppNativePlugin.h"
#import "MyPlugin.h"

__attribute__((constructor))
static void initPlugin() {
    [MyPlugin registerPluginAndInit:[[MyPlugin alloc] init]];
};

@implementation MyPlugin

// 声明插件ID
WEAPP_DEFINE_PLUGIN_ID(YOUR_PLUGIN_ID)

// 声明插件同步方法
WEAPP_EXPORT_PLUGIN_METHOD_SYNC(mySyncFunc, @selector(mySyncFunc:))

- (id)mySyncFunc:(NSDictionary *)param {    

   WXLaunchMiniProgramReq *launchMiniProgramReq = [WXLaunchMiniProgramReq object];
   launchMiniProgramReq.userName = @"YOUR_USERNAME";  // 拉起的小程序的username
   launchMiniProgramReq.miniProgramType = WXMiniProgramTypeTest; // 拉起小程序的类型
   [WXApi sendReq:launchMiniProgramReq completion:nil];        
    
   return @"invoke launch miniprogram";
}

- (void)onReq:(BaseReq*)reqonReq {
    
}

- (void)onResp:(BaseResp*)resp {
    NSLog(@"wxapi onresp %@", resp);
}

// 插件初始化方法，在注册插件后会被自动调用
- (void)initPlugin {
    NSLog(@"initPlugin");
    // 初始化 Open SDK
    [WXApi registerApp:@"YOUR_OPEN_APPID" universalLink:@"YOUR_UNIVERSAL_LINK"];
    [self registerAppDelegateMethod:@selector(application:openURL:options:)];
    [self registerAppDelegateMethod:@selector(application:continueUserActivity:restorationHandler:)];
}

- (void)application:(UIApplication *)app openURL:(NSURL *)url options:(NSDictionary<UIApplicationOpenURLOptionsKey, id> *)options {
    // 按 Open SDK 要求重写方法
    [WXApi handleOpenURL:url delegate:self];
}

- (void)application:(UIApplication *)application continueUserActivity:(NSUserActivity *)userActivity restorationHandler:(void (^)(NSArray<id<UIUserActivityRestoring>> *__nullable restorableObjects))restorationHandler {
    // 按 Open SDK 要求重写方法
    [WXApi handleOpenUniversalLink:userActivity delegate:self];
}

@end
```

## [#](#四、运行) 四、运行

开发者在开发调试阶段，运行插件工程的方法与 [iOS 原生插件开发指引](iosPlugin#%E8%BF%90%E8%A1%8C)中的指引无异。需要注意的是，使用 CocoaPods 管理项目，需要通过双击 `NativePlugin.xcworkspace` 打开 Xcode。简单区分就是 Xcode 文件列表中是否有 Pods 的相关内容。

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/202401041038040.png)

## [#](#五、构建) 五、构建

开发者可以在 `ios` 目录下，执行以下命令打包出插件动态库

```
xcodebuild -workspace NativePlugin.xcworkspace -scheme plugin -configuration Release -arch arm64 -sdk iphoneos -derivedDataPath mypluginbuild
```

命令执行成功之后，可以在 `ios/mypluginbuild` 目录下找到 YOUR\_PLUGIN\_ID.framework

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/202401041130095.png)

最后，开发者可将构建产物放至[对应目录](iosPlugin#%E6%9E%84%E5%BB%BA)下；上传插件，最终应用到多端应用中，具体可查看[指引](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/202401041045638.png)。

## [#](#六、总结) 六、总结

在上文中，我们介绍了如何引入 CocoaPods 来管理我们的 iOS 插件项目。开发者可在该项目结构的基础上，主要通过修改 `MyPlugin.podspec` 文件来引入更多的第三方 SDK，添加更多的自定义配置来完成自身需求

Incorrect translation.