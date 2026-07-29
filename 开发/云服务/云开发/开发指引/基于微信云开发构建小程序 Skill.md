# [#](#基于微信云开发构建小程序-Skill) 基于微信云开发构建小程序 Skill

本文介绍如何使用微信云开发作为后端，快速开发一个小程序 SKILL。

使用云开发后，您无需编写 `wx.request`、无需自行搭建服务器、也无需维护登录态——通过 `wx.cloud.callFunction` 即可直连云函数，用户身份 `OPENID` 由云开发的免鉴权能力自动注入。

本文假设您已了解 [AI 开发模式](https://developers.weixin.qq.com/miniprogram/dev/ai/guide) 以及小程序 SKILL 的四件套（`mcp.json` / `SKILL.md` / `index.js` / 组件），因此将聚焦于一件事：如何将"调用自建后端"替换为"调用云开发"，以及由此带来的开发简化。

全文以一个 **TODO 待办清单** SKILL 为例贯穿讲解。

---

## [#](#云开发能为您省去哪些工作) 云开发能为您省去哪些工作

在常规的 SKILL 开发中，原子接口需要通过 `wx.request` 调用自建后端，并额外编写登录中间件（`wx.login` → 换取 token → `setStorage` → 服务端 `code2session`）。改用云开发后，这些工作可以大幅简化：

| 常规做法 | 使用云开发 |
| --- | --- |
| `wx.request` 调用自建 HTTP 后端 | `wx.cloud.callFunction` 调用云函数 / `wx.cloud.database` 直连云数据库 |
| 在中间件中 `wx.login` + 换取 token + `setStorage` | 无需处理，云函数中 `getWXContext().OPENID` 直接获取 |
| 自行搭建服务器、配置域名、部署 HTTPS | 云函数 + 云数据库 + 云存储，开箱即用 |

> 适用前提：云开发相关 API 仅在**原子接口环境**可用（`wx.cloud.init` / `wx.cloud.callFunction` / `wx.cloud.database`），**原子组件环境暂时不支持**。因此请将所有数据获取放在原子接口中完成，组件仅负责渲染。

---

## [#](#前置准备) 前置准备

- 一个已申请「开发模式」权限的小程序 AppID
- 微信开发者工具 Nightly 版，基础库版本 ≥ `3.16.1`
- 已开通**微信云开发**环境，并记录环境 ID（形如 `your-env-xxxxxx`）。开通方式请参阅[微信云开发快速开始](basis/getting-started)

---

## [#](#第-1-步：创建独立分包并声明-SKILL) 第 1 步：创建独立分包并声明 SKILL

SKILL 需放置在独立分包中。请在 `app.json` 中按如下方式配置：

```
{
  "lazyCodeLoading": "requiredComponents",
  "cloud": true,
  "subPackages": [
    { "root": "skills/todo-skill", "independent": true, "pages": [] }
  ],
  "agent": {
    "skills": [
      { "name": "todo", "description": "待办清单业务", "path": "skills/todo-skill" }
    ]
  }
}
```

目录结构如下（接口实现直接写在 `index.js` 中，组件统一放在 `components/` 目录下）：

```
skills/todo-skill/
├── mcp.json                    # 接口与组件声明
├── SKILL.md                    # 业务流程编排
├── index.js                    # 初始化云开发 + 实现并注册所有接口
└── components/
    └── todo-card/              # 原子组件：仅负责渲染，不涉及网络请求
        ├── index.js
        ├── index.json
        ├── index.wxml
        └── index.wxss
```

---

## [#](#第-2-步：声明能力（mcp-json）) 第 2 步：声明能力（mcp.json）

`mcp.json` 用于向 AI 声明"提供了哪些接口、参数如何填写、使用哪张卡片展示"。其中 `description` 与参数说明的写法，将直接影响 AI 能否选对接口、填对参数。请务必在参数说明中写清"取值来源"与"缺失时的处理方式"，并明确禁止编造：

```
{
  "apis": [
    {
      "name": "addTodo",
      "description": "新增一条待办事项。当用户说『记一下/帮我记/加个待办』并给出具体内容时调用。",
      "_meta": { "ui": { "componentPath": "components/todo-card/index" } },
      "inputSchema": {
        "type": "object",
        "properties": {
          "title": {
            "type": "string",
            "description": "待办内容，取自用户原话（如『买牛奶』）。用户未说出具体内容时禁止填写，应反问『您要记什么待办？』。"
          }
        },
        "required": ["title"]
      }
    },
    {
      "name": "listTodos",
      "description": "查看当前用户的全部待办清单。当用户说『看看我的待办/还有什么没做』时调用，无需任何参数。",
      "_meta": { "ui": { "componentPath": "components/todo-card/index" } },
      "inputSchema": { "type": "object", "properties": {} }
    },
    {
      "name": "completeTodo",
      "description": "把一条待办标记为已完成。",
      "_meta": { "ui": { "componentPath": "components/todo-card/index" } },
      "inputSchema": {
        "type": "object",
        "properties": {
          "todoId": {
            "type": "string",
            "description": "待办唯一标识，必须来自上游 listTodos 返回的 todoId 原值。禁止编造，也禁止从用户自然语言推断；上下文无可用 todoId 时应先调 listTodos。"
          }
        },
        "required": ["todoId"]
      }
    }
  ],
  "components": [
    { "path": "components/todo-card/index", "relatedPage": "/pages/index/index" }
  ]
}
```

> 三个接口共用同一张 `todo-card` 卡片进行渲染；`relatedPage` 为卡片右上角"进入小程序"入口所关联的页面，请填写您小程序中对应的待办页路径。

---

## [#](#第-3-步：编排业务流程（SKILL-md）) 第 3 步：编排业务流程（SKILL.md）

`SKILL.md` 是面向 AI 的业务级说明书，用于描述跨接口的流程、依赖与约束。请勿在其中重复 `mcp.json` 中单个接口的参数说明：

```
# 待办清单 SKILL

帮助用户用自然语言管理个人待办：新增、查看、标记完成。

## 业务流程

用户意图
  ├─ 新增（"记一下…""帮我加个待办"）---> addTodo --> 待办清单卡片
  ├─ 查看（"看看我的待办""还有啥没做"）--> listTodos --> 待办清单卡片
  └─ 完成（点击卡片某条 / "把买牛奶标记完成"）> completeTodo --> 刷新清单卡片

## 业务约束（铁律）

- completeTodo 的 todoId 必须来自 listTodos 返回的原值，禁止编造或从用户措辞推断；
  上下文中没有可用 todoId 时，先调 listTodos 让用户从卡片中点选。
- 任何接口返回 isError=false 才算成功，未成功前禁止向用户宣布"已添加/已完成"。
- 新增或完成后，都应展示最新的待办清单卡片，禁止用纯文本罗列待办。

## 意图分流

- 用户给出具体内容 → addTodo；只说"记一下"未给内容 → 先反问要记什么。
- 用户表达模糊（如"那个"）→ 先反问澄清，禁止猜测。
```

---

## [#](#第-4-步：在-index-js-中初始化云开发并实现接口) 第 4 步：在 index.js 中初始化云开发并实现接口

`index.js` 运行在原子接口环境中。完成 `wx.cloud` 初始化后，您可以直接在此实现接口逻辑并就地注册：

```
// skills/todo-skill/index.js
wx.cloud.init({ env: 'your-env-xxxxxx' })

const skill = wx.modelContext.createSkill('skills/todo-skill')

// 添加待办：写操作走云函数（OPENID 由云开发自动注入，无需登录）
skill.registerAPI('addTodo', async ({ title }) => {
  if (!title) return { isError: true, content: [{ type: 'text', text: '缺少待办内容，请反问用户要记什么，禁止编造。' }] }

  const { result } = await wx.cloud.callFunction({ name: 'addTodo', data: { title } })
  return {
    content: [{ type: 'text', text: `已添加「${title}」，请展示最新待办清单卡片。` }],
    structuredContent: { todos: result.todos }
  }
})

// 查看待办：只读，直接连云数据库
skill.registerAPI('listTodos', async () => {
  const { data } = await wx.cloud.database().collection('todos').orderBy('createTime', 'desc').get()
  return {
    content: [{ type: 'text', text: `共 ${data.length} 条待办，请展示清单卡片，禁止纯文本罗列。` }],
    structuredContent: { todos: data.map(t => ({ todoId: t._id, title: t.title, done: t.done })) }
  }
})

// 完成待办：写操作走云函数
skill.registerAPI('completeTodo', async ({ todoId }) => {
  if (!todoId) return { isError: true, content: [{ type: 'text', text: 'todoId 须来自 listTodos 返回值，禁止编造。' }] }

  await wx.cloud.callFunction({ name: 'completeTodo', data: { todoId } })
  return { content: [{ type: 'text', text: '已标记完成，请刷新待办清单卡片。' }] }
})

module.exports = skill
```

几点说明：

- `content` 建议采用"陈述事实 + 指示下一步"的两段式写法，避免使用缺少上下文的裸指令。
- 无需再编写 `wx.login` 登录中间件；若需统一上报或错误监听，可使用 `skill.use(...)`。
- `listTodos` 属于只读场景，直接连接云数据库即可；而写操作（addTodo / completeTodo）一律通过云函数完成校验，详见[安全要点](#安全要点)。

---

## [#](#第-5-步：身份认证——交由云开发免鉴权处理) 第 5 步：身份认证——交由云开发免鉴权处理

云开发的一项重要能力在于：调用云函数时，微信会自动将当前用户身份注入云函数上下文，**小程序端无需登录，也无需传递 openid**。

- 小程序端：直接调用 `wx.cloud.callFunction`，无需（也不应）传入 `openid`。
- 云函数端：通过 `cloud.getWXContext().OPENID` 即可获取当前用户身份。

注意：AI 生成的参数**不可信任**。免鉴权能力解决的是"用户是谁"，而"某条 todoId 是否属于该用户"仍需在云函数中进行**所有权 / 越权校验**（详见[安全要点](#安全要点)）。

---

## [#](#第-6-步：编写云函数（您的后端逻辑）) 第 6 步：编写云函数（您的后端逻辑）

云函数即标准的云开发云函数，SKILL 不对其做任何介入。在云函数中，用户身份可直接获取，数据库也可直接读写：

```
// cloudfunctions/addTodo/index.js
const cloud = require('wx-server-sdk')
cloud.init({ env: cloud.DYNAMIC_CURRENT_ENV })
const db = cloud.database()

exports.main = async (event) => {
  const { OPENID } = cloud.getWXContext()
  const title = String(event.title || '').slice(0, 100)   // 服务端二次校验
  if (!title) return { code: 1, msg: '内容为空' }

  await db.collection('todos').add({ data: { _openid: OPENID, title, done: false, createTime: db.serverDate() } })
  const { data } = await db.collection('todos').where({ _openid: OPENID }).orderBy('createTime', 'desc').get()
  return { code: 0, todos: data.map(t => ({ todoId: t._id, title: t.title, done: t.done })) }
}
```

```
// cloudfunctions/completeTodo/index.js
const cloud = require('wx-server-sdk')
cloud.init({ env: cloud.DYNAMIC_CURRENT_ENV })
const db = cloud.database()

exports.main = async (event) => {
  const { OPENID } = cloud.getWXContext()
  // where 同时带上 _openid，确保只能修改自己的待办（越权校验）
  await db.collection('todos').where({ _id: event.todoId, _openid: OPENID }).update({ data: { done: true } })
  return { code: 0 }
}
```

云函数的依赖管理与部署方式，请参阅[云函数文档](https://developers.weixin.qq.com/doc/oplatform/openApi/cloudbase-common/scf-management/api_getfuntionlist)。

---

## [#](#第-7-步：编写原子组件（仅负责渲染）) 第 7 步：编写原子组件（仅负责渲染）

组件环境**不支持** `wx.cloud`，其数据全部来自接口返回的 `structuredContent`。当用户点击某条待办时，通过代用户上行消息触发 `completeTodo`：

```
// skills/todo-skill/components/todo-card/index.js
Component({
  data: { todos: [] },
  lifetimes: {
    created() {
      this.ctx = wx.modelContext.getContext(this)
      this.ctx.on(wx.modelContext.NotificationType.Result, ({ result }) => {
        this.setData({ todos: (result.structuredContent || {}).todos || [] })
      })
    }
  },
  methods: {
    onTapTodo(e) {
      const { todoId, title } = e.currentTarget.dataset.todo
      this.ctx.sendFollowUpMessage({
        content: [
          { type: 'text', text: `完成「${title}」` },
          { type: 'api/call', data: { name: 'completeTodo', arguments: { todoId } } }
        ]
      })
    }
  }
})
```

```
<!-- skills/todo-skill/components/todo-card/index.wxml -->
<view class="card">
  <view wx:for="{{todos}}" wx:key="todoId" class="item {{item.done ? 'done' : ''}}"
        data-todo="{{item}}" bindtap="onTapTodo">
    {{item.done ? '[x]' : '[ ]'}} {{item.title}}
  </view>
</view>
```

skills/todo-skill/components/todo-card/index.json：

```
{ "component": true }
```

---

## [#](#安全要点) 安全要点

> 安全是云开发场景中最为关键的环节，请务必逐条落实。

1. **AI 参数不可信任**：原子接口与云函数均需校验参数的类型、范围与有效性（例如 `title` 是否非空、是否超出长度上限）。
2. **在云函数中执行所有权 / 越权校验**：免鉴权仅解决"用户是谁"，执行操作前应使用 `OPENID` 进行比对（在 `where` 条件中带上 `_openid`），避免误改他人数据。
3. **写操作一律通过云函数**：增、删、改均由云函数落库，禁止客户端直接连接数据库进行写入。
4. **只读直连需配套安全规则**：`listTodos` 这类客户端 `wx.cloud.database()` 直查场景，必须在[安全规则](guide/database/security-rules)中限定 `auth.openid == doc._openid`，否则可能读取到他人的待办。
5. **密钥仅存放于环境变量**：第三方密钥等敏感信息应存放于云函数环境变量中，切勿写入小程序端代码或接口返回值。

---

## [#](#一次完整的数据流) 一次完整的数据流

下面以「帮我记个待办：买牛奶」为例，串联本文涉及的各个角色：

sequenceDiagram
participant U as 微信用户
participant AI as 微信 AI 后台
participant IDX as Skills 原子接口（skills/todo-skill/index.js）
participant CF as 微信云开发 - 云函数
participant DB as 微信云开发 - 云数据库
participant CMP as Skills 原子组件（skills/todo-skill/components）
U->>AI: "帮我记个待办：买牛奶"
AI->>IDX: 调用 addTodo(title="买牛奶")
IDX->>CF: wx.cloud.callFunction('addTodo')
CF->>CF: getWXContext().OPENID 获取身份
CF->>DB: 写入 todos 集合
DB-->>CF: 返回最新待办清单
CF-->>IDX: 返回结果
IDX->>AI: 组装 { content, structuredContent } 回传
AI->>CMP: 下发渲染指令
CMP->>U: todo-card 渲染待办清单卡片
Note over U,DB: 更新待办（用户交互流程）
U->>CMP: 点击某条待办
CMP->>CF: sendFollowUpMessage 触发 completeTodo
CF->>CF: 校验 \_openid 身份
CF->>DB: 更新待办状态
DB-->>CF: 返回最新清单
CF-->>CMP: 返回结果
CMP->>U: 刷新待办卡片

至此，您只需编写三处代码：**原子接口（在 index.js 中调用云函数或直连数据库）、云函数（业务逻辑）、原子组件（渲染）**。

登录态、服务器与域名配置均无需操心，微信云开发已为您一并处理。

Incorrect translation.