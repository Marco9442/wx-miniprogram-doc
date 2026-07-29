# [#](#WebSocket) WebSocket

微信云托管支持 WebSocket 服务，如果你当前没有现成的例子，请访问[此网址](https://github.com/TCloudBase/wxcloudrun-websocket-nodejs)下载示例源码

下载源码后，按照[服务指南](../../guide/service/version)新建一个服务版本，选择代码包本地上传方式，端口监听选择 `3000`，部署服务

**注意**

1）WebSocket 服务，云托管底层会有健康检查尝试连接，属于正常的请求；你可以通过请求的 `header` 进行识别进行过滤，正常的 WebSocket 连接请求会带 `Connection: Upgrade` 、`Upgrade: websocket` 这两个 `header`。可根据 `header` 的差异在代码中过滤请求。

2）WebSocket 目前只支持 wss 方式连接；

目前客户端支持情况如下：

| 客户端 | 支持情况 | 文档 |
| --- | --- | --- |
| 微信小程序 | 可使用 | [使用文档](miniprogram) |
| 公众号H5 | 可使用 | [使用文档](h5) |
| WEB或其他客户端 | 可使用 | [使用文档](web) |

Incorrect translation.