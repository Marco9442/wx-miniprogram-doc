# [#](#Page) Page

Page 模块提供了控制小程序页面的方法。

## [#](#属性) 属性

### [#](#page-path) page.path

页面路径。

```
page.path: string
```

### [#](#page-query) page.query

页面参数。

```
page.query: Object
```

## [#](#方法) 方法

### [#](#page) page.$

获取页面元素。

```
page.$(selector: string): Promise<Element>
```

**参数说明**

| 字段 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| selector | string | 是 | - | 选择器 |

> 同 WXSS，仅支持部分 CSS 选择器，点击[此处](https://developers.weixin.qq.com/miniprogram/dev/framework/view/wxss)查看详细信息。

示例代码：

```
automator.launch().then(async miniProgram => {
  const page = await miniProgram.currentPage()
  const element = await page.$('.index-desc')
  console.log(element.tagName) // -> 'view'
})
```

### [#](#page-2) page.$$

获取页面元素数组。

```
page.$$(selector: string): Promise<Element[]>
```

**参数说明**

| 字段 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| selector | string | 是 | - | 选择器 |

> 该方法跟 $ 一样均无法选择自定义组件内的元素，请使用 [element.$](element)。

示例代码：

```
automator.launch().then(async miniProgram => {
  const page = await miniProgram.currentPage()
  const elements = await page.$$('.kind-list-text')
  console.log(elements.length)
})
```

### [#](#page-waitFor) page.waitFor

等待直到指定条件成立。

```
page.waitFor(condition: string | number | Function): Promise<void>
```

**参数说明**

| 字段 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| condition | string number Function | 是 | - | 等待条件 |

如果条件是 string 类型，那么该参数会被当成选择器，当该选择器选中元素个数不为零时，结束等待。

如果条件是 number 类型，那么该参数会被当成超时时长，当经过指定时间后，结束等待。

如果条件是 Function 类型，那么该参数会被当成断言函数，当该函数返回真值时，结束等待。

示例代码：

```
automator.launch().then(async miniProgram => {
  const page = await miniProgram.currentPage()
  await page.waitFor(5000) // 等待 5 秒
  await page.waitFor('picker') // 等待页面中出现 picker 元素
  await page.waitFor(async () => {
    return (await page.$$('picker')).length > 5
  }) // 等待页面中 picker 元素数量大于 5
})
```

### [#](#page-data) page.data

> 传递数据路径 automator 0.6.0，基础库 2.9.0 开始支持。

获取页面渲染数据。

```
page.data(path?: string): Promise<Object>
```

**参数说明**

| 字段 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| path | string | 否 | - | 数据路径 |

示例代码：

```
automator.launch().then(async miniProgram => {
  const page = await miniProgram.currentPage()
  console.log(await page.data('list'))
})
```

### [#](#page-setData) page.setData

设置页面渲染数据。

```
page.setData(data: Object): Promise<void>
```

**参数说明**

| 字段 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| data | Object | 是 | - | 要改变的数据 |

示例代码：

```
automator.launch().then(async miniProgram => {
  const page = await miniProgram.currentPage()
  await page.setData({
    text: 'changed data'
  })
})
```

### [#](#page-size) page.size

获取页面大小。

```
page.size(): Promise<Object>
```

**返回值说明**

| 字段 | 类型 | 说明 |
| --- | --- | --- |
| width | number | 页面可滚动宽度 |
| height | number | 页面可滚动高度 |

示例代码：

```
automator.launch().then(async miniProgram => {
  const page = await miniProgram.currentPage()
  const { width, height } = await page.size()
  console.log(width, height)
})
```

### [#](#page-scrollTop) page.scrollTop

> automator 0.7.0 开始支持。

获取页面滚动位置。

```
page.scrollTop(): Promise<number>
```

示例代码：

```
automator.launch().then(async miniProgram => {
  const page = await miniProgram.currentPage()
  await miniProgram.pageScrollTo(20)
  console.log(await page.scrollTop())
})
```

### [#](#page-callMethod) page.callMethod

调用页面指定方法。

```
page.callMethod(method: string, ...args: any[]): Promise<any>
```

**参数说明**

| 字段 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| method | string | 是 | - | 需要调用的方法名 |
| ...args | array<any> | 否 | - | 方法参数 |

示例代码：

```
automator.launch().then(async miniProgram => {
  const page = await miniProgram.currentPage()
  await page.callMethod('onShareAppMessage')
})
```

Incorrect translation.