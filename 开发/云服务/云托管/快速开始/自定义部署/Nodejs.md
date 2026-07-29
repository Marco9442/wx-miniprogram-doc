# [#](#快速入门-Node-JS自定义部署) 快速入门-Node.JS自定义部署

欢迎使用微信云托管，将带领你通过微信云托管创建一个服务，并在小程序和WEB端调用此服务。

我们将以Node.JS为例，如果你擅长其他语言和框架，可以前往对应的「上手指引」：

- [java版本](java)
- [php版本](index)
- [golang版本](golang)
- [python版本](python)

或者可以前往[微信云托管官方仓库](https://github.com/WeixinCloud)查看更多模板示例。

你可以用任何你认为趁手的代码编辑器来完成下述代码编辑操作，官方推荐「[Visual Studio Code](https://code.visualstudio.com/)」

## [#](#第一步：准备项目) 第一步：准备项目

### [#](#_1-创建一个项目目录，名称任意，本示例中为-hello) 1. 创建一个项目目录，名称任意，本示例中为 `hello`

你可以用CLI命令，或者可视化方式新建

```
mkdir hello
cd hello
```

### [#](#_2-在项目目录中，新建-Dockerfile-文件，并在文件中填入如下信息) 2. 在项目目录中，新建 `Dockerfile` 文件，并在文件中填入如下信息

```
FROM node:12-slim
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm install --only=production
COPY . ./
CMD [ "node", "index.js" ]
```

### [#](#_3-创建-index-js-文件，并在文件中填入如下代码) 3. 创建 `index.js` 文件，并在文件中填入如下代码

```
const express = require('express')
const app = express()

app.get('/', (req, res) => {
  res.send('欢迎使用微信云托管！')
})

const port = process.env.PORT || 80
app.listen(port, () => {
  console.log('服务启动成功，端口：', port)
})
```

### [#](#_4-新建-package-json-文件，并在文件中填入如下代码) 4. 新建 `package.json` 文件，并在文件中填入如下代码

```
{
  "name": "werun-nodejs",
  "version": "1.0.0",
  "description": "Simple example in Node",
  "main": "index.js",
  "scripts": {
    "start": "node index.js"
  },
  "author": "",
  "license": "Apache-2.0",
  "dependencies": {
    "express": "^4.16.4"
  }
}
```

你也可以自己 `npm init` , 然后安装 `npm i express`, 得到 `package.json`

## [#](#第二步：服务的部署和发布) 第二步：服务的部署和发布

### [#](#_1-访问微信云托管控制台) 1. 访问微信云托管控制台

访问[微信云托管控制台](https://cloud.weixin.qq.com/cloudrun?utm_source=wxrundoc&utm_content=quickstart_custom)，用微信扫描网页上的登录二维码，进入控制台

进入控制台之前，会提示要求你选择「小程序/公众号」，如果你选择的「小程序/公众号」没有微信云托管环境，则会提示新建

> **如何选择「小程序/公众号」？**  
> 微信云托管环境是建立在腾讯云账号上的，基于选择的「小程序/公众号」，复用其主体信息，建立腾讯云账号。如果你选择的「小程序/公众号」是企业主体，则腾讯云账号就是对应的企业主体，个人主体同理。  
> 如果你之前在某个「小程序/公众号」中开通过云开发，则会与其共用一个腾讯云账号。

新建环境时，需要填写环境名称，微信云托管会在你的名称后面追加一串字符组成环境ID

### [#](#_2-创建服务) 2. 创建服务

如果你已经有微信云托管环境，则可以直接进入控制台主平台

![](https://res8.wxqcloud.qq.com.cn/wxdoc/7d5c2c58-d0bb-4003-a947-2f909b9ef394.png)

点击服务列表中，右上角【新建服务】按钮，在微信云托管环境中创建一个服务

弹出框中填写「服务名称」，在这里名称填写`demo`，并开启「允许公网访问」

> **如何判断是否「允许公网访问」？**  
> 微信云托管的服务在运行过程中，可以接收公网和内网的访问。如果你是单一服务类型，则建议开启公网访问。  
> 微服务类型时，如果你的业务是面向用户的，比如登录注册服务，则开启公网访问。  
> 如果你的微服务模块用于支撑其他服务模块，比如令牌维护服务，则不要开启。  
> 在不开启公网访问时，服务只能被同一环境下的其他服务调用，或同一VPC网络（或内网互联）下的其他资源调用。公网其他资源将无法访问  
> 不开启公网访问只是限制外向内访问，不会限制服务内向外发送网络请求

新建服务后，点击服务列表中新建的 `demo` 服务，进入服务详情

### [#](#_3-创建第一个版本) 3. 创建第一个版本

进入服务详情默认在「部署发布」栏中，在「选择方式」中指定「手动上传代码包」

然后选择「上传方式」为文件夹，在「选择文件」中选择上传第一步创建的文件夹（注意一定选到文件夹）

![](https://res8.wxqcloud.qq.com.cn/wxdoc/f21b7745-10a2-45b3-b09c-98fa94e68b4d.png)

上传完毕后，效果如上图所示，点击「发布」按钮，开始版本部署

之后会跳转至部署发布流程，可以看到构建日志，整体分为「构建」和「部署」两个步骤，时间大概持续3分钟。

![](https://res8.wxqcloud.qq.com.cn/wxdoc/fe04ec99-9ec8-4057-a8d5-0ef64b89de8a.png)

如果中途部署出现问题，你可以复制上图中标识位置的信息到官方交流群或者提工单反馈。

### [#](#_4-部署发布) 4. 部署发布

当部署完毕后，会显示如下效果：

![](https://res8.wxqcloud.qq.com.cn/wxdoc/6691ed88-ff8d-4c32-8be6-373253208241.png)

在线上版本处，点击公网域名访问，看到如下效果

![](https://res8.wxqcloud.qq.com.cn/wxdoc/bb5528c6-ee85-4fd5-b8ce-af7b88a8e29e.png)

接下来，我们根据当前的状态，继续深入实践，去探索微信云托管的其他能力使用

## [#](#第三步：流水线和灰度发布) 第三步：流水线和灰度发布

### [#](#_1-将项目目录上传至自己的git网站，并建立git仓库) 1. 将项目目录上传至自己的git网站，并建立git仓库

你可以选择 `github`, `gitlab`, `gitee` 中的任意一个建立仓库，上传代码后得到仓库地址，保证根目录中有上述的3个文件

> 如果你暂时没有git网站账户或者git相关知识，可以先略过这一部分，直接看第四步。

### [#](#_2-在部署发布中，点击「发布」按钮) 2. 在部署发布中，点击「发布」按钮

新建一个发布单，此时选择方式为「绑定代码仓库」，具体什么形式根据上一步自己仓库所在指定。

如果第一次使用需要先进行授权，授权完毕后就可以在下面的「代码仓库」中加载账号下的仓库了。

选择刚才自己上传的仓库，分支根据自身仓库情况决定，一般是 `main`

![](https://res8.wxqcloud.qq.com.cn/wxdoc/97b19167-94af-41cf-9a40-06ce96a2dbf9.png)

勾选灰度发布，完成后点击「发布」按钮。

接下来，就进入了部署构建环节，和之前效果一致。

此时你配置的代码仓库信息已经保存在「服务设置-流水线」中，你可以前往修改，此后发布时，可以直接选择「执行流水线」，不需要每次配置仓库信息。[详细文档](../../guide/service/pipeline)

部署完毕后自动进入测试和灰度发布环节

### [#](#_3-测试和灰度发布) 3. 测试和灰度发布

在测试页面中，你可以通过两种方式来配置测试策略，一种是「openid白名单」，一种是「URL参数」

![](https://res8.wxqcloud.qq.com.cn/wxdoc/d94a08d2-6393-4dc4-9e43-a3eccc553833.png)

- openid白名单：可以在「小程序/公众号」获取用户openid，填写在测试列表中的用户，会使用新的版本提供服务，其他用旧的
- url参数：适合WEB网站，可以配置一个或多个get参数，符合条件的路径会使用新的版本提供服务，其他用旧的

填写后点击右下角「测试配置更新」使整个测试生效，以上两种方式可以同时配置

当你在真实项目中测试没有问题时，就可以开始灰度发布环节了，点击「灰度上线」按钮

![](https://res8.wxqcloud.qq.com.cn/wxdoc/5866c526-0024-4f6d-b5c7-38975778d266.png)

进入灰度过程后，你可以随意调整比例，来控制新版本在全网流量的占比，并随时在下面的监控中查看日志和运行情况，来判断版本的稳定性。如果有问题，可以点击「回退」按钮结束发布单，流量全部切换为之前的版本。

在整个灰度环节，你可以指定哪些用户一定打到最新版本。

当灰度流量比例设置100%后，就可以点击「结单」按钮，完成发布，此时所有流量都在新的版本中，一轮发布结束。

## [#](#第四步：调用微信云托管服务) 第四步：调用微信云托管服务

### [#](#_1-服务端和其他客户端应用) 1. 服务端和其他客户端应用

在第二步中，访问服务获取的默认域名地址，就是服务对外提供服务的入口，你可以将其按照正常的服务来调用访问，比如上述Node.js例子中，就可以用以下来调用：

```
# 请替换成自己的域名后再试
curl GET 'https://demo.ap-shanghai.run.tcloudbase.com'
```

你的项目在正式上线时，需要自己的域名，可以在按照[自定义域名指引](../../guide/domain/index)中的步骤完成域名的绑定。

如果你的项目中有其他路径，比如：

- / GET形式，上述Node.js例子就只有这个
- /do POST形式
- /upload PUT形式

按照如上的情况，对应的curl访问应该是：

```
# /do    POST形式
curl POST 'https://demo.ap-shanghai.run.tcloudbase.com/do'

# /upload  PUT形式
curl PUT 'https://demo.ap-shanghai.run.tcloudbase.com/upload'
```

浏览器中，对应的访问应该是：

```
// 【/】GET形式，上述Node.js例子就只有这个
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

各种语言和框架的网络请求，请参阅各语言的文档和其他教学资料。

### [#](#_2-微信小程序) 2. 微信小程序

首先，确认当前调试基础库版本为 `2.13.1` 以上，可以在开发者工具-详情-本地设置中查看当前的基础库版本。

![img](https://res.wx.qq.com/wxdoc/dist/assets/img/vendor.a4a774fb.png)

在小程序中使用如下的代码：

```
// 确认已经在 onLaunch 中调用过 wx.cloud.init 初始化环境（任意环境均可，可以填空）
const res = await wx.cloud.callContainer({
  config: {
    env: '填入云环境ID', // 微信云托管的环境ID
  },
  path: '/xxx', // 填入业务自定义路径和参数，根目录，就是 / 
  method: 'POST', // 按照自己的业务开发，选择对应的方法
  header: {
    'X-WX-SERVICE': 'xxx', // xxx中填入服务名称（微信云托管 - 服务管理 - 服务列表 - 服务名称），在上述实践中是 demo
  }
  // 其余参数同 wx.request
});

console.log(res);
```

`wx.cloud.callContainer` 其他参数，直接参考 [wx.request](https://developers.weixin.qq.com/miniprogram/dev/api/network/request/wx.request.html) API

以上Node.js例子访问的代码如下（在小程序项目 `app.js` 中覆盖写入如下代码）

```
App({
  onLaunch: async function () {
      wx.cloud.init({
        // env: "其他云开发环境，也可以不填"    // 此处init的环境ID和微信云托管没有作用关系，没用就留空
      });
      const res = await wx.cloud.callContainer({
        config: {
          env: "微信云托管ID", // 微信云托管环境ID，不能为空，替换自己的
        },
        path: '/', 
        method: 'GET',
        header: {
          'X-WX-SERVICE': 'demo',
        }
      });
      console.log(res); // 在控制台里查看打印
    }
});
```

### [#](#_3-普通WEB网页和微信公众号H5) 3. 普通WEB网页和微信公众号H5

首先，在网页中引入如下JS文件

```
https://web-9gikcbug35bad3a8-1304825656.tcloudbaseapp.com/sdk/1.3.0/cloud.js
```

使用如下代码：

```
// 初始化 Cloud 实例
var c1 = new wx.cloud.Cloud({
  identityless: true, // 如果你是普通WEB网页开发，设置为true，如果是公众号开发，则去掉
  resourceAppid: "小程序或公众号appid", // 微信云托管所在的「小程序/公众号」appid
  resourceEnv: "微信云托管ID", // 微信云托管环境ID，不能为空
});
await c1.init();

// 返回值同 wx.request
const res = await c1.callContainer({
  path: '/xxx', // 填入业务自定义路径和参数，根目录，就是 / 
  method: 'POST', // 按照自己的业务开发，选择对应的方法
  header: {
    'X-WX-SERVICE': 'xxx', // xxx中填入服务名称（微信云托管 - 服务管理 - 服务列表 - 服务名称）
  }
  // 其余参数同 wx.request
});

console.log(res);
```

`callContainer` 其他参数，直接参考 [wx.request](https://developers.weixin.qq.com/miniprogram/dev/api/network/request/wx.request.html) API

以上Node.js例子在浏览器中访问的代码如下（请将以下代码放置在html文件中，并在浏览器里运行控制台看结果）

```
<script src="https://web-9gikcbug35bad3a8-1304825656.tcloudbaseapp.com/sdk/1.3.0/cloud.js"></script>
<script>
  window.onload = async function () {
    var c1 = new cloud.Cloud({
      identityless: true,
      resourceAppid:'微信云托管所在的「小程序/公众号」appid', // 替换成自己的
      resourceEnv: "微信云托管环境ID", // 替换成自己的
    });
    await c1.init();

    const res = await c1.callContainer({
      path: '/',
      method: 'GET',
      header: {
        'X-WX-SERVICE': 'demo'
      }
    });

    console.log(res); // 在控制台里查看打印
  }
</script>
```

如果你是普通网页开发，则可以直接按照以上方式使用，或者直接对公网域名发起request请求。

如果你开发微信公众号网页，则前往对应的[开发指引](../../development/call/h5)

## [#](#写到最后) 写到最后

到此，我们完成了微信云托管核心【容器服务】的入门，你可以继续探索控制台的其他能力，在这里做一个引述：

1. 业务过程中需要存储数据到数据库、对象存储中，可以参看[数据库使用指引](../../guide/mysql/index)、[对象存储使用指引](../../guide/storage/index)
2. 绑定云托管的小程序/公众号在调用服务时，会带入微信生态信息；另外云托管服务可以免鉴权调用微信接口，具体可以参看[微信开放能力](../../guide/weixin/index)

Incorrect translation.