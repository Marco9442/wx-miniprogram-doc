# [#](#wx-shareToOfficialAccount-Object-object) wx.shareToOfficialAccount(Object object)

> 基础库 3.9.2 开始支持，低版本需做[兼容处理](../../framework/compatibility.html)。

> **以 [Promise 风格](../../framework/app-service/api.html#%E5%BC%82%E6%AD%A5-API-%E8%BF%94%E5%9B%9E-Promise) 调用**：不支持
>
> **需要页面权限**：当前是插件页面时，宿主小程序不能调用该接口，反之亦然
>
> **小程序插件**：不支持

## [#](#功能描述) 功能描述

支持拉起贴图发表页，用户可将图片与文字内容发表为贴图。

## [#](#参数) 参数

### [#](#Object-object) Object object

| 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- |
| title | string |  | 是 | 贴图的标题 |  |
| content | string |  | 否 | 贴图的正文 |  |
| tags | Array.<string> |  | 否 | 贴图的标签，上限10个 |  |
| images | Array.<string> |  | 否 | 贴图的图片，必须为本地路径或临时路径 |  |
| recommendPath | string |  | 否 | 贴图链接卡片跳转页面 | [3.16.1](../../framework/compatibility.html) |
| recommendTitle | string |  | 否 | 贴图链接卡片标题 | [3.16.1](../../framework/compatibility.html) |
| success | function |  | 否 | 接口调用成功的回调函数 |  |
| fail | function |  | 否 | 接口调用失败的回调函数 |  |
| complete | function |  | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |  |

#### [#](#object-success-回调函数) object.success 回调函数

##### [#](#参数-2) 参数

###### [#](#Object-res) Object res

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| status | string | 贴图发表状态 |
| postUrl | string | 贴图发表后的文章链接，仅在success回调中返回，并且只有在发表成功后链接才可访问 |

## [#](#示例代码) 示例代码

```
wx.shareToOfficialAccount({
  title: '标题',
  content: '正文',
  tags: ['标签1', '标签2'],
  success: (res) => {
    // 贴图发表成功时触发
    console.log(res)
  },
  fail: (err) => {
    // 用户主动退出贴图发表页时触发
    console.log(err)
  },
  complete: (res) => {
    // 统计接口总共调用次数
    console.log(res)
  },
})
```

## [#](#推荐图标) 推荐图标

推荐使用贴图品牌图标作为该功能按钮，可使用下列高清素材：

![推荐图标1](https://res.wx.qq.com/op_res/92p2SWttdiOWvv5u9ZnyZwZrBXYrnz8TwwQNyOnfjFK2EG_Veqj4i0Gvs_EzXzzoXSByoaXkou7gw5_UIHiYRg)

![推荐图标2](https://res.wx.qq.com/op_res/T9EwP8p1f6xuyLUDFdfVP7qiQsqrm203K6PeQdxjh87W_ME_-ht8nLLdtMZmapwdrfgpmMctsjiBwZpkIyfxgA)

Incorrect translation.