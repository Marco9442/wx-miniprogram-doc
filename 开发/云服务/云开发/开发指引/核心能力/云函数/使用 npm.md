## [#](#使用-npm) 使用 npm

在云函数中我们可以引入第三方依赖来帮助我们更快的开发。云函数的运行环境是 Node.js，因此我们可以使用 npm 安装第三方依赖。比如除了使用 Node.js 提供的原生 `http` 接口在云函数中发起网络请求，我们还可以使用一个流行的 Node.js 网络请求库 [request](https://github.com/request/request) 来更便捷的发起网络请求。

注意，在 IDE 中选择上传云函数时，可以选择云端安装依赖（不上传 node\_modules 文件夹）或全量上传（同时上传 node\_modules 文件夹）。

在[下一章节](wx-server-sdk)，我们一起了解下官方提供的云函数端 SDK： `wx-server-sdk`。

Incorrect translation.