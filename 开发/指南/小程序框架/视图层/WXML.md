# [#](#WXML) WXML

WXML（WeiXin Markup Language）是框架设计的一套标签语言，结合[基础组件](index)、[事件系统](event)，可以构建出页面的结构。

要完整了解 WXML 语法，请参考[WXML 语法参考](https://developers.weixin.qq.com/miniprogram/dev/reference/wxml/)。

用以下一些简单的例子来看看 WXML 具有什么能力：

## [#](#数据绑定) 数据绑定

```
<!--wxml-->
<view> {{message}} </view>
```

```
// page.js
Page({
  data: {
    message: 'Hello MINA!'
  }
})
```

## [#](#列表渲染) 列表渲染

```
<!--wxml-->
<view wx:for="{{array}}"> {{item}} </view>
```

```
// page.js
Page({
  data: {
    array: [1, 2, 3, 4, 5]
  }
})
```

## [#](#条件渲染) 条件渲染

```
<!--wxml-->
<view wx:if="{{view == 'WEBVIEW'}}"> WEBVIEW </view>
<view wx:elif="{{view == 'APP'}}"> APP </view>
<view wx:elif="{{view == 'MINA'}}"> MINA </view>
<view wx:else> UNKNOWN </view>
```

```
// page.js
Page({
  data: {
    view: 'MINA'
  }
})
```

## [#](#模板) 模板

```
<!--wxml-->
<template name="staffName">
  <view>
    FirstName: {{firstName}}, LastName: {{lastName}}
  </view>
</template>

<template is="staffName" data="{{...staffA}}"></template>
<template is="staffName" data="{{...staffB}}"></template>
<template is="staffName" data="{{...staffC}}"></template>
```

```
// page.js
Page({
  data: {
    staffA: {firstName: 'Hulk', lastName: 'Hu'},
    staffB: {firstName: 'Shang', lastName: 'You'},
    staffC: {firstName: 'Gideon', lastName: 'Lin'}
  }
})
```

具体的能力以及使用方式在以下章节查看：

[数据绑定](https://developers.weixin.qq.com/miniprogram/dev/reference/wxml/data)、[列表渲染](https://developers.weixin.qq.com/miniprogram/dev/reference/wxml/list)、[条件渲染](https://developers.weixin.qq.com/miniprogram/dev/reference/wxml/conditional)、[模板](https://developers.weixin.qq.com/miniprogram/dev/reference/wxml/template)、[引用](https://developers.weixin.qq.com/miniprogram/dev/reference/wxml/import)

Incorrect translation.