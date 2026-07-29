# [#](#Android-配置原生资源) Android 配置原生资源

在使用厂商推送或者其他安卓插件时，可能需要在项目 app 目录下添加一些配置文件。因此`project.miniapp.json`新增了一个配置`resourcePath`。

![](https://testchu-7gy8occc8dcc14c3-1304825656.tcloudbaseapp.com/img/amin/202407181124406.png)

- 目前支持的可配置资源：
  - `app 根目录`
  - `app/src/main/assets`
  - `app/src/main/res`

## [#](#使用说明) 使用说明

`resourcePath` 选择的是一个文件夹目录，该文件夹目录结构如下：

```
.
├── app
│   └── test1.json
├── assets
│   └── test3.json
└── res
    ├── drawable-xhdpi-v4
    │   └── amintest.png
    └── raw
        └── xg_ring.mp3
```

- `app` 目录下的文件会被拷贝到 `app 根目录`下。
- `assets` 目录下的文件会被拷贝到 `app/src/main/assets` 目录下。
- `res` 目录下的文件会被对应拷贝到 `app/src/main/res` 对应文件夹下。

Incorrect translation.