# [#](#string-CacheManager-addRule-string-RegExp-Record-string-any-rule) string CacheManager.addRule(string|RegExp|Record.<string, any> rule)

> 基础库 2.24.0 开始支持，低版本需做[兼容处理](../../../framework/compatibility.html)。

> **小程序插件**：不支持

> 相关文档: [弱网体验优化](../../../framework/performance/weak-network.html)

## [#](#功能描述) 功能描述

添加规则。

## [#](#参数) 参数

### [#](#string-RegExp-Record-string-any-rule) string|RegExp|Record.<string, any> rule

规则

## [#](#返回值) 返回值

### [#](#string) string

规则 id

## [#](#规则说明) 规则说明

支持的规则写法有字符串、正则和对象三种：

### [#](#字符串写法) 字符串写法

1. `addRule('/abc')`：纯 uri 串。
2. `addRule('GET /abc')：带方法的 uri 串，除了匹配 uri 外，还会匹配请求方法。如例子中必须是 GET 方法请求才会被匹配。
3. `addRule('/abc/:id')：带可变部分的 uri 串，id 可以是任意符合标准的字符串，表示这一段可以动态变化。比如`/abc/123`和`/abc/321`都会被匹配，而`/abc/123/xxx` 因为多了一段，就不会被匹配。
4. `addRule('/abc?aa')：带 query 参数的 uri 串，包含 aa 参数，值可以为任意值。比如`/abc?aa=haha`会被匹配，但是`/abc`就不会被匹配，因为缺少规则中声明的 aa 参数；不过如果请求是`/abc?aa=haha&bb=123`，虽然多带了 bb 参数，但是因为包含了 aa 参数，所以也可以被匹配。
5. `addRule('/abc?dd=haha')：带 query 参数的 uri 串，包含 dd 参数且值为 haha。比如`/abc?dd=haha`和`/abc?dd=haha&bb=123`会被匹配，而`/abc?dd=123` 就不会被匹配，因为规则要求了 dd 参数的值。

> 以上写法中的 uri 串如果只有 path 部分，则会取全局 origin 进行补全。比如全局 origin 是 `https://weixin.qq.com`，而规则是 `/abc`，则会补全为 `https://weixin.qq.com/abc`。因此在前面例子中 `addRule('/abc')` 和 `addRule('https://weixin.qq.com/abc')` 的写法效果一致。所以一般情况下如果需要匹配的请求 origin 和全局 origin 一致，则规则中可忽略不写 orign。

### [#](#正则写法) 正则写法

1. `addRule(/\/(abc|cba)$/ig)`：直接正则匹配请求的 uri，同时会比对请求 origin 和全局 origin 是否一致。
2. `addRule(/^https:\/\/weixin.qq.com\/(abc|cba)$/ig)`：带有 orign 部分的正则表达式，则只匹配 uri，不再比对 origin。

### [#](#对象写法) 对象写法

使用规则对象，可以更为详细的描述规则内容。（一般使用规则对象，是为了匹配请求参数）

#### [#](#规则对象：) 规则对象：

| 属性名 | 类型 | 默认值 | 备注 |
| --- | --- | --- | --- |
| id | string |  | 规则 id，如果不填则会由基础库生成 |
| method | string |  | 请求方法，可选值 GET/POST/PATCH/PUT/DELETE，如果为空则表示前面提到的所有方法都能被匹配到 |
| url | any | 必填 | uri 匹配规则，可参考规则字符串写法和正则写法 |
| maxAge | number | 7 \* 24 \* 60 \* 60 \* 1000 | 缓存有效时间，单位为 ms，不填则默认取缓存管理器全局的缓存有效时间 |
| dataSchema | Array<DataRule> |  | 匹配请求参数 |

其中，dataSchema 用来匹配对象类型的请求参数（比如 wx.request 的 data），默认可以不填，即不做参数匹配。

dataSchema 的类型是一个 DataRule 对象数组，一个 DataRule 对象描述一个参数，比如一个 wx.request 请求的 data 是 `{a: 123, b: 'haha', c: true}`，你想要用一条规则来匹配其中的 a 和 b 参数，如果 a 是数字且 b 是字符串就能命中该规则，那么就需要在 dataSchema 中补充两个 DataRule 对象，即 `[{name: 'a', schema: {type: 'number'}}, {name: 'b', schema: {type: 'string'}}]`。

#### [#](#DataRule-对象：) DataRule 对象：

| 属性名 | 类型 | 默认值 | 备注 |
| --- | --- | --- | --- |
| name | string |  | 需要匹配的参数名 |
| schema | DataSchema/Array<DataSchema> | 需要匹配的参数模式，支持数组，表示该参数值有多种模式 |  |

name 表示要匹配的参数名，schema 为 DataSchema 对象，用来描述该参数的类型和值。

一个 DataRule 对象也可以匹配可能拥有多种类型的参数，所以 schema 也支持为 DataSchema 对象数组。比如上述例子中，希望匹配的 a 参数必须是数值或者字符串，那么可以这么写：`{name: 'a', schema: [{type: 'number'}, {type: 'string'}]}`。

