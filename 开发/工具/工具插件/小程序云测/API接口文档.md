## [#](#第三方接口介绍) 第三方接口介绍

为了方便用户和已有的Devops流程（如Jenkins等）打通，云测插件提供第三方接口，支持直接用https接口调用的方式提测。

**注意：第三方接口有限流，每个项目，每小时1000次**

## [#](#接口示例代码-Python3) 接口示例代码(Python3)

[点击下载](https://res.wx.qq.com/op_res/r_ZV6lkE3usfeftcuqstBjmpmiP_ikXeldrUlnX_N1OBxoi3KGg3ZFya9mMzTPKZgS_8zl91ti8sx3G2nU-qMA)

## [#](#基本参数) 基本参数

### [#](#_1-用户Token（token）) 1. 用户Token（token）

用于区分不同用户。在页面右上角头像下拉菜单中的 “我的信息”，跳转至我的信息页面，查看“我的Token”。

![](https://res8.wxqcloud.qq.com.cn/wxdoc/a2ee86d7-bbce-487d-a30e-279511ca7b05.gif)

### [#](#_2-项目英文ID（group-en-id）) 2. 项目英文ID（group\_en\_id）

用于定位具体项目。在 项目管理/产品管理 页面获取，

![](https://res8.wxqcloud.qq.com.cn/wxdoc/f4eed2ee-5955-4232-a79f-99f5d87aee96.png)

## [#](#请求返回状态码) 请求返回状态码

成功：rtn返回0

失败：rtn返回-1

Incorrect translation.