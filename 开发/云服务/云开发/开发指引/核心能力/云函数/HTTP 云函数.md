# [#](#HTTP-云函数) HTTP 云函数

「HTTP 云函数」是专为 Web 服务场景设计的云函数类型，提供了原生 HTTP 支持、实时通信能力和多函数路由等特性。

## [#](#HTTP-云函数开发指引) HTTP 云函数开发指引

### [#](#创建函数入口文件) 创建函数入口文件

**Nodejs 项目示例**

创建 `index.js` 作为 HTTP 函数入口文件：

```
const http = require('http')
const port = 9000

const server = http.createServer((req, res) => {
  res.writeHead(200, { 'Content-Type': 'text/plain' })
  res.end('Hello World!')
})

server.listen(port, () => {
  console.log(`Server listening at http://localhost:${port}`)
})
```

**Python 项目示例**

创建 `main.py` 作为 HTTP 函数入口文件：

```
from http.server import HTTPServer, BaseHTTPRequestHandler

class Handler(BaseHTTPRequestHandler):
    def do_GET(self):
        self.send_response(200)
        self.send_header('Content-Type', 'text/plain')
        self.end_headers()
        self.wfile.write(b'Hello World!')

if __name__ == '__main__':
    server = HTTPServer(('0.0.0.0', 9000), Handler)
    print('Server listening at http://localhost:9000')
    server.serve_forever()
```

### [#](#创建启动脚本) 创建启动脚本

在项目根目录创建 `scf_bootstrap` 文件（**无扩展名**），内容为启动项目的命令：

**Nodejs 项目示例**

```
#!/bin/bash
node index.js
```

**Python 项目示例**

```
#!/bin/bash
python3 main.py
```

### [#](#项目结构) 项目结构

**Nodejs 项目示例**

完整的项目目录结构如下：

```
nodejs-http-function/
├── scf_bootstrap          # 启动脚本（必需，无扩展名）
├── package.json           # 项目配置
├── index.js                    # 函数入口文件
└── node_modules/       # 依赖包（npm install 后生成）
```

**Python 项目示例**

完整的项目目录结构如下：

```
python-http-function/
├── scf_bootstrap          # 启动脚本（必需，无扩展名）
└── main.py                    # 函数入口文件
```

**参考资源**：

- 更多示例：[示例代码仓库](https://github.com/TencentCloudBase/cloudbase-examples/tree/master/httpfunctions)
- 模板代码：[JavaScript 模板](https://github.com/TencentCloudBase/func-v2-template) | [TypeScript 模板](https://github.com/TencentCloudBase/cloudbase-examples/tree/master/cloudrunfunctions/ts-multiple-functions)

## [#](#函数框架) 函数框架

HTTP 云函数支持直接使用 web 相关框架来进行开发，例如：Nodejs 环境下的 Express、Koa、NestJS等，或 Python 环境下的 Flask、Django 等，或其他各语言的web框架。

HTTP云函数支持 web 框架，因此可以通过对应的 web 框架进行实现请求路由，更贴合开发习惯。

除 web 框架实现业务代码外，函数启动依赖 `scf_bootstrap` 的启动文件。

## [#](#scf-bootstrap启动文件说明) `scf_bootstrap`启动文件说明

在 HTTP 云函数中，`scf_bootstrap` 是一个**必需的启动文件**，作为 Web Server 的启动入口。它负责启动您的 Web 服务、配置运行环境、加载依赖并确保服务正常监听请求。

`scf_bootstrap` 文件在云函数实例启动时自动执行，主要承担以下职责：

| 职责 | 说明 |
| --- | --- |
| **启动 Web 服务** | 确保您的 Web 服务正常启动并监听请求（默认端口为 `9000`） |
| **环境配置** | 设定运行时依赖库的路径、环境变量等 |
| **依赖加载** | 加载自定义语言、版本依赖的库文件及扩展程序，如需实时拉取依赖，建议下载至 `/tmp` 目录 |
| **全局初始化** | 执行函数调用前所需的全局操作，（如 HTTP Client 初始化、数据库连接池创建等），便于在调用阶段复用 |
| **插件加载** | 启动安全、监控等插件 |

为了确保启动文件能被正确执行，必须满足以下条件：

| 要求 | 说明 |
| --- | --- |
| **文件名固定** | 必须命名为 `scf_bootstrap`，**不支持其他名称** |
| **可执行权限** | 文件必须具备可执行权限（建议 `777` 或 `755`） |
| **系统环境** | 需能在系统环境（CentOS 或 标准 Linux）中可运行 |
| **Shebang 声明** | 如果是 Shell 脚本，第一行必须包含 `#!/bin/bash` |
| **绝对路径** | 启动命令必须使用绝对路径（见"标准语言环境绝对路径"） |
| **监听地址** | 建议使用 `0.0.0.0`，**不可使用内部回环地址 `127.0.0.1`** |
| **文件格式** | 文件结尾必须以 LF 换行符结束（不能是 CRLF） |
| **写权限限制** | 在标准运行环境下，仅 `/tmp` 目录可读写，输出文件时请注意路径 |

