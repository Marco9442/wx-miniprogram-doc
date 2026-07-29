# [#](#普通网页-访问云托管服务) 普通网页-访问云托管服务

假设你的公网访问域名是：`https://demo.ap-shanghai.run.tcloudbase.com`

服务项目中有业务路径如下：

- `/`：GET形式
- `/do`：POST形式
- `/upload`：PUT形式

浏览器中，对应的访问应该是：

```
// 【/】GET形式
fetch('https://demo.ap-shanghai.run.tcloudbase.com').then(r => r.json()).then(console.log)

// 【/do】POST形式
fetch("https://demo.ap-shanghai.run.tcloudbase.com/post",{
  method: 'POST'
}).then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

// 【/upload】PUT形式
fetch("https://demo.ap-shanghai.run.tcloudbase.com/upload", {
  method: 'PUT'
}).then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

需要注意，此种方法调用云托管服务，不附带微信用户信息，请自己建立用户登录体系。

Incorrect translation.