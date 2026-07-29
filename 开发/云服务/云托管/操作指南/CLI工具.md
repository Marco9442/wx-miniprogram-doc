# [#](#CLI工具) CLI工具

微信云托管推出CLI工具，帮助开发者能够在本地或者自定义CI/CD中快速进行版本创建和其他操作。

[微信云托管 CLI 官方文档](https://cloud.weixin.qq.com/cli/)

## [#](#安装) 安装

CLI工具安装前需要在安装 `npm`，具体请看[此文档](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)

```
npm install -g @wxcloud/cli
```

## [#](#获取CLI密钥) 获取CLI密钥

CLI工具的登录采用了密钥形式，在使用前需要前往[微信云托管控制台-设置-CLI密钥](https://cloud.weixin.qq.com/cloudrun/settings/other)生成，生成时需要账号管理员扫码，可以新建多个密钥，用于在不同地方使用。

![](https://res8.wxqcloud.qq.com.cn/wxdoc/20d5b25a-355b-424b-954f-231b237a3607.png)

获取的密钥不会在平台中显式保存，所以在新建后需要自己妥善保管。

## [#](#登录和注销) 登录和注销

### [#](#一、登录) 一、登录

传入微信APPID和CLI密钥，操作登录

```
wxcloud login [OPTIONS]
```

参数信息

```
OPTIONS
  -a, --appId=appId            微信 AppID
  -h, --help                   查看帮助
  -k, --privateKey=privateKey  微信云服务私钥
```

### [#](#二、注销) 二、注销

退出当前的登录

```
wxcloud logout
```

## [#](#查看信息) 查看信息

### [#](#一、查看环境列表) 一、查看环境列表

查看登录账号下所有的环境列表

```
wxcloud env:list [OPTIONS]
```

参数信息：

```
OPTIONS
  -h, --help  查看帮助
  --json      是否以json格式展示结果
```

返回信息JSON

```
{
  "code":0,
  "errmsg":"success",
  "data":[{
    "Alias":"wxrun",
    "EnvId":"wxrun-thisisaid",
    "CreateTime":"2021-06-02 19:17:16"
  }]
}
```

### [#](#二、查看服务列表) 二、查看服务列表

查看指定环境下的所有服务列表

```
wxcloud service:list [OPTIONS]
```

参数信息：

```
OPTIONS
  -e, --envId=envId              环境ID
  -h, --help                     查看帮助
  -p, --page=page                页数，每页100条
  -s, --serviceName=serviceName  服务名称，如果有值则只取这一个
  --json                         是否以json格式展示结果
```

返回信息JSON

```
{
  "code":0,
  "errmsg":"success",
  "data":[{
    "ServerName":"server",
    "Status":"succ",
    "IsPublicAccess":"开启",
    "DefaultPublicDomain":"https://server.ap-shanghai.run.tcloudbase.com",
    "CustomDomain":"-",
    "CreatedTime":"2022-04-25 11:14:53",
    "UpdatedTime":"2022-04-25 11:17:14"
  }]
}
```

### [#](#三、查看版本列表) 三、查看版本列表

查看指定环境下，指定服务的版本列表

```
wxcloud version:list [OPTIONS]
```

参数信息：

```
OPTIONS
  -e, --envId=envId              环境ID
  -h, --help                     查看帮助
  -p, --page=page                页数，每页100条
  -s, --serviceName=serviceName  服务名称
  --json                         是否以json格式展示结果
```

返回信息JSON

```
{
  "code":0,
  "errmsg":"success",
  "data":[{
    "VersionName":"server-001",
    "Status":"normal",
    "CreatedTime":"2022-04-25 11:15:35",
    "UpdatedTime":"2022-04-25 11:49:10"
  }]
}
```

## [#](#创建服务) 创建服务

在指定环境中，创建一个服务

```
wxcloud service:create [OPTIONS]
```

参数信息

```
OPTIONS
  -e, --envId=envId              环境ID
  -h, --help                     查看帮助
  -s, --serviceName=serviceName  服务名称
  --isPublic                     是否开通外网访问
  --json                         是否以json格式展示结果
```

返回信息JSON

```
{
  "code":0,
  "errmsg":"success",
  "data":null
}
{ 
  "code":"ResourceInUse",
  "errmsg": "当前环境已存在同名服务，请改名后重试",
  "data": null
}
```

## [#](#部署服务) 部署服务

针对指定环境，服务，发布一个新版本。

支持本地代码上传，发布版本后直接100%接入现网。

```
wxcloud run:deploy [OPTIONS] [PATH]
```

参数信息

```
ARGUMENTS
  PATH  [default: .] 项目根目录

OPTIONS
  -e, --envId=envId              环境ID
  -h, --help                     查看帮助信息

  -s, --serviceName=serviceName  服务名

  --override                     缺省的参数是否沿用上一次命令的配置
  --detach                       是否直接返回，不显示部署日志
  --noConfirm                    发布前是否跳过二次确认

  --dockerfile=dockerfile        Dockerfile文件名(代码包形式)
  --targetDir=targetDir          目标目录(代码包形式)
  
  --libraryImage=libraryImage    线上镜像仓库的tag(线上镜像形式部署)
  
  --containerPort=containerPort  监听端口
  --remark=remark                版本备注
  --releaseType=FULL|GRAY        发布策略；FULL-全量；GRAY-灰度；
  --envParams=envParams          服务环境变量，在此版本开始生效，同步到服务设置，格式为xx=a&yy=b，默认为空
```

返回信息JSON

```
{
  "code":0,
  "errmsg":"success",
  "data":null
}
{ 
  "code": "ResourceInUse",
  "errmsg": "当前已有部署发布任务运行中,请结束后再执行",
  "data": null 
}
```

## [#](#版本回退) 版本回退

将一个服务的线上版本切到之前的某一个版本中

```
wxcloud run:rollback [OPTIONS]
```

参数信息

```
OPTIONS
  -e, --envId=envId              环境ID
  -h, --help                     查看帮助
  -s, --serviceName=serviceName  服务名称
  -v, --version=version          回退版本
  --detach                       是否直接返回，不显示部署日志
  --json                         是否以json格式展示结果
  --noConfirm                    发布前是否跳过二次确认
```

返回信息JSON

```
{
  "code":0,
  "errmsg":"success",
  "data":null
}
{
  "code": "InvalidParameter",
  "errmsg": "当前版本 server-001 落后于回滚版本 server-003",
  "data": null
}
```

## [#](#上传云存储文件) 上传云存储文件

上传文件到对象存储或静态资源存储中

```
USAGE
  $ wxcloud storage:upload [PATH]

ARGUMENTS
  PATH  [default: .] 文件目录

EXAMPLE
  wxcloud storage:upload <文件目录>
```

参数信息

```
OPTIONS
  -c, --concurrency=concurrency       并发上传数量
  -e, --envId=envId                   环境ID
  -h, --help                          查看帮助信息
  -m, --mode=(staticstorage|storage)  上传模式：storage 为对象存储，staticstorage 为静态资源存储
  -r, --remotePath=remotePath         目标目录
```

## [#](#实际举例) 实际举例

在 `wxrun-id` 环境下的，`demo` 服务创建一个版本，以线上镜像作为源，端口为 `80`，不展示部署步骤，不确认，直接返回。

```
wxcloud run:deploy --envId wxrun-id --serviceName demo --libraryImage demo-001-20220425111535 --containerPort 80 --releaseType FULL --remark 测试备注 --noConfirm --detach
```

在 `wxrun-id` 环境下的，`demo` 服务创建一个版本，代码在当前命令运行目录，Dockerfile文件为 `Dockerfile`, 容器暴露端口为 `80`

```
wxcloud run:deploy --targetDir=. --dockerfile=Dockerfile --containerPort=80 --envId=wxrun-id --serviceName=demo
```

在 `wxrun-id` 环境下的，`demo` 服务创建一个版本，项目目录和端口配置按照之前最后的配置。

```
wxcloud run:deploy --envId=wxrun-id --serviceName=demo --override
```

在 `wxrun-id` 环境下的，`demo` 服务创建一个版本，项目目录和端口配置按照之前最后的配置，直接执行不二次确认。

```
wxcloud run:deploy --noConfirm --envId=wxrun-id --serviceName=demo --override
```

在 `wxrun-id` 环境下上传本地 `/foo/bar/baz` 目录下的所有文件到对象存储的根目录下。

```
wxcloud storage:upload /foo/bar/baz --envId=wxrun-id --mode=storage --remotePath=/
```

Incorrect translation.