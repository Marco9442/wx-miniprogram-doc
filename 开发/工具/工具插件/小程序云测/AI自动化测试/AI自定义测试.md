工具插件/小程序云测/AI自动化测试/AI自定义测试/
## [\#](https://developers.weixin.qq.com/miniprogram/dev/devtools/minitest/ai\_plan.html\#AI-%E8%87%AA%E5%AE%9A%E4%B9%89%E6%B5%8B%E8%AF%95) AI 自定义测试
AI 自定义测试，是利用大模型能力，可以让用户使用自然语言描述用例，底层使用Minium驱动用例自动执行。它的主要优势如下：
- 用户无需写代码，用自然语言描述执行步骤即可， \*\*使用门槛较低\*\*
- 任务执行成功后，会 \*\*自动生成\*\* 本次任务执行过程的 \*\*Minium脚本\*\*。用户可以将该脚本作为用例上传为 [Minium](https://developers.weixin.qq.com/miniprogram/dev/devtools/minitest/minium) 用例，后续可以快速执行本用例
以"小程序示例"（微信搜索小程序示例即可找到这个小程序）为例，假设需要对多线程进行测试，步骤描述为：
```text
1. 点击接口
2. 向下滑动找到"多线程"，并点击多线程
3. 点击利用 Worker 线程计算 按钮
4. 页面能正常首先是结果和耗时，且都不为空
```
云测运行报告可以参考 [示例报告](https://minitest.weixin.qq.com/cloudtest/share/report\_details?share\_token=207f455e3056b14e80746d8000646bed&level=device&app\_id=19&device\_id=6981&tab=ai-execute-steps)
使用前请仔细阅读使用须知：
1. 目前 AI 自定义测试处于 \*\*内测中\*\*。如遇到跑测失败，可以先查看最下方的常见问题，如仍有问题，请在 [帮助页面](https://developers.weixin.qq.com/miniprogram/dev/devtools/minitest/help)，扫码加入云测官方企微群，联系群主反馈
2. 目前 AI 操作目前支持 \*\*点击、简单输入、滑动，function\\_call，大模型断言\*\* 等能力。如有其他需求，请联系群主评估
## [\#](https://developers.weixin.qq.com/miniprogram/dev/devtools/minitest/ai\_plan.html\#%E5%BF%AB%E9%80%9F%E5%BC%80%E5%A7%8B) 快速开始
你可以按照以下步骤开始 AI 自定义测试任务
### [\#](https://developers.weixin.qq.com/miniprogram/dev/devtools/minitest/ai\_plan.html\#%E4%B8%80%E3%80%81-%E6%96%B0%E5%BB%BA-AI-%E6%B5%8B%E8%AF%95%E7%94%A8%E4%BE%8B) 一、 新建 AI 测试用例
在"AI 用例"页面，新建测试用例，在弹出的窗口中，填写用例名称、优先级和用例描述。
其中， \*\*用例描述\*\* 即本次 AI 探索过程的自然语言描述，尽量准确详细描述用例执行的过程。
![](https://res8.wxqcloud.qq.com.cn/wxdoc/dead8c69-1cf1-46dc-98ec-e84b14a4cc6b.png)
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/devtools/minitest/ai\_plan.html\#%E5%A1%AB%E5%86%99%E7%94%A8%E4%BE%8B%E6%8F%8F%E8%BF%B0-Tips%EF%BC%9A) 填写用例描述 Tips：
填写用例描述时，可以从人类视觉的角度去描述（会把当前屏幕截图给到大模型）， \*\*你可以假想当前已经打开了你的小程序，你只需要描述后续步骤即可\*\*。
以航空小程序为例，参考描述如下：
```text
1. 在首页中，点击出发地下面的"成都"，进入更换出发地页面。
2. 在更换出发地页面中，在导航栏搜索"XIC"，在搜索结果中，选择第一个"西昌"，并返回购票页面
3. 在购票页面中，点击目的地下面的"北京"，进入更换目的地页面
4. 在更换目的地页面中，在导航栏搜索"NKG"，在搜索结果中，选择第一个"南京"，并返回购票页面
5. 在购票页面中，点击"搜索机票"，进入选择机票页面。途中如果遇到公告弹窗，要关闭这个弹窗
6. 能成功进入选择机票页面，任务成功。如果无法进入选择机票页面，任务失败
```
此外以下是一些有用的小 Tips：
- 在描述滑动时，需要描述清楚是 \*\*上下\*\* 滑动还是 \*\*左右\*\* 滑动，这样大模型才好做成正确的判断
- 如果需要滑动到页面底部，可以直接描述说滑动到页面底部，加快执行流程
- 如果需要在滑动中找到某个文字，可以描述向下滑动，找到"xxx"。注意此时页面必须存在"xxx"文字，因为是执行中，云测会用 OCR 的方式去匹配文字。
#### [\#](https://developers.weixin.qq.com/miniprogram/dev/devtools/minitest/ai\_plan.html\#%E7%89%B9%E6%AE%8A%E6%93%8D%E4%BD%9C) 特殊操作
此外，AI 自定义测支持以下特殊操作：
##### [\#](https://developers.weixin.qq.com/miniprogram/dev/devtools/minitest/ai\_plan.html\#\_1-minium-func-call) 1\. minium\\_func\\_call
minium\\_func\\_call 支持用户在大模型描述中，调用自己的函数，类似大模型function\\_call能力。
使用function\\_call能力的特别须知：
- \*\*调用的函数，必需要上传到云测\*\*
- 函数的第一个参数，\*\*需要传入mini\*\*，详情可以参考下方示例。mini会把minitest.MiniTest实例传入到函数，方便用户使用minium的能力。注意即使函数不需要使用mini的能力，也需要将第一个参数设置为mini
使用示例如下：
用户已经将test\\_config.py和config/test\\_config.py已经上传到云测的Minium用例中。这两文件内容相同，这里只是为了演示在不同目录下，要如何调用。
test\\_config.py内容也很简单，有一个示例函数和示例类（再次提醒第一个参数要传入mini）。各种不同情况的调用方式描述如下：
- 调用 \*\*test\\_config.py\*\* 中的 \*\*get\\_config\*\* 函数：`从minium\_func\_call("test\_config.get\_config")中读取 [出发地] 和 [目的地] 信息`
- 调用 \*\*test\\_config.py\*\* 中的 \*\*TestConfig\*\* 类中的 \*\*get\\_config\*\* 函数：`从minium\_func\_call("test\_config.TestConfig.get\_config")中读取 [出发地] 和 [目的地] 信息`
- 调用 \*\*config/test\\_config.py\*\* 中的 \*\*get\\_config\*\* 函数：`从minium\_func\_call("config.test\_config.get\_config")中读取 [出发地] 和 [目的地] 信息`
- 调用 \*\*config/test\\_config.py\*\* 中的 \*\*TestConfig\*\* 类中的get\\_config函数：`从minium\_func\_call("config.test\_config.TestConfig.get\_config")中读取 [出发地] 和 [目的地] 信息`
![](https://res8.wxqcloud.qq.com.cn/wxdoc/b6ad3f02-7fdd-44df-a596-9e82e04942f7.png)
如果函数需要传入自定义参数，例如上述get\\_config函数增加了2个参数（start\\_date和end\\_date），参考示例：
```python
def get\_config(mini, start\_date, end\_date):
# 注意：这里一定要用user\_logger，这样打印的日志才会在云测报告中展示！！
mini.user\_logger.info(f'params is {start\_date} {end\_date}')
return {
'出发地': '深圳',
'目的地': '广州'
}
```
在调用时，第一个参数mini不需要写，其他参数需要指定。目前自定义参数格式尽量简单，最好是 \*\*数值或者字符串\*\*，复杂格式（如数组或者字典）会有问题。例如上述函数描述可以这么传入：
```text
1. 从minium\_func\_call("test\_config.get\_config", "2026-01-01", "2026-03-01")中读取 [出发地] 和 [目的地] 信息
```
> \*\*特别注意：\*\*
>
> 1\. 调用的函数名、文件名、文件路径， \*\*请尽量使用英文\*\*，不要带有特殊符号，避免import失败。自己的函数参数
>
> 2\. 如果希望在自定义函数中输出日志，需要用`mini.user\_logger.info("xxx")` （info可以换成warning等其他logger日志等级，mini是函数参数中传入的minium实例名称），这样打印的日志才能在云测查看。在skills中的用户函数也是如此，总之如果希望看到函数调用的日志，需要使用user\\_logger！！！
##### [\#](https://developers.weixin.qq.com/miniprogram/dev/devtools/minitest/ai\_plan.html\#\_2-skills) 2\. skills
minium\\_func\\_call能力有个明显的局限性：需要用户在描述中指定好使用的函数和参数
在部分场景中，用户希望自己提供一系列的"技能"，让大模型在执行过程中，根据当前的实际场景，让大模型自己判断是否要选择执行某个技能，而不是描述中指定好，这样可以更加灵活的完成 AI 任务。
为了满足这个需求，小程序云测特别推出了skill能力，用户只需要描述清楚skill函数作用，相关参数，即可快速注册技能。大模型在后台会自己决策调用时机和参数。
详细使用规则，可以参考文档： [skill能力详细说明](https://developers.weixin.qq.com/community/develop/article/doc/0006ee97e4c8d8da1ac4545b06b013)
##### [\#](https://developers.weixin.qq.com/miniprogram/dev/devtools/minitest/ai\_plan.html\#\_3-llm-assert) 3\. llm\\_assert
在描述中，如果要用assert能力，可以使用llm\\_assert。注意如果llm\\_assert失败， \*\*将终止当前Case测试\*\*。
例如，用户可以描述如下：
```text
1、从minium\_func\_call("test\_config.get\_config")中读取 [出发地] 和 [目的地] 信息
2. 将出发地换成第一步中读取的 [出发地]
3. 将目的地换成[目的地]
4. llm\_assert("出发地成功切换为[出发地]，目的地切换为[目的地]")
```
在上述的描述中，大模型可以自己识别结果的\[出发地\] 和 \[目的地\] ，换成北京和上海，生成的llm\\_assert代码：
```python
self.op\_llm\_assert('''出发地成功切换为北京，目的地切换为上海''')
```
### [\#](https://developers.weixin.qq.com/miniprogram/dev/devtools/minitest/ai\_plan.html\#%E4%BA%8C%E3%80%81-%E6%96%B0%E5%BB%BA-AI-%E6%B5%8B%E8%AF%95%E8%AE%A1%E5%88%92) 二、 新建 AI 测试计划
AI 测试用例新建完成后，点击"测试计划"页面， \*\*新建 AI 测试计划\*\*。填写计划名称，勾选需要执行的 AI 用例。
和Minium类似，云测会 \*\*按照勾选的顺序执行用例\*\*。注意 AI 测试用例采用的是 \*\*DDT\*\* 的模式依次执行。
![](https://res8.wxqcloud.qq.com.cn/wxdoc/0fc105d6-f5a6-4856-95d4-345b61937762.png)
### [\#](https://developers.weixin.qq.com/miniprogram/dev/devtools/minitest/ai\_plan.html\#%E4%B8%89%E3%80%81-%E6%8F%90%E4%BA%A4%E6%B5%8B%E8%AF%95%E4%BB%BB%E5%8A%A1) 三、 提交测试任务
> AI 自定义测试任务是用Minium驱动执行的，所以它本质还是一个 [Minium](https://developers.weixin.qq.com/miniprogram/dev/devtools/minitest/minium) 类型的任务
AI 自定义测试计划创建完成后，在"测试任务"页面，点击"新建任务"按钮。
在弹出窗口中，选择`Minium`测试类型，在测试计划中，选择刚才创建的 AI 测试计划。
注意，所有 AI 测试计划的右侧都有 \*\*AI 任务的 Tag 标识\*\*
![](https://res8.wxqcloud.qq.com.cn/wxdoc/7f32ac4b-a649-4e42-a2a2-e92f5a937fb2.png)
### [\#](https://developers.weixin.qq.com/miniprogram/dev/devtools/minitest/ai\_plan.html\#%E5%9B%9B%E3%80%81-%E6%9F%A5%E7%9C%8B%E6%B5%8B%E8%AF%95%E6%8A%A5%E5%91%8A) 四、 查看测试报告
任务结束后，可以在测试报告页面查看执行结果。例如上述描述执行结果如下：
![](https://res8.wxqcloud.qq.com.cn/wxdoc/a8aba6fc-1f4a-44ee-b794-700187c7651a.gif)
测试结果一般分为 \*\*测试成功\*\* 和 \*\*测试失败\*\* 。
- 测试成功，是 AI 按照描述，执行完成 。特别注意：这里是 \*\*AI 自我感觉执行成功\*\*，用户可以根据测试报告截图以及生成的Minium代码自行判断
- 测试失败 一般有几种情况：
- \*\*根据任务描述返回失败\*\*：例如任务描述要求 "如果找不到'广州'，直接返回失败，结束测试"，在探索过程中，未找到'广州'，此时返回失败，并结束测试，在生成代码中，会带有`asesert Fasle, error\_msg`的代码
- \*\*AI 探索失败\*\*：AI 按照任务描述，连续多次都无法成功，故返回失败。此时在用例执行结果的错误日志一般会有提示"AI 探索连续失败了x次，结束测试"
- \*\*AI 探索超时\*\*：AI 还在探索中，但是任务规定的时间已经到了，结束测试，并返回失败
测试成功的代码，可以直接下载，作为Minium用例上传到云测，直接跑测 [Minium任务](https://developers.weixin.qq.com/miniprogram/dev/devtools/minitest/minium)
![](https://res8.wxqcloud.qq.com.cn/wxdoc/d5100b96-9c4a-43b8-ba72-d1e93b699554.png)
## [\#](https://developers.weixin.qq.com/miniprogram/dev/devtools/minitest/ai\_plan.html\#%E5%B8%B8%E8%A7%81%E9%97%AE%E9%A2%98) 常见问题
### [\#](https://developers.weixin.qq.com/miniprogram/dev/devtools/minitest/ai\_plan.html\#\_1-%E4%B8%BA%E4%BB%80%E4%B9%88-AI-%E6%8E%A2%E7%B4%A2%E8%80%97%E6%97%B6%E8%BE%83%E9%95%BF%EF%BC%8C%E4%B8%8B%E8%BD%BD%E7%9A%84-Minium-%E7%9A%84%E7%94%A8%E4%BE%8B%E5%BE%88%E5%BF%AB%E5%B0%B1%E6%89%A7%E8%A1%8C%E5%AE%8C%E6%88%90%E4%BA%86%EF%BC%9F) 1\. 为什么 AI 探索耗时较长，下载的 Minium 的用例很快就执行完成了？
AI 任务过程比较长，需要多次和大模型交互，每一步的耗时都会较长，而生成好的 Minium 的用例只需要执行就可以，无需和大模型再次交互，所以速度会快很多
### [\#](https://developers.weixin.qq.com/miniprogram/dev/devtools/minitest/ai\_plan.html\#\_2-AI-%E4%BB%BB%E5%8A%A1%E7%94%9F%E6%88%90%E4%B8%8D%E5%8F%8A%E9%A2%84%E6%9C%9F%E5%BA%94%E8%AF%A5%E6%80%8E%E4%B9%88%E5%8A%9E%EF%BC%9F) 2\. AI 任务生成不及预期应该怎么办？
建议可以先观察下测试报告，看看 AI 在哪里出错的，然后对应优化任务描述。
如果仍有问题，可以加入云测官方企微群，联系群主反馈
## [\#](https://developers.weixin.qq.com/miniprogram/dev/devtools/minitest/ai\_plan.html\#%E9%9C%80%E8%A6%81%E5%B8%AE%E5%8A%A9) 需要帮助
如果你任何建议或需求，欢迎前往 [需要帮助](https://developers.weixin.qq.com/miniprogram/dev/devtools/minitest/help) 页面，扫码加入云测官方企微群，联系群主反馈。
![](https://res8.wxqcloud.qq.com.cn/wxdoc/56617deb-b17d-4cf1-bccd-71d2c41ccc76.svg)文档变更日志（1条）
2026 年 05 月 09 日
文档描述优化