#### [#](#DataSchema-对象：) DataSchema 对象：

| 属性名 | 类型 | 默认值 | 备注 |
| --- | --- | --- | --- |
| type | string |  | 需要匹配的 data 对象的参数类型，string、number、boolean、null、object、any（表示任意类型），同时支持数组模式（数组模式则在类型后面加 []，如 string[] 表示字符串数组） |
| value | string/regexp/function/Array<DataRule> |  | 需要匹配的 data 对象的参数值，当 type 为基本类型时，可以用 string/regexp 来匹配固定的值，也可以通过 function 来确定值是否匹配，如果传入的 type 是 object，那么表示需要嵌套匹配值是否正确，可以传入 Array |

type 参数表示要匹配的参数类型，value 表示要匹配的参数值。其中 value 支持多种写法，不同写法有如下匹配方式：

1. 字符串写法：直接判值的字符串形式是否和给定字符串一样，比如 value 值为 `123`，就要求参数值必须为 123 才能与之匹配。
2. 正则写法：直接判值的字符串形式是否能被正则匹配，比如 value 值为 `/\d+/ig`，就要求参数值必须为数字，如果参数值为 `abc` 则不会被匹配。
3. 函数写法：在匹配时会调用用户传入的函数，交由用户判断是否匹配。
4. DataRule 数组写法：当参数类型为对象时，那么字符串写法和正则写法就无法使用，需要传入 DataRule 数组来进行匹配，即通过嵌套 DataRule 数组的方式来匹配嵌套的对象。

### [#](#示例代码) 示例代码

```
const ruleId = cacheManager.addRule({
  id: 'haha-rule',
  method: 'GET',
  url: '/haha',
  maxAge: 123455,
  dataSchema: [
    // data 字段的匹配，默认为空，表示不匹配
    // 类型可以是：string、number、boolean、null、object、any（表示任意类型均可），以及这些类型的数组表示方式
    {name: 'aaa', schema: {type: 'string'}}, // 类型为 string
    {name: 'bbb', schema: [{type: 'number'}, {type: 'string'}]}, // 类型为 number, string
    {name: 'ccc', schema: {type: 'string', value: 'abc'}}, // 值为 abc
    {name: 'ddd', schema: {type: 'string', value: /(abc|cba)/ig}}, // 值符合该正则匹配，如果该值不是字符串类型，则会被尝试转成字符串后再进行比较
    {name: 'ddd', schema: {type: 'string', value: val => val === '123'}}, // 传入函数来校验值
    {name: 'eee', schema: {type: 'object', value: [{ // 类型为对象，则通过嵌套的方式来逐层校验
      name: 'aaa', schema: {type: 'string'},
      // ...
      // 嵌套 dataSchema，同上面的方式一样来匹配嵌套的对象
    }]}},
    {name: 'fff', schema: {type: 'string[]'}}, // 类型为 string 数组
    {name: 'ggg', schema: {type: 'any'}}, // 类型为任意类型
    {name: 'hhh', schema: {type: 'any[]'}}, // 类型为任意类型的数组
  }],
})
```

### [#](#补充说明) 补充说明

用户可以添加多条规则，每条规则都会去解析网络请求，然后判断是否命中规则。假设有多条规则命中，则取第一条命中的规则。

### [#](#缓存覆盖) 缓存覆盖

不同的网络请求也可能命中同一条规则，所以每条规则可能对应多个缓存。每条规则会有一个规则 id，每个缓存会有一个缓存 id，一个规则 id 可能对应多个缓存 id，而缓存管理器的缓存存储是基于缓存 id 标识的，如果两个不同的请求生成了同样的缓存 id，那么后发生的请求结果缓存会覆盖前者。因此使用时需要思考缓存的覆盖情况，目前缓存 id 生成方式如下：

1. 规则使用字符串写法：那么按 method + url + 规则中声明的 query 参数来生成缓存 id。

> 需要注意的是这里不使用真实请求中的 query 参数来生成缓存 id，而是使用规则中匹配到的 query 来生成缓存 id。比如规则是 `/abc?aa=123`，请求是 GET 方法的 `/abc?aa=123&bb=123`，那么就会基于 `GET /abc?aa=123` 来生成缓存 id。而规则里没有声明 `bb=123`，所以 bb 参数不会被纳入缓存 id 的生成基准。

2. 规则使用正则写法：那么只按 method + url 生成缓存 id，不考虑 query 参数。
3. 规则使用对象写法：如果规则对象中的 url 是字符串写法，那么按 method + url + 规则中声明的 query 参数 + 规则中 dataSchema 声明的请求参数来生成缓存 id；如果规则对象中的 url 是正则写法，那么按 method + url + 规则中 dataSchema 声明的请求参数来生成缓存 id。

> 生成缓存 id 时没有使用请求中完整的 query 参数或者请求参数来作为基准，是考虑到很多请求可能会带上 token 或时间戳等参数。因为此参数存在不确定性，会导致每次请求生成的缓存 id 都不同，进而导致缓存命中率下降，故采取规则中声明的 query 参数和 dataSchema 声明的请求参数来作为生成缓存 id 的基准。

Incorrect translation.