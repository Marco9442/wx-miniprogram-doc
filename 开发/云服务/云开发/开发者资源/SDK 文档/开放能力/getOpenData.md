# [#](#Cloud-getOpenData-list-string-Object) [Cloud](../Cloud).getOpenData(list: string[]): Object

> 支持端：[云函数](../../reference/changelog-server-sdk)

获取 CloudID 对应的开放数据

## [#](#参数) 参数

### [#](#list-string) list: string[]

要获取对应开放数据的 CloudID 列表

## [#](#返回值) 返回值

### [#](#Object) Object

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| list | Array.<Object> | 开放数据列表，与传入的 CloudID 列表一一对应 |

**list 的结构**

| 属性 | 类型 | 说明 |
| --- | --- | --- |
| cloudID | string | 开放数据 CloudID |
| data | Object | 开放数据 |

## [#](#说明) 说明

详见[通过云调用获取开放数据](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/signature)

## [#](#示例代码) 示例代码

```
const cloud = require('wx-server-sdk')
cloud.init({
  env: cloud.DYNAMIC_CURRENT_ENV
})

exports.main = async (event, context) => {
  const res = await cloud.getOpenData({
    list: event.openData.list, // 假设 event.openData.list 是一个 CloudID 字符串列表
  })
  return res.list
}
```

返回的结果结构类似如下（假设 `list` 长度为 1，其中的 CloudID 是微信运动数据的 CloudID）：

```
[{
  "cloudID": "27_Ih-9vxDaOhIbh48Bdpk90DUkUoNMAPaNtg7OSGM-P2wPEk1NbspjKGoql_g",
  "data": {
    "stepInfoList": [
      {
        "step": 9103,
        "timestamp": 1571673600
      },
      {
        "step": 9783,
        "timestamp": 1571760000
      }
    ],
    "watermark": {
      "appid": "wx3d289323f5900f8e",
      "timestamp": 1574338655
    }
  }
}]
```

Incorrect translation.