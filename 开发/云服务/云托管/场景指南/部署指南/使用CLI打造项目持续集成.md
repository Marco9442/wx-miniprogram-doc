# [#](#使用CLI打造项目持续集成) 使用CLI打造项目持续集成

本篇主要讲解CODING持续集成如何和微信云托管CLI工具结合，从代码到部署服务的全过程。

**什么是持续集成？** 以下引用[CODING文档](https://help.coding.net/docs/ci/intro.html)。

> 当提交了一部分修改完成的代码后，我们总是希望可以快速得到直观且有效的反馈，及早暴露问题。在开发过程中总有一部分工作是相对机械化，易出错的（例如打包、部署）。为何不将这部分工作交给机器来做呢？仅需要轻点鼠标，起身泡杯咖啡，将部署与发布的事宜交由持续集成，把时间花在更有价值的事物上。

微信云托管的服务流水线能力也是做的这个事情，但以下场景可能标配流水线无法满足开发者需求，所以需要进行有限结合：

- 开发者使用了非Github/Gitlab/Gitee的其他仓库，或者自己内网搭建的私有仓库；
- 开发者有一些自己的项目特殊需要，有一些比较苛刻的构建条件。

既然流水线的最终目的是将项目镜像部署到云托管中，这一步CLI工具就可以完成，前面的打包镜像完全就可以自己实现。

基于这个方向，我们开始以java为例子，尝试一下这个过程。

## [#](#一、建立一个项目) 一、建立一个项目

在这里我们提供了一个非常简单的[SpringBoot项目](https://7765-web-9gikcbug35bad3a8-1304825656.tcb.qcloud.la/real/JAVA-CI.zip)，可以下载之后上传到CODING的项目代码仓库中。

我们后续要基于一个代码仓库来实施构建过程。

除了CODING之外，你也可以使用其他类似的集成方式，包括本机maven部署，或者使用其他jenkins持续集成（CODING基于jenkins）。

## [#](#二、构建项目) 二、构建项目

不同语言和框架构建命令不一样，这里遵循自己的业务项目就可以。

我们的SpringBoot项目例子，是MAVEN构建过程，可以直接在CODING的构建示例中选择。

![](https://res8.wxqcloud.qq.com.cn/wxdoc/9193c8d9-05ab-433a-b4d1-cb4515ace325.png)

CODING 持续集成全面兼容 Jenkinsfile，在文本编辑器中编写的配置文件所需遵循的语法规范与 Jenkinsfile 保持一致即可成功运行。

![](https://res8.wxqcloud.qq.com.cn/wxdoc/f380a14f-b973-4a04-b36a-347dcd5284d0.png)

从构建流程来看，基本涉及了打包，构建镜像，推送镜像的过程，根据自己的项目改一改就可以了。

在我们的例子中，直接到maven编译就可以了，执行完这一步骤，构建环境中的项目target目录会有jar包。

接下来我们开始把jar包进一步打成Docker镜像

## [#](#三、Docker镜像构建) 三、Docker镜像构建

jar包变Docker镜像，在实践教学[IDEA中开发的java项目如何部署到容器](https://developers.weixin.qq.com/community/business/doc/00042a4a180a8051f8adaee915940d)中有提到过。

主要原理就是jar包启动，手动操作如下：

1. 建立一个目录，在目录中导入构建的jar包，命名为 app.jar
2. 在同一目录下，创建一个 `Dockerfile` 文件，内容如下：

```
# 根据自己的版本引入支持的基础镜像，也可以引入openjdk这类
FROM java:8

# 命名和自己导入的对齐
COPY app.jar .

# 启动命令，需要自行确认对齐
CMD ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/app.jar"]
```

以上作为一个文件夹，然后就可以进行Docker镜像过程了。

上述用Jenkinsfile描述大概如下：

```
stage('准备Docker目录') {
  steps {
    sh 'mkdir werun' // 建立一个目录，用于Docker打包
    sh 'mv ./target/*.jar ./werun/app.jar' // 把jar包复制过来，不管名字是什么，复制过来一律叫app.jar
    sh 'mv Dockerfile ./werun' // 把根目录我们传的Dockerfile拿进来
  }
}
```

其中Dockerfile我们在代码中一起上传进去了。

接下来就是Docker打包镜像阶段了

```
stage('构建镜像并推送到云托管镜像仓库') {
  steps {
    sh "cd werun && docker build -t javatest:${DOCKER_IMAGE_VERSION} ."
    sh "docker login ccr.ccs.tencentyun.com --username=${DOCKER_USER} --password=${DOCKER_PASSWORD}"
    sh "docker tag javatest:${DOCKER_IMAGE_VERSION} ${DOCKER_RES}:${DOCKER_IMAGE_VERSION}"
    sh "docker push ${DOCKER_RES}:${DOCKER_IMAGE_VERSION}"
  }
}
```

环境变量这些根据自己的需要配置在全局环境变量中。

推送的镜像仓库可以参考[此文档](../../guide/service/image)找到并配置。

![](https://res8.wxqcloud.qq.com.cn/wxdoc/0d0503e7-a724-4ed4-9f34-e7e4e22f708c.png)

## [#](#四、运行CLI工具) 四、运行CLI工具

上传到微信云托管挂载的镜像仓库之后，接下来我们就可以指定刚才上传的镜像进行部署了,CLI的使用可以参考[此文档](../../guide/cli/index)。

Jenkinsfile示例如下：

```
stage('发布微信云托管') {
  steps {
    script {
      sh 'npm install -g @wxcloud/cli' // 安装CLI工具
      sh 'wxcloud login --appId ${WXCLI_APPID} --privateKey ${WXCLI_KEY}' // 登录CLI
      result = sh returnStdout: true ,script: "wxcloud run:deploy --libraryImage ${DOCKER_IMAGE_VERSION} --containerPort=${PORT} --envId=${WXRUN_ENVID} --serviceName=${WERUN_SERVER} --remark ${REMARK} --releaseType FULL --detach --noConfirm" // 部署命令
      result = result.trim()
      echo result
    }
  }
}
```

![](https://res8.wxqcloud.qq.com.cn/wxdoc/3d910fff-1db5-4bd9-b022-279afaa4b300.png)

## [#](#五、总结) 五、总结

以上以CODING控制台举例，原理可以举一反三应用于其他持续集成平台中。

CLI工具除了可以指定线上镜像，也可以直接上传代码包构建，上述SpringBoot项目如果直接上传，Dockerfile需要分为两个流程，一个是打jar包，另外一个通过jar包构建Docker镜像，所以呈现的内容如下：

```
# 这是项目打jar包的过程
FROM maven:3.6.0-jdk-8-slim as build
WORKDIR /app
COPY src /app/src
COPY settings.xml pom.xml /app/
RUN mvn -s /app/settings.xml -f /app/pom.xml clean package

# 这是jar包构建Docker镜像构成
FROM java:8
# 服务上一步打jar包步骤里的jar包
COPY --from=build /app/target/*.jar .
CMD ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/app.jar"]
```

也就是说你用持续集成来做打jar包的事情，就不需要再用docker重复这个事情了。说白了，折腾这么多主要是为了运行，从项目代码到jar包，再从jar包到Docker镜像，这两个构建阶段，你放到哪里都是可以的，根据自己的需要来。

Incorrect translation.