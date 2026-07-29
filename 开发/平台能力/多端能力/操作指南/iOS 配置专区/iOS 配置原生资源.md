# [#](#iOS-配置原生资源) iOS 配置原生资源

在使用厂商推送或者其他 iOS 插件时，可能需要在项目 App 目录下添加一些配置文件。因此`project.miniapp.json`新增了一个配置`resourcePath`。

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img%2Fmelody%2F202412061612214.png)

## [#](#使用说明) 使用说明

- `resourcePath` 选择的是一个文件夹目录，该文件夹下的所有文件都会被拷贝到主包下
- 注意，该文件夹下的文件不允许覆盖主包下的同名文件，否则会报错

Incorrect translation.