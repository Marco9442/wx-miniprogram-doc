# [#](#iOS-隐私信息访问许可描述) iOS 隐私信息访问许可描述

- 为方便开发者配置使用权限的用途描述，开发者可在 `project.miniapp.json` 中配置，涉及的配置如下：
- 开发者需在输入框内填写正确的权限用途，否则可能用户会拒绝授权
- 以及部分 JSAPI 需要配置对应的权限许可描述才可以成功调用，具体可查看 JSAPI 对应文档的说明

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202405281547733.png)

- 在出现系统授权弹窗的呈现的输入框的内容的交互参考如下：

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202405281551333.png)

- 此外，为了帮助开发者避免因忘记填写许可描述而导致 JSAPI 无法调用，开发者工具支持开启「使用默认隐私信息访问许可描述」（开发者工具版本 >= 1.06.2406242）

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202406261128157.png)

- 但如 App 需要正式上架，开发者依旧需要如实填写，不可使用工具内置的默认描述；即不要勾选「使用默认隐私信息访问许可描述」，并且重新如实填写许可描述

Incorrect translation.