# [#](#getIotBindContactList-Object-req) getIotBindContactList(Object req)

> 本接口为异步接口，返回 `Promise` 对象。

根据 openId，查询指定用户是否授权某台设备。

## [#](#参数) 参数

### [#](#Object-req) Object req

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| sn | string |  | 是 | 设备 SN |
| model\_id | string |  | 是 | 设备的 model\_id |
| openid\_list | string[] |  | 是 | 要查询的用户 openId 列表 |

## [#](#返回值) 返回值

### [#](#Object) Object

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| errcode | number | 错误码 |
| errmsg | string | 错误信息 |
| contact\_list | Info[] | openid 授权信息，status: 1 表示已授权，0 表示未授权 |

## [#](#示例代码) 示例代码

```
const wmpfVoip = requirePlugin('wmpf-voip').default

wmpfVoip
  .getIotBindContactList({
    sn: '设备sn',
    model_id: '申请的modelid',
    openid_list: ['openid_1', 'openid_2'], // 传入需要验证的openid列表
  })
  .then(res => {
    console.log(`[getIotBindContactList]:`, res.contact_list)
    // [{sn: 'xxx', model_id: 'xxx', status: 0}]
    // status: 0/未授权；1/已授权
  })
```

Incorrect translation.