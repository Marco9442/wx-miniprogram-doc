# [#](#路由API) 路由API

## [#](#navigateTo) navigateTo

**app.navigateTo(object)**

保留当前页面，跳转到应用内的某个页面。但是不允许跳转到 tabbar 页面。

**参数属性**

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| pageId | string | '' | 是 | 页面 ID |
| packageName | string | '' | 否 | 子应用名称 |
| params | object | {} | 否 | query object 对象 |
| events | Object | {} | 否 | 页面间通信接口，用于监听被打开页面发送到当前页面的数据。基础库 2.7.3 开始支持。 |
| success | function | 无 | 否 | 接口调用成功的回调函数， |
| fail | function | 无 | 否 | 接口调用失败的回调函数 |
| complete | function | 无 | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

**示例代码**

```
app.navigateTo({
    pageId: 'index',    // 页面 Id 
    params: {key: 'value'},
});
```

## [#](#redirectTo) redirectTo

**redirectTo(object)**

关闭当前页面，跳转到应用内的某个页面。但是不允许跳转到 tabbar 页面。

**参数属性**

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| pageId | string | '' | 是 | 页面 ID |
| packageName | string | '' | 否 | 子应用名称 |
| params | object | {} | 否 | query object 对象 |
| events | Object | {} | 否 | 页面间通信接口，用于监听被打开页面发送到当前页面的数据。基础库 2.7.3 开始支持。 |
| success | function | 无 | 否 | 接口调用成功的回调函数 |
| fail | function | 无 | 否 | 接口调用失败的回调函数 |
| complete | function | 无 | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

**示例代码**

```
app.redirectTo({
    pageId: 'home',    // 页面 Id 
    packageName: '',   // 主应用为空或不填，子模块填写 子包目录，查找位置 子包编辑器 --- 页面 --- 子包目录
    params: {key: 'value'}
});
```

## [#](#reLaunch) reLaunch

**reLaunch(object)**

关闭所有页面，打开到应用内的某个页面

**参数属性**

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| pageId | string | '' | 是 | 页面 ID |
| packageName | string | '' | 否 | 子应用名称 |
| params | object | {} | 否 | query object 对象 |
| events | Object | {} | 否 | 页面间通信接口，用于监听被打开页面发送到当前页面的数据。基础库 2.7.3 开始支持。 |
| success | function | 无 | 否 | 接口调用成功的回调函数 |
| fail | function | 无 | 否 | 接口调用失败的回调函数 |
| complete | function | 无 | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

**示例代码**

```
app.reLaunch({
    pageId: 'home',    // 页面 Id 
    packageName: '',   // 主应用为空或不填，子模块填写 子包目录，查找位置 子包编辑器 --- 页面 --- 子包目录
    params: {}
})
```

## [#](#navigateBack) navigateBack

**app.navigateBack(object)**

关闭所有页面，打开到应用内的某个页面。

**参数属性**

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| delta | number | 1 | 否 | 返回的页面数，如果 delta 大于现有页面数，则返回到首页。 |
| success | function | 无 | 否 | 接口调用成功的回调函数 |
| fail | function | 无 | 否 | 接口调用失败的回调函数 |
| complete | function | 无 | 否 | 接口调用结束的回调函数（调用成功、失败都会执行） |

**示例代码**

```
app.navigateBack({
    delta: 1
});
```

Incorrect translation.