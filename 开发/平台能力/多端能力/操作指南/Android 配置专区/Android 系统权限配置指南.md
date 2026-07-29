# [#](#Android-系统权限配置指南) Android 系统权限配置指南

根据工业和信息化部关于开展 App 侵害用户权益专项整治要求，应用的隐私政策中需详细描述使用权限的用途（每个开发者的 App 使用如下权限的用途不一样，具体内容由开发者按照实际的用途填写）

为方便开发者配置使用权限的用途描述，开发者可在 `project.miniapp.json` 中配置，涉及的配置如下：

- 开发者需在输入框内填写正确的权限用途，建议的表述为「申请 XXX 权限用于 XXXX」，即需要将权限的名称和用途都描述清楚，否则用户可能会拒绝、应用市场上架审核也可能会驳回。

![](https://res.wx.qq.com/op_res/iWKxAkX6DmXvKx_Z9gVonNaLHGbAZslaoejY-LlFcmLOt8VWnPuyHdKy2ePlRK62B2IC7dztioYMEcOT-Jx-5Q)

- 示例：如在 `android.permission.CAMERA` 配置使用用途之后，在调用到保存相册等接口时，在出现系统授权弹窗的同时，会在顶部出现配置的请求授权提示，交互参考如下：

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202303291610768.png)

- 如果应用上架审核时检测到某些权限，但是实际上你并未用到，而应用市场则以你未声明相关用途而驳回时，则可将 project.miniapp.json 切换到 json 格式，然后通过 `uselessPermissions` 参数移除相关权限项，如：

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F%E4%BC%81%E4%B8%9A%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_4e4cb2e1-cb64-4806-ad78-d9c1f0e3d15d.png)

- 如果需要新增某些 Android 的权限，但是 `project.miniapp.json` 的可视化配置中并未支持，开发者可将 `project.miniapp.json` 切换到 json 格式，然后通过 `permissions` 参数新增相关权限项，android.permission. 前缀的都能直接加。如：

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202502211140422.png)

Incorrect translation.