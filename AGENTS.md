# 🤖 AI Agent 专用阅读与检索指南 (AGENTS.md)

> 本文件是专门为 AI Coding Agent (如 Cursor, Claude, Antigravity, GitHub Copilot, AutoGPT) 设计的仓库根入口。配置本文件的目的是帮助 Agent 在无需遍历全量 4400+ 文件的前提下，精确理解仓库索引结构并快速路由到目标文档。

---

## 🎯 仓库定位与使用原则

1. **仓库性质**: 微信小程序官方完整文档库（收录 4494 篇 `.md` 格式文档）。
2. **文档结构保护**: 原始文档目录结构（`介绍/`、`安全/`、`开发/`、`数据/`、`设计/`、`运营/`）保持原样未经修改。
3. **Agent 检索模式**:
   - **快速准确定位**: 优先通过 `doc-index.json` 进行 JSON 字段过滤或关键词匹配。
   - **大纲总览**: 读取 `llms.txt` 查看主要功能域映射。
   - **全量列表**: 读取 `llms-full.txt` 进行大视角上下文分析。

---

## 📂 目录路由规范 (Routing Rules)

| Agent 目标 query 领域 | 检索目标目录 | 常用 Tag 标记 |
| :--- | :--- | :--- |
| 小程序前端 JavaScript API (请求、位置、设备、界面等) | `开发/API/` | `API`, `开发` |
| 小程序 WXML UI 组件 (view, button, input, list 等) | `开发/组件/` | `组件`, `开发` |
| 微信云开发 (云函数、云数据库、云存储) | `开发/云服务/` | `云开发`, `开发` |
| 小程序后端 API (code2Session, AccessToken, 微信支付) | `开发/服务端/` | `服务端`, `开发` |
| 小程序框架语法 (生命周期、WXML/WXSS、双线程架构) | `开发/指南/` | `指南`, `开发` |
| AI 能力与高级平台能力 (人脸识别、音视频、无障碍) | `开发/平台能力/` | `开发` |
| 小程序审核规则、驳回原因、服务类目资质 | `运营/` | `运营`, `规范` |
| 数据埋点、统计接口与体验分析 | `数据/` | `数据` |
| 界面设计原则与 WeUI 视觉规范 | `设计/` | `设计` |
| 安全门禁、网关安全与代码加固 | `安全/` | `安全` |

---

## 🔑 微信小程序核心技术术语 (Key Domain Knowledge)

在回答用户关于微信小程序的问题或阅读文档时，请注意以下专有名词与技术概念：

- **双线程模型 (Dual-thread Architecture)**: 逻辑层 (AppService / JavaScript) 与渲染层 (WebView / Skyline) 隔离运行。
- **WXML (WeiXin Markup Language)**: 微信小程序标签语言，用于描述页面结构。
- **WXSS (WeiXin Style Sheets)**: 微信小程序样式语言，支持 `rpx` (responsive pixel) 响应式单位。
- **wxs (WeiXin Script)**: 运行在渲染层的脚本语言，可提高页面交互性能。
- **code2Session**: 小程序前端调用 `wx.login()` 获取 `code` 后，服务端换取 `openid` 和 `session_key` 的标准接口。
- **云开发 (Base Cloud Development)**: 腾讯云为小程序提供的免运维 Serverless 解决方案（云函数、云数据库、云存储）。
- **Skyline 渲染引擎**: 微信小程序推出的新一代高性能渲染引擎（替代传统 WebView 渲染）。

---

## 🛠️ 针对 Agent 的建议操作命令 (Recommended Agent Tools)

1. **精准搜索特定文档**:
   ```bash
   grep -i "wx.request" doc-index.json
   ```
2. **全文搜索特定 API**:
   ```bash
   grep -rn "wx.getLocation" 开发/API/
   ```
3. **查阅 JSON 索引全量列表**:
   直接解析根目录下的 `doc-index.json`。

---

> **版本标识**: Modern Agent Optimized Standard v1.0