> ⚠️ **提示**：在 Linux/macOS 系统中，使用 `chmod +x scf_bootstrap` 或 `chmod 777 scf_bootstrap` 命令设置可执行权限。

**标准语言环境绝对路径**

在编写启动命令时，必须使用语言对应的**绝对路径**。以下是常见版本路径参考：

| 语言版本 | 绝对路径 |
| --- | --- |
| **Node.js 18.15** | `/var/lang/node18/bin/node` |
| **Node.js 16.13** | `/var/lang/node16/bin/node` |
| **Node.js 14.18** | `/var/lang/node14/bin/node` |
| **Node.js 12.16** | `/var/lang/node12/bin/node` |
| **Python 3.10** | `/var/lang/python310/bin/python3.10` |
| **Python 3.9** | `/var/lang/python39/bin/python3.9` |
| **Python 3.7** | `/var/lang/python37/bin/python3.7` |
| **Python 3.6** | `/var/lang/python3/bin/python3.6` |
| **PHP 8.0** | `/var/lang/php80/bin/php` |
| **PHP 7.4** | `/var/lang/php74/bin/php` |
| **PHP 7.2** | `/var/lang/php7/bin/php` |
| **Java 11** | `/var/lang/java11/bin/java` |
| **Java 8** | `/var/lang/java8/bin/java` |

**`scf_bootstrap`示例**

Express 框架：

```
#!/bin/bash
export PORT=9000
/var/lang/node18/bin/node app.js
```

Flask 框架

```
#!/bin/bash
export PORT=9000
/var/lang/python3/bin/python3 app.py
```

Django 框架

```
#!/bin/bash
export PORT=9000
/var/lang/python3/bin/python3 manage.py runserver 0.0.0.0:9000
```

SpringBoot 框架

```
#!/bin/bash
export PORT=9000
/var/lang/java8/bin/java -Dserver.port=${PORT} -jar target/my-app.jar
```

## [#](#调用-HTTP-云函数) 调用 HTTP 云函数

通过微信小程序原生 SDK 中的 `wx.cloud.callHTTPFunction` 方法，可以直接调用 HTTP 云函数，支持流式传输（SSE）。

> ⚠️ **版本要求**：调用 HTTP 云函数时，确保小程序基础库版本为 **3.15.1** 及以上。

### [#](#调用方法) 调用方法

`wx.cloud.callHTTPFunction` 方法的调用方式与 `wx.request` 类似，支持多种请求方法和流式传输。

**基础调用示例：**

```
wx.cloud.callHTTPFunction({
  name: 'my-http-function', // 云函数名称
  config: {
    env: 'your-env-id', // 可选：指定云开发环境 ID
  },
  data: { key: 'value' }, // 请求数据
  path: '/api/hello', // 请求路径
  method: 'post', // 请求方法
  header: {
    'X-Custom-Header': 'value', // 自定义请求头
  },
  timeout: 1500, // 超时时间（毫秒）
  enableChunked: true, // 启用流式传输
  onHeadersReceived: (res) => {
    console.log("httpFunc headers received", res)
  },
  onChunkedReceived: (res) => {
    console.log("chunked",res)
    const arrayBuffer = res.data;
    const uint8Array = new Uint8Array(arrayBuffer);
    let str = '';
    for (let i = 0; i < uint8Array.length; i++) {
      str += String.fromCharCode(uint8Array[i]);
    }
    // 尝试解码 utf-8
    try {
      const decodedStr = decodeURIComponent(escape(str));
      console.log('SSE chunk received:', decodedStr);
    } catch (e) {
      console.log('SSE chunk received (raw):', str);
    }
  },
  success: (res) => {
    console.log("httpFunc success", res)

  },
  fail: (err) => {
    console.log("callHttpFunction err", err)

  },
});
```

### [#](#请求参数说明) 请求参数说明

#### [#](#调用参数) 调用参数

| 参数 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| `name` | string | 是 | 云函数名称 |
| `config` | object | 否 | 配置对象 |
| `config.env` | string | 否 | 云开发环境 ID |
| `data` | object | 否 | 请求数据（body） |
| `path` | string | 是 | 请求路径 |
| `method` | string | 是 | 请求方法，可选值：`get` / `post` / `put` / `delete` / `head` / `options` |
| `header` | object | 否 | 自定义请求头 |
| `enableChunked` | boolean | 否 | 是否启用流式传输 |
| `dataType` | string | 否 | 指定响应的数据类型，仅非流式情况下生效 |
| `responseType` | string | 否 | 指定响应的数据类型，仅非流式情况下生效 |
| `timeout` | number | 否 | 请求超时时间，单位为毫秒（ms），需设置小于 1500 ms |
| `success` | function | 否 | 请求成功的回调 |
| `fail` | function | 否 | 请求失败的回调 |
| `complete` | function | 否 | 请求结束的回调（成功或失败都会执行） |
| `onHeadersReceived` | function | 否 | 流式模式下，收到响应头时的回调 |
| `onChunkedReceived` | function | 否 | 流式模式下，收到 chunk 数据时的回调 |

