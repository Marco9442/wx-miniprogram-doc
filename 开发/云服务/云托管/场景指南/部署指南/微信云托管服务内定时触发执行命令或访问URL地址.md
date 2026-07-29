# [#](#微信云托管服务内定时触发执行命令或访问URL地址) 微信云托管服务内定时触发执行命令或访问URL地址

很多情况下，由于业务原因需要定时触发一项操作，可能是每天固定一个时间点发送消息，也可能每小时执行清理操作。

本文就主要展示，在云托管中实现定时触发。

云托管核心提供的是易配置的容器服务，所以在操作上我们都是围绕着容器来操作。

首先需要有你项目原本的DockerFile，我们要在其基础上进行修改，如果没有，那请参照这篇[知识](https://w.cloudbase.vip/detail.html?id=100024-007)。

有了DockerFile之后，我们在其中插入以下命令

```
FROM <你的基础镜像-是什么就是什么，不要动>

# 如果你的Dockerfile有apt-get安装过程，则省略这一项
RUN apt-get update

# 如果你的项目原本安装了一些，请紧跟在其后执行以下两个，如果有重复安装，请删除
RUN apt-get install -y --no-install-recommends cron
RUN apt-get install -y --no-install-recommends curl

# 对apt-get安装文件进行清理，减小体积，如果感觉没用，可以去掉
RUN rm -rf /var/lib/apt/lists/* && apt-get clean

# 定位你的项目目录
WORKDIR <你的项目是什么就是什么>

# 在你Dockerfile同级目录中创建一个文件，task.txt，并参考<a href="https://www.runoob.com/linux/linux-comm-crontab.html" target="_blank">命令</a>写上的定时触发策略

# 再创建另一个文件，task.sh，写下如下命令，并在命令尾部，把你项目的启动命令写上
# cron start
# service cron status
# echo '启动成功'

# 如果你原本的，有全部复制，那最好了，如果是有选择的复制，请一定要改一下，把两个文件复制到 WORKDIR 定位的目录中
COPY . ./

# 使用task.txt 新创建 cron 任务
RUN crontab task.txt

# 容器运行时，执行start.sh文件，包含crontab和你的项目启动
ENTRYPOINT ["sh", "start.sh"]
```

请按照上述命令的描述，正确改造你自己的dockerfile，主要改造的目标就3个：

1. 安装 `cron` ，如果需要触发业务 `url`，需要安装 `curl`，有些极简版的镜像没有，所以自己检查一下。
2. 创建 `crontab` 执行命令，在这里需要注意，如果启动时报错`install` 失败什么的，可能是txt文件编码不对，可以下载本文底部的压缩包，复制 `task.txt` 并更改。
3. 将你项目的启动命令和 `cron` 启动命令合并起来组成一个脚本，把容器运行的启动命令改成执行脚本。

以下提供了一个php可用版本的，容器运行时，每分钟会访问本地php项目，日志在项目目录下的 mylog.log，可以使用 `cat mylog.log` 查看实时触发的输出。

[点击下载php-cron示例](https://7765-web-v2-1g8g0y2x3197301a-1304825656.tcb.qcloud.la/FVZccLds4aqcs6x9L6t75bS1hry5S7jT_.zip?sign=61b28988bb9880ae17bd1b34d80e91c7&t=1677046601)

有关于其他版本，我们会根据需要动态新增，如果你不太理解更改方式需要帮助的话，请在[官方交流群](https://www.cloudbase.vip/scan/?code=werun)联系我们。

Incorrect translation.