# [#](#安装-Android-模拟器) 安装 Android 模拟器

- 以下操作步骤适用于 Windows 系统和 Mac 系统
- 本文适用于通过 Android Studio 进行安装 Android 模拟器，开发者亦可选择其他方式安装 Android 模拟器

### [#](#_1、下载-Android-Studio) 1、下载 Android Studio

- 下载 [Android Studio](https://developer.android.google.cn/studio/)。
- 当前最新版本为：android-studio-2021.3.1.17（2022-12-21），如果笔记本的芯片是 Apple M1 Pro 则下载 [Mac with Apple chip](https://redirector.gvt1.com/edgedl/android/studio/install/2021.3.1.17/android-studio-2021.3.1.17-mac_arm.dmg)，反之下载 [Mac with Intel chip](https://redirector.gvt1.com/edgedl/android/studio/install/2021.3.1.17/android-studio-2021.3.1.17-mac.dmg)。开发者需依据系统实际情况下载合适的版本
- 点击安装，安装时选择 `Custom` 选项，不选 `Standard`
- 确保选中了以下几项：`Android SDK`、`Android SDK Platform`、`Android Virtual Device`

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202212231040924.png)

### [#](#_2、创建模拟器) 2、创建模拟器

- 如下图，点击右上角的「模拟器」图标，点击「Create device」
- 进入「Virtual Device Configuration」面板后，按照指引完成配置，即可成功创建模拟器

![](https://github.com/yujon/ipa-mac-builder/assets/16963584/d8696b17-9d78-473a-a609-f5050a636818) ![image](https://github.com/yujon/ipa-mac-builder/assets/16963584/2f4804a9-9701-42ec-9333-d0ca5f50bde6) ![image](https://github.com/yujon/ipa-mac-builder/assets/16963584/f7123886-b660-4e2d-aadf-cac0e548ffdb)

### [#](#_3、配置环境变量) 3、配置环境变量

安装后需要配置对应的环境变量

- 1）配置环境前，可打开终端输入可执行 `echo $SHELL` 判断本地 shell 版本，从而选择对应的环境变量方式，如下面的 bash 或者 zsh
- 2）执行 `open -e ~/.bash_profile`，或者 `open -e ~/.zshrc` 打开对应的配置文件（如果执行的时候发现文件不存在，可以通过 `touch ~/.bash_profile` 或 `touch ~/.zshrc` 新建打开）
- 3）添加 `ANDROID_HOME` 等相关环境变量，例如下方内容（如何查看 Android SDK 的安装路径（即 ANDROID\_HOME 的路径），可查看[环境搭建常见问题](./mac.md#%E5%9B%9B%E3%80%81%E7%8E%AF%E5%A2%83%E6%90%AD%E5%BB%BA%E5%B8%B8%E8%A7%81%E9%97%AE%E9%A2%98)）

```
export ANDROID_HOME=$HOME/Library/Android/sdk
export PATH=$PATH:$ANDROID_HOME/emulator
export PATH=$PATH:$ANDROID_HOME/tools
export PATH=$PATH:$ANDROID_HOME/tools/bin
export PATH=$PATH:$ANDROID_HOME/platform-tools
```

- 4）执行命令 `source ~/.bash_profile` 或者 `source ~/.zshrc` 使配置生效
- 5）验证是否配置成功，打开终端，输入 `echo $ANDROID_HOME`，查看效果

> 注意：修复环境变量需要重启微信开发者工具项目

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202212212128935.png)

Incorrect translation.