#### [#](#返回参数) 返回参数

| 参数 | 类型 | 说明 |
| --- | --- | --- |
| `data` | string / Object / ArrayBuffer | 返回的数据内容，流式返回时为 ArrayBuffer |
| `statusCode` | number | HTTP 状态码 |
| `header` | Object | 响应头 |

## [#](#实时通信能力) 实时通信能力

HTTP 云函数提供两种实时通信方式：「SSE（Server-Sent Events）」和「WebSocket」。

### [#](#SSE（Server-Sent-Events）) SSE（Server-Sent Events）

「SSE」是一种基于 HTTP 的服务端推送技术，支持**单向**实时数据流传输（服务端 → 客户端）。

**特点**：

- 基于 HTTP 协议，兼容性好，**默认支持无需配置**
- 客户端自动重连
- 实现简单，资源占用低
- 适合 AI 对话流式输出、实时日志、进度更新等场景

**代码示例**：

使用 Express 实现 SSE 流式响应：

```
const express = require('express');
const app = express();

// SSE 路由
app.get('/stream', (req, res) => {
	// 设置 SSE 响应头
	res.setHeader('Content-Type', 'text/event-stream');
	res.setHeader('Cache-Control', 'no-cache');
	res.setHeader('Connection', 'keep-alive');

	console.log('新的 SSE 连接建立');

	// 流式推送数据
	const msg = ['SSE', 'empowering', 'GPT', 'applications', '!', 'Happy', 'chatting', '!'];

	let index = 0;
	const intervalId = setInterval(() => {
		if (index < msg.length) {
			// 发送 SSE 消息
			const data = {
				id: index,
				content: msg[index],
			};
			res.write(`data: ${JSON.stringify(data)}\n\n`);
			index++;
		} else {
			// 完成推送，关闭连接
			clearInterval(intervalId);
			res.end();
		}
	}, 1000);

	// 客户端断开连接时清理
	req.on('close', () => {
		clearInterval(intervalId);
		console.log('SSE 连接已关闭');
	});
});

// 启动服务，监听 9000 端口
app.listen(9000, () => {
	console.log('SSE 服务已启动，监听端口 9000');
});
```

小程序侧接收 SSE 数据：

```
wx.cloud.callHTTPFunction({
  name: 'express-sse', // 根据需要修改为实际函数名
  path: '/sse',
  method: 'GET',
  enableChunked: true,
  onHeadersReceived: (res) => {
    console.log("httpFn headers received", res)
  },
  onChunkedReceived: (res) => {
    console.log("chunked",res)
    const arrayBuffer = res.data;
    const uint8Array = new Uint8Array(arrayBuffer);
    let str = '';
    for (let i = 0; i < uint8Array.length; i++) {
      str += String.fromCharCode(uint8Array[i]);
    }
    // 尝试解码 utf-8
    try {
      const decodedStr = decodeURIComponent(escape(str));
      console.log('SSE chunk received:', decodedStr);
    } catch (e) {
      console.log('SSE chunk received (raw):', str);
    }
  },
});
```

### [#](#WebSocket) WebSocket

「WebSocket」是一种全双工通信协议，支持**双向**实时通信（服务端 ↔ 客户端）。

**特点**：

- 双向实时通信，持久连接，低延迟
- 需要在控制台**开启 WebSocket 协议支持**
- 服务器必须监听 **9000 端口**
- 适合实时聊天、协作编辑、游戏服务器等场景

**代码示例**：

使用 `ws` 库实现 WebSocket 服务器：

```
const WebSocket = require('ws');

// 创建 WebSocket 服务器，必须监听 9000 端口
const wss = new WebSocket.Server({ port: 9000 });

wss.on('connection', (ws) => {
	console.log('新连接建立');

	// 发送欢迎消息
	ws.send('欢迎连接到 WebSocket 服务');

	// 接收消息
	ws.on('message', (message) => {
		console.log('收到消息:', message.toString());

		// 回复消息
		const response = {
			type: 'response',
			data: message.toString(),
			timestamp: Date.now(),
		};
		ws.send(JSON.stringify(response));
	});

	// 连接关闭
	ws.on('close', () => {
		console.log('连接已关闭');
	});

	// 错误处理
	ws.on('error', (error) => {
		console.error('WebSocket 错误:', error);
	});
});

console.log('WebSocket 服务器已启动，监听端口 9000');
```

### [#](#技术选型对比) 技术选型对比

| 特性 | SSE | WebSocket |
| --- | --- | --- |
| 通信方式 | 单向（服务端→客户端） | 双向（服务端↔客户端） |
| 协议 | HTTP | WebSocket 协议 |
| 实现复杂度 | 简单 | 相对复杂 |
| 配置要求 | 无需配置 | 需控制台开启 |
| 自动重连 | 是 | 否（需手动实现） |
| 适用场景 | 单向数据推送 | 实时双向通信 |

**选择建议**：

- 只需服务端推送数据（如 AI 对话、日志、进度）→ 选择 **SSE**
- 需要双向实时通信（如聊天、协作、游戏）→ 选择 **WebSocket**

Incorrect translation.