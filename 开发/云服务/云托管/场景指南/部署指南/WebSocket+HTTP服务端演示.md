# [#](#WebSocket-HTTP服务端演示-Node-js-Express) WebSocket+HTTP服务端演示[Node.js+Express]

## [#](#项目介绍) 项目介绍

项目所在仓库：[github](https://github.com/WeixinCloud/wxcloud-websocket-express)

本项目基于Node.js语言，使用[express-ws](https://www.npmjs.com/package/express-ws)完成了一个简单的websocket服务。

小程序可以向此服务发起ws连接，连接后将用户信息保存在本机中，可以通过另一个http接口查询当前连接的所有用户。

并且项目还针对同一个微信用户多次连接有限制，多次连接将被拒绝。

**需要注意，项目中用户信息保存直接保存在容器中，如果是多个容器则无法做到全局唯一性，建议正式项目将信息保存转移到公共的数据库或者存储中。**

## [#](#项目部署) 项目部署

1. 将项目作为文件夹上传到微信云托管建立服务，名称可以随意，在这里为`ws`。
2. 在小程序中页面js里，可以粘贴下面代码，注意修改环境ID以及服务名称

```
Page({
    async onLoad() {
        wx.cloud.init()
        await websocketTest('1')
        await websocketTest('2') // 故意多发起一次链接
    }
})

async function callcontainer() {
    const info = await wx.cloud.callContainer({
        config: {
            env: '微信云托管环境ID'
        },
        path: '/query',
        header: {
            "X-WX-SERVICE": 'ws', // 替换自己的服务名
            "content-type": 'application/json'
        },
        method: "POST"
    })
    return info.data
}

async function websocketTest(flag) {
    const { socketTask } = await wx.cloud.connectContainer({
        config: {
            env: '微信云托管环境ID',
        },
        service: 'ws', // 替换自己的服务名
        path: '/ws'
    })
    socketTask.onMessage(function (res) {
        console.log(flag, '【WEBSOCKET】', res.data)
    })
    socketTask.onOpen(async function (res) {
        console.log(flag,'【WEBSOCKET】', '链接成功！')
        console.log(flag,'当前链接',await callcontainer())
        socketTask.send({
            data: '这是小程序消息'
        })
    })
    socketTask.onClose(async function () {
        console.log(flag,'【WEBSOCKET】链接关闭！')
        console.log(flag,'当前链接',await callcontainer())
    })
    return socketTask
}
```

项目效果图如下：

![IDE](https://res8.wxqcloud.qq.com.cn/wxdoc/0410bf12-0529-4f12-b955-491779920a60.png)

Incorrect translation.