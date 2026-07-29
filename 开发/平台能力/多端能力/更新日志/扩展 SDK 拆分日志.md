# [#](#扩展-SDK-拆分日志) 扩展 SDK 拆分日志

- 为了减少 SDK 的大小以及减少个人用户信息的收集，将对如下扩展 SDK 进一步拆分，开发者可以按需勾选更细颗粒度的 SDK。

## [#](#iOS-Media-SDK) iOS Media SDK

- 在 iOS SDK >= 1.3.11 以及 开发者工具版本 >= 1.06.2405102(nightly 版)，iOS Media SDK 已经被拆分为：Audio SDK、Video SDK、Image SDK、Camera SDK
- 注意，必须勾选对应所需的 SDK 方可正常构建，以及 Api 才可以正常调用

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F%E4%BC%81%E4%B8%9A%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_815263b8-b8f3-48f3-9ece-66bdd43c4eb1.png)

- 然后需将`project.miniapp.json`切换到 json 模式，然后手动删除 WeAppMedia

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202405151820543.png)

Incorrect translation.