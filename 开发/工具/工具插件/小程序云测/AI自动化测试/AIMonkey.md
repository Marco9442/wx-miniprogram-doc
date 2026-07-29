# [#](#AIMonkey) AIMonkey

AIMonkey主要依托大模型能力，重构原来的智能化Monkey测试。对比原来的智能化Monkey，主要优势是：

- **可以回放Monkey过程**：执行完成后会自动生成本次操作的Minium代码，你也可以把它上传到云测作为Minium用例再次执行，回放本次Monkey过程
- **鸿蒙操作系统，只支持AIMonkey模式**。对于鸿蒙操作系统，即使页面选择智能化Monkey，云测会自动切换到AIMonkey模式
- 利用大模型能力驱动测试，更加贴近人类感知

请注意：AIMonkey是纯大模型驱动，不支持原来智能化Monkey的拓展能力，如不支持配置前置步骤

# [#](#快速开始) 快速开始

### [#](#_1-在提交任务时，选择AIMonkey测试计划) 1. 在提交任务时，选择AIMonkey测试计划

在“测试任务”页面，新建任务时，在Monkey测试类型的测试计划中，选择“AIMonkey”

![](https://res8.wxqcloud.qq.com.cn/wxdoc/ee0cfe28-66f3-4076-88d7-2acb6cc16c54.png)

### [#](#_2-查看报告) 2. 查看报告

AIMonkey的报告和原来智能化Monkey基本一致，只是在用例结果页面，会多出一个“自动生成用例”的Tab

你可以下载代码，然后自行上传为Minium用例，在云测使用[Minium任务](minium)回放本次执行过程

![](https://res8.wxqcloud.qq.com.cn/wxdoc/f3181ae3-e8a6-451f-84ad-2af79df56930.png)

# [#](#需要帮助) 需要帮助

如果你任何建议或需求，欢迎前往 [需要帮助](help) 页面，扫码加入云测官方企微群，联系群主反馈。

Incorrect translation.