# [#](#void-setVoipEndPagePath-Object-req) void setVoipEndPagePath(Object req)

设置插件功能执行完成后的跳转页面路径。

## [#](#参数) 参数

### [#](#Object-req) Object req

| 属性 | 类型 | 默认值 | 必填 | 说明 | 最低版本 |
| --- | --- | --- | --- | --- | --- |
| url | string |  | 是 | 跳转页面的路径 |  |
| key | string |  | 是 | 业务类型，参见下文 |  |
| options | string |  | 否 | 跳转页面的 queryString。最终跳转的路径为 `url + '?' + options` |  |
| routeType | string | redirectTo | 否 | 页面跳转的方式，取值有：redirectTo/switchTab/reLaunch | 2.3.9 |

**业务类型**

key 参数有以下取值

- `Call`：设置通话结束后跳转的页面路径，**需保证在通话结束前设置**。
- `BindContact`：设置联系人绑定关系页面操作完成后要跳转的页面路径。仅用于[校园场景支付刷脸模式](../wxpay)。

## [#](#返回值) 返回值

无

## [#](#示例代码) 示例代码

```
const wmpfVoip = requirePlugin('wmpf-voip').default

// 可根据 typeof wmpf !== 'undefined' 判断是否是设备端跳转不同页面
wmpfVoip.setVoipEndPagePath({
  url: '/pages/contactList/contactList',
  options: 'param1=xxx&param2=xxx',
  key: 'Call',
})
```

Incorrect translation.