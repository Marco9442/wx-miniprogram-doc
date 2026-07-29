# [#](#数据源API) 数据源API

## [#](#cloud-dataSources) cloud.dataSources

通过 `app.cloud.dataSources`可以获取到当前应用绑定的所有数据源。

```
console.log(app.cloud.dataSources);
// 以示例应用为例，输出 {logUser: Object}
```

## [#](#在低码编辑器中使用数据源) 在低码编辑器中使用数据源

在应用的低代码编辑器及微搭组件的组件代码中可以使用以下 API 接口进行数据源的调用

| 接口名称 | 接口功能 | 接口说明 |
| --- | --- | --- |
| app.cloud.getTempFileURL | 获取云存储文件的临时访问链接 | [查看文档](https://docs.cloudbase.net/lowcode/datasource/usage#appcloudgettempfileurl) |
| app.cloud.utils | cloud-sdk的辅助工具方法 | [查看文档](https://docs.cloudbase.net/lowcode/datasource/usage#appcloudutils) |
| app.cloud.getCloudInstance | 返回云开发web-sdk初始化后的实例 | [查看文档](https://docs.cloudbase.net/lowcode/datasource/usage#appcloudgetcloudinstance) |
| app.cloud.callFunction | 调用云开发的云函数 | [查看文档](https://docs.cloudbase.net/lowcode/datasource/usage#appcloudcallfunction) |
| app.cloud.callWedaApi | 调用微搭后端API服务 | [查看文档](https://docs.cloudbase.net/lowcode/datasource/usage#appcloudcallwedaapi) |
| app.cloud.callWorkflow | 调用微搭流程服务 | [查看文档](https://docs.cloudbase.net/lowcode/datasource/usage#appcloudcallworkflow) |

## [#](#云函数) 云函数

在微搭中，云函数建立在数据源之下，只有当应用绑定了某个数据源，才能调用到该数据源以下的云函数。

> 说明
>
> 关于云函数的基本用法，请参见 [云函数开发指引](../functions) 。

假设当前应用绑定了 `logUser` 数据源,数据源包含 `create`, `delete`, `update`, `getItem`, `getList` 五个云函数,则可以在页面的生命周期调用云函数。

```
 async onPageLoad(query) {
    let res = await app.cloud.dataSources.logUser.create({
        name: 'Jack',
        email: 'example@qq.com'
    });
    console.log(res)
},
```

开启小程序的调试，即可看到调用云函数返回的结果。
![img](https://main.qcloudimg.com/raw/afbf6126ce08172f024099d8a2d8dedd.png)

## [#](#数据库) 数据库

微搭为开发者提供了数据库的使用渠道，具体使用方法可参见 [Open API 参考—数据库](https://docs.cloudbase.net/api-reference/openapi/database)。

## [#](#CMS) CMS

CloudBase CMS (opens new window)是云开发推出的，基于 Node.js 的 Headless 内容管理平台，提供了丰富的内容管理功能。使用方法可参见 [CMS 使用说明](https://docs.cloudbase.net/cms/usage/restful/intro)。

Incorrect translation.