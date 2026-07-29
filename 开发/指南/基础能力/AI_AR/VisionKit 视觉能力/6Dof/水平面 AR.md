# [#](#_6DoF-平面-AR能力) 6DoF-平面 AR能力

## [#](#方法定义) 方法定义

6DoF-平面AR能力，提供基础AR功能，提供旋转和平移6自由度的定位功能。

包括 `V1` 和 `V2` 两种适用不同场景的算法，两种平面AR能力各有优劣，用户根据适用场景及产品需求，自行判断调用接口类型，具体介绍如下：

1. V1平面接口，适用于用户在平面场景下，例如桌面，地面，泛平面场景，放置虚拟物体，不提供真实世界距离。用户放置物体时，手机相机倾斜向下对着目标平面点击即可，具有广泛的机型支持。
2. V2平面接口，提供真实物理距离的ar定位功能，提供平面识别功能，用户在平面范围点击放置虚拟物体的功能，具有有限的支持机型。

### [#](#能力扩展) 能力扩展

在 `V2` 平面基础上，可以通过配置开启多种扩展能力，比如：

1. marker 识别能力，即平面空间下多个不同识别目标的识别。
2. 虚实遮挡的能力，即虚拟物体和真实世界的交互遮挡能力。

更多使用效果与开关配置细节，可以参考 [平面AR能力扩展](plane-options)。

### [#](#如何开启-V1-或-V2) 如何开启 V1 或 V2

初始化时，通过 VKSession 配置 version 确定。

```
const session = wx.createVKSession({
  track: {
    plane: {
        mode: 1
    },
  },
  version: 'v2' // 在满足设备条件时开启，否则会使用 v1
  // version: "v1" 强制开启v1
})
```

