# [#](#WebSocket-WEB和其他客户端) WebSocket-WEB和其他客户端

## [#](#使用指南) 使用指南

服务端和客户端都按照正常的 WebSocket 协议接入

服务端如果没有现成的例子，请访问[此网址](https://github.com/TCloudBase/wxcloudrun-websocket-nodejs)下载示例源码

将服务部署后，在服务的「云端调试」板块中，找到 WebSocket，获取到下述形式的链接：

```
wss://demo-prod-aaa-110.ap-shanghai.run.wxcloudrun.com
```

接下来就按照客户端协议来正常开发。

## [#](#示例代码) 示例代码

WEB端例子：

```
<script>
  const ws = new WebSocket("wss://demo-prod-aaa-110.ap-shanghai.run.wxcloudrun.com");
  ws.onopen = function () {
    console.log('链接建立成功')
    ws.send("微信云托管测试信息") // 发送消息
  };
  ws.onmessage = function (evt) {
    console.log(evt.data)
  };
  ws.onclose = function () {
    console.log('链接已经关闭')
  };
</script>
```

Incorrect translation.