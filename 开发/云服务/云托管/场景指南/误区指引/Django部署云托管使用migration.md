# [#](#Django部署云托管使用migration) Django部署云托管使用migration

Django 有一套 ORM，所以在使用 Django 开发项目时，我们不需要写SQL语句和数据库交互，直接通过 ORM 将类的操作转换成SQL操作。

参与上述步骤的内容主要有如下几种：

1. Models：也就是我们在开发项目所定义的数据模型。
2. Migrations：记录Model从初始状态演进为最终状态的步骤
3. django\_migrations：数据库中的表，记录执行了哪些步骤，为的是后续执行的时候就只需要执行没有执行的步骤。

当你的 Model 发生变化时，就可以执行 migration 来将 Model 与数据库 Table 同步，这个同步过程主要分两步：

1. `python manage.py makemigrations`，生成 migrations，将修改前的 Model 和修改后的 Model 对比，找出不同点，然后根据不同点找出同步的步骤，生成 migrations 文件。
2. `python manage.py migrate`，根据 migrations 文件执行SQL语句，操作数据库的表结构，如果数据库之前有操作过（不是空表），则根据 django\_migrations 表中记录，只执行没有执行过的步骤。

## [#](#migration-应该如何正确执行？) migration 应该如何正确执行？

migration 操作涉及数据库的SQL语句执行，所以我们在执行操作的时候，一定首先要判断执行的环境能不能连接数据库。

云托管的数据库有两个地址，一个是内网地址（只有同一个环境内的服务可以访问），一个是外网地址（有网的地方就能访问）。

### [#](#_1-Dockerfile-中-RUN-命令) 1. `Dockerfile` 中 `RUN` 命令

很多同学会直接在构建时执行 CMD 命令，在这里需要注意的是，构建环境（包括本地）都不在数据库VPC内网中。

也就是说，你在这里执行 `migration` ，内网地址是行不通的，你只能使用外网地址才能完成。

我们不建议这种用法，如果你的 `migration` 操作非常多的时候，因为操作耗时变长，相应的会增加构建耗时。

### [#](#_2-本机直接执行-migration-操作) 2. 本机直接执行 migration 操作

通过数据库外网地址连接，完成 `migration` 操作。

这种方法虽然简单，但如果说新旧版本依赖的数据库结构不同，有可能会引起业务故障。所以一般来说在线的生产环境，尽量不要在新版服务未就位的情况下，擅自变动数据库结构。

### [#](#_3-启动服务时执行-migration-操作) 3. 启动服务时执行 migration 操作

在 `Dockerfile` 的 `CMD` 或 `ENTRYPOINT` 命令中，集成 `migration` 操作，服务容器启动后即开始 `migration` 过程。

可以写一个sh脚本，将项目启动命令和 `migration` 操作写入。然后直接 `CMD` 此脚本。

这种方式有几个点需要注意：

1. 多个实例同时创建出来时，需要注意竞争处理，不要发生多个实例同时 `migration` 操作。
2. 尽可能优化 `migration` 操作，时间不要太长，可以通过重新生成 migrations 文件，改变 django\_migrations 记录值来实现。
3. `migration` 操作过程如果较长时，需要注意项目的兼容性，比如直接返回升级中字样。

### [#](#_4-直接进入Webshell，完成-migration-操作) 4. 直接进入Webshell，完成 migration 操作

如果你为了安全考虑，不想打开数据库外网地址。可以通过任意服务的实例 webshell 进入，执行 `migration` 操作，webshell进入的实例都是同数据库VPC内网环境。

你可以专门构建一个用户管理的服务，预先安装所以必须的程序，后续操作的时候，直接拉起这个管理服务，进入websell操作任务即可。

![](https://res8.wxqcloud.qq.com.cn/wxdoc/98407456-12d7-4534-b94b-689402a8f5a2.png)

Incorrect translation.