有关完整的VKSession配置，详见 [VKSession配置参考](https://developers.weixin.qq.com/miniprogram/dev/api/ai/visionkit/wx.createVKSession.html)。

### [#](#V1-与-V2-对比) V1 与 V2 对比

| 接口类型 | 平面检测 | 真实距离 | 初始化速度 | 机型覆盖率 | 功耗 | 精度 | 多物体放置效果 | 多种扩展能力 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| V1 | 无 | 无 | 快 | 高 | 低 | 中 | 良 | 无 |
| V2 | 有 | 有 | 慢 | 低 | 高 | 高 | 优 | 有 |

## [#](#应用场景示例) 应用场景示例

V1平面demo

![planev1_gif](https://res8.wxqcloud.qq.com.cn/wxdoc/3d036aeb-260c-4b0b-8866-873e0c88ecb5.gif)

V2平面demo

![planev2_gif](https://res.wx.qq.com/wxdoc/dist/assets/img/planev2.af95186a.gif)

V2平面+虚实遮挡demo

![planev2_deepocc_gif](https://res8.wxqcloud.qq.com.cn/wxdoc/d619d288-d0f9-439a-be27-03a718a25dae.gif)

## [#](#程序示例) 程序示例

1. 可以在 [V1平面](https://github.com/wechat-miniprogram/miniprogram-demo/tree/master/miniprogram/packageAPI/pages/ar/plane-ar) 页面查看示例代码。
2. 可以在 [V2平面](https://github.com/wechat-miniprogram/miniprogram-demo/tree/master/miniprogram/packageAPI/pages/ar/plane-ar-v2) 页面查看示例代码。
3. 可以在 [V2平面+虚实遮挡](https://github.com/wechat-miniprogram/miniprogram-demo/tree/master/miniprogram/packageAPI/pages/ar/plane-ar-v2-depth) 页面查看示例代码，在小程序示例中的**接口-VisionKit视觉能力-水平面AR-v2-虚实遮挡**中体验。

## [#](#附录) 附录

### [#](#V1平面接口系统要求) V1平面接口系统要求

1）IOS机型要求: iphone 6s及以上机型

2）Android机型要求：Android 7.0, Android SDK 24及以上

### [#](#V2平面AR接口支持列表) V2平面AR接口支持列表

1. IOS机型要求: iphone 7及以上机型
2. Android机型支持会逐步增加，如测试机型效果有误可论坛反馈，目前支持机型包括:

| 手机厂商 | 手机型号 |
| --- | --- |
| Hi | Hi nova 9 |
| OPPO | OPPO A32 |
| OPPO | OPPO A53 |
| OPPO | OPPO A57 |
| OPPO | OPPO A72 5G |
| OPPO | OPPO A92s |
| OPPO | OPPO A93s |
| OPPO | OPPO A93 |
| OPPO | OPPO A95 |
| OPPO | OPPO Ace2 |
| OPPO | OPPO Find X2 |
| OPPO | OPPO Find X3 Pro |
| OPPO | OPPO Find X3 |
| OPPO | OPPO Find X5 Pro |
| OPPO | OPPO Find X5 |
| OPPO | OPPO K10 Pro |
| OPPO | OPPO K10 Pro |
| OPPO | OPPO K10x |
| OPPO | OPPO K10 |
| OPPO | OPPO K3 |
| OPPO | OPPO K5 |
| OPPO | OPPO K9 Pro |
| OPPO | OPPO Pad |
| OPPO | OPPO R15 |
| OPPO | OPPO R17 |
| OPPO | OPPO Reno 10倍变焦版 |
| OPPO | OPPO Reno Ace |
| OPPO | OPPO Reno Z |
| OPPO | OPPO Reno2 |
| OPPO | OPPO Reno3 Pro 5G |
| OPPO | OPPO Reno3 元气版 |
| OPPO | OPPO Reno3 |
| OPPO | OPPO Reno4 |
| OPPO | OPPO Reno5 K |
| OPPO | OPPO Reno5 Pro+ |
| OPPO | OPPO Reno5 |
| OPPO | OPPO Reno6 Pro+ |
| OPPO | OPPO Reno6 Pro |
| OPPO | OPPO Reno6 |
| OPPO | OPPO Reno7 Pro |
| OPPO | OPPO Reno7 SE |
| OPPO | OPPO Reno7 |
| OPPO | OPPO Reno8 Pro+ |
| OPPO | OPPO Reno8 Pro |
| OPPO | OPPO Reno8 |
| OPPO | OPPO Reno9 Pro+ |
| OPPO | OPPO Reno |
| OPPO | Oppo A11 |
| OPPO | Oppo K7x |
| OPPO | Oppo Reno2 Z |
| OPPO | Oppo Reno5 Pro |
| ROG | ROG游戏手机2精英版 |
| Realme | Realme C11 (2021) |
| Realme | Realme GT Neo 5 |
| Realme | Realme X7 Pro |
| Samsung | Samsung Galaxy Note10+(855) |
| Samsung | Samsung Galaxy S10+ |
| Samsung | Samsung Galaxy S10 |
| VIVO | VIVO IQOO |
| VIVO | VIVO S7 |
| VIVO | Vivo X90 |
| VIVO | Vivo Z5x |
| VIVO | Vivo iQOO 11 Pro |
| VIVO | Vivo iQOO Neo7 Racing |
| VIVO | vivo IQOO NEO6 SE |
| VIVO | vivo NEX 3 |
| VIVO | vivo NEX |
| VIVO | vivo Pad |
| VIVO | vivo S10 |
| VIVO | vivo S12 Pro |
| VIVO | vivo S12 |
| VIVO | vivo S15 Pro |
| VIVO | vivo S15e |
| VIVO | vivo S15 |
| VIVO | vivo S16e |
| VIVO | vivo S16 |
| VIVO | vivo S5 |
| VIVO | vivo S6 |
| VIVO | vivo S9e |
| VIVO | vivo S9 |
| VIVO | vivo T1 |
| VIVO | vivo X27 |
| VIVO | vivo X30 Pro |
| VIVO | vivo X30 |
| VIVO | vivo X50 Pro |
| VIVO | vivo X50 |
| VIVO | vivo X60 Pro |
| VIVO | vivo X60 |
| VIVO | vivo X70 Pro |
| VIVO | vivo X70 |
| VIVO | vivo X80 |
| VIVO | vivo Y52s |
| VIVO | vivo Y53s |
| VIVO | vivo Y70s |
| VIVO | vivo Y73s |
| VIVO | vivo Z5 |
| VIVO | vivo iQOO 3 5G |
| VIVO | vivo iQOO 5 5G |
| VIVO | vivo iQOO Neo |
| VIVO | vivo iQOO Pro |
| iQOO | iQOO 10 Pro |
| iQOO | iQOO 10 |
| iQOO | iQOO 11 |
| iQOO | iQOO 7 |
| iQOO | iQOO 8 Pro |
| iQOO | iQOO 8 |
| iQOO | iQOO 9 Pro |
| iQOO | iQOO 9 |
| iQOO | iQOO Neo 855 |
| iQOO | iQOO Neo3 |
| iQOO | iQOO Neo5 SE |
| iQOO | iQOO Neo5S |
| iQOO | iQOO Neo5 |
| iQOO | iQOO Neo6 |
| iQOO | iQOO Neo7 SE |
| iQOO | iQOO Z1x |
| iQOO | iQOO Z1 |
| iQOO | iQOO Z3 |
| iQOO | iQOO Z5x |
| iQOO | iQOO Z5 |
| iQOO | iQOO Z6 |
| realme | realme GT Neo2T |
| realme | realme GT Neo2 |
| realme | realme GT Neo3 |
| realme | realme GT Neo |
| realme | realme GT |
| realme | realme Q3 Pro |
| realme | realme Q3 |
| realme | realme V15 |
| realme | realme X2 Pro |
| 一加 | OnePlus 11 |
| 一加 | OnePlus Ace 2V |
| 一加 | OnePlus Ace 2 |
| 一加 | 一加10 Pro |
| 一加 | 一加7 Pro |
| 一加 | 一加7T Pro |
| 一加 | 一加7T |
| 一加 | 一加7 |
| 一加 | 一加8 Pro |
| 一加 | 一加8T |
| 一加 | 一加8 |
| 一加 | 一加9 Pro |
| 一加 | 一加9RT |
| 一加 | 一加9R |
| 一加 | 一加9 |
| 一加 | 一加Ace Pro |
| 一加 | 一加Ace 竞速版 |
| 一加 | 一加Ace |
| 努比亚 | 努比亚红魔3 |
| 努比亚 | 努比亚红魔6 |
| 华为 | HUAWEI Mate50 Pro |
| 华为 | HUAWEI Mate50 |
| 华为 | HUAWEI MatePad Pro 11英寸 |
| 华为 | HUAWEI nova 10 SE |
| 华为 | Huawei Mate 30 5G |
| 华为 | Huawei Mate 30 RS Porsche Design |
| 华为 | Huawei Mate 30E Pro 5G |
| 华为 | Huawei Mate 40 Pro+ |
| 华为 | Huawei nova 6 5G |
| 华为 | 华为Mate 20 Pro |
| 华为 | 华为Mate 9 |
| 华为 | 华为Mate20X |
| 华为 | 华为Mate20 |
| 华为 | 华为Mate30 Pro |
| 华为 | 华为Mate30 |
| 华为 | 华为Mate40 Pro |
| 华为 | 华为Mate40E |
| 华为 | 华为Mate40 |
| 华为 | 华为MatePad 10.8 |
| 华为 | 华为MatePad 11 |
| 华为 | 华为MatePad Pro |
| 华为 | 华为MatePad Pro |
| 华为 | 华为P20 |
| 华为 | 华为P30 Pro |
| 华为 | 华为P30 |
| 华为 | 华为P40 Pro+ |
| 华为 | 华为P40 Pro |
| 华为 | 华为P40 |
| 华为 | 华为P50 Pro |
| 华为 | 华为P50 Pro |
| 华为 | 华为nova 10 Pro |
| 华为 | 华为nova 10 |
| 华为 | 华为nova 4e |
| 华为 | 华为nova 4 |
| 华为 | 华为nova 5 Pro |
| 华为 | 华为nova 5i Pro |
| 华为 | 华为nova 6 |
| 华为 | 华为nova 7 5G |
| 华为 | 华为nova 7 Pro 5G |
| 华为 | 华为nova 7 Pro |
| 华为 | 华为nova 7 |
| 华为 | 华为nova 8 Pro |
| 华为 | 华为nova 8 |
| 华为 | 华为nova 9 Pro |
| 华为 | 华为nova 9 |
| 华为 | 华为平板 M6 8.4英寸 |
| 华为 | 华为畅享10 Plus |
| 坚果 | 坚果Pro 3 |
| 小米 | Redmi K20 Pro |
| 小米 | Redmi K30 5G |
| 小米 | Redmi K30S |
| 小米 | Redmi K40 Pro |
| 小米 | Redmi K40S |
| 小米 | Redmi K40 |
| 小米 | Redmi K50 Pro |
| 小米 | Redmi K50 Ultra |
| 小米 | Redmi K60 Pro |
| 小米 | Redmi K60 |
| 小米 | Redmi Note 10 Pro |
| 小米 | Redmi Note 11T Pro+ |
| 小米 | Redmi Note 11 |
| 小米 | Redmi Note 12 Pro |
| 小米 | Redmi Note 9 5G |
| 小米 | Xiaomi 13 Pro |
| 小米 | Xiaomi 13 |
| 小米 | Xiaomi Mi 10 Ultra |
| 小米 | Xiaomi Redmi K30 Pro |
| 小米 | Xiaomi Redmi K30 |
| 小米 | Xiaomi Redmi Note 9 Pro 5G |
| 小米 | 小米 9 |
| 小米 | 小米10 Pro |
| 小米 | 小米10S |
| 小米 | 小米10 |
| 小米 | 小米10青春版 |
| 小米 | 小米11 Pro |
| 小米 | 小米11 Ultra |
| 小米 | 小米11 |
| 小米 | 小米11青春版 |
| 小米 | 小米12 Pro |
| 小米 | 小米12S Pro |
| 小米 | 小米12S Ultra |
| 小米 | 小米12X |
| 小米 | 小米12 |
| 小米 | 小米8 |
| 小米 | 小米Civi 1S |
| 小米 | 小米MIX4 |
| 小米 | 小米平板5 pro |
| 小米 | 小米平板5 |
| 小米 | 红米K30 Ultra |
| 小米 | 红米Note 11T Pro |
| 联想 | 联想小新 Pad |
| 联想 | 联想拯救者 Y700 |
| 联想 | 联想拯救者电竞手机Pro |
| 荣耀 | Honor80 Pro |
| 荣耀 | Honor80 |
| 荣耀 | 荣耀20S |
| 荣耀 | 荣耀20 |
| 荣耀 | 荣耀30 Pro+ |
| 荣耀 | 荣耀30S |
| 荣耀 | 荣耀30 |
| 荣耀 | 荣耀50 Pro |
| 荣耀 | 荣耀50 |
| 荣耀 | 荣耀60 Pro |
| 荣耀 | 荣耀60 |
| 荣耀 | 荣耀70 Pro |
| 荣耀 | 荣耀70 |
| 荣耀 | 荣耀9X |
| 荣耀 | 荣耀Magic3 |
| 荣耀 | 荣耀Magic4 Pro |
| 荣耀 | 荣耀Magic4 |
| 荣耀 | 荣耀V20 |
| 荣耀 | 荣耀V30 PRO |
| 荣耀 | 荣耀V30 |
| 荣耀 | 荣耀V40 |
| 荣耀 | 荣耀X10 |
| 荣耀 | 荣耀X30 |
| 荣耀 | 荣耀X40 GT |
| 荣耀 | 荣耀X40 |
| 荣耀 | 荣耀平板V6 |
| 荣耀 | 荣耀平板V7 Pro |
| 黑鲨 | 黑鲨5 RS |
| 黑鲨 | 黑鲨游戏手机2 Pro |
| 黑鲨 | 黑鲨游戏手机2 |
| 黑鲨 | 黑鲨游戏手机3 |
| 黑鲨 | 黑鲨游戏手机4 |

Incorrect translation.