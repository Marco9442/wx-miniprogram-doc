# 📱 微信小程序官方文档库 (AI Agent 优化版)

<p alias="badges">
  <img src="https://img.shields.io/badge/Documents-4400%2B-blue.svg?style=flat-square" alt="Doc Count" />
  <img src="https://img.shields.io/badge/AI_Agent-Optimized-brightgreen.svg?style=flat-square" alt="Agent Optimized" />
  <img src="https://img.shields.io/badge/Standard-llms.txt-orange.svg?style=flat-square" alt="llms.txt Standard" />
  <img src="https://img.shields.io/badge/License-MIT-green.svg?style=flat-square" alt="License" />
</p>

> 本仓库汇集微信小程序全量官方标准 Markdown 文档（共 4400+ 篇），经过现代化开源仓库标准重构与 AI Agent 专属优化。无论是人类开发者查阅，还是给 Cursor / Claude / Antigravity / AutoGPT / RAG 向量数据库读取，均能实现秒级检索与精准理解。

---

## 🌟 核心特色 (Highlights)

- 🤖 **AI Agent 专用优化**: 包含 [AGENTS.md](AGENTS.md) 系统阅读指引、[llms.txt](llms.txt) 标准索引、[llms-full.txt](llms-full.txt) 全量上下文与 [doc-index.json](doc-index.json) 机器可读元数据矩阵。
- 📚 **全量覆盖 4400+ 文档**: 包含介绍、安全、开发（API/组件/服务端/云开发/框架）、数据、设计、运营等完整生命周期体系。
- ⚙️ **现代化开源配置**: 配置完善的 GitHub Issue/PR 模板、GitHub Actions 自动校验流水线、MIT 开源协议与标准代码规范。
- 📂 **原始文档结构未被破损**: 严格保持官方 Markdown 目录分级，无缝兼容现有全量文档路径。

---

## 🧭 Agent 与开发者导航 (Navigation Guide)

### 🤖 对于 AI Agent / LLM
如果您是 AI Coding Agent，请阅读以下文件：
1. **[AGENTS.md](AGENTS.md)**: 了解本仓库目录路由规则、微信小程序核心术语词典与 Agent 搜索指导。
2. **[llms.txt](llms.txt)**: 遵循 [llmstxt.org](https://llmstxt.org) 规范的核心文档映射树。
3. **[doc-index.json](doc-index.json)**: 全量 4400+ 篇文档的结构化 JSON 索引表，支持快速搜索与向量化 Embeddings。

### 👨‍💻 对于开发者 (For Humans)
可以通过以下核心入口快速导航到指定领域：

| 领域分类 | 包含文件数 | 核心内容与入口 |
| :--- | :---: | :--- |
| 🚀 **开发 (Development)** | **3767** | [开发 API](开发/API/) \| [前端组件](开发/组件/) \| [云开发](开发/云服务/) \| [服务端 API](开发/服务端/) \| [开发指南](开发/指南/) |
| 📋 **运营 (Operations)** | **534** | [运营规范](运营/运营规范/) \| [开放类目](运营/开放的服务类目/) \| [服务条款](运营/服务条款/) |
| 介绍 (Introduction) | **67** | [小程序接入指南](介绍/小程序接入指南/) \| [客服功能指南](介绍/客服功能使用指南/) |
| 📊 数据 (Analytics) | **56** | [数据分析指南](数据/数据分析/) \| [体验分析](数据/体验分析/) |
| 🎨 设计 (Design) | **51** | [微信小程序设计指南](设计/微信小程序设计指南/) \| WeUI 视觉规范 |
| 🛡️ 安全 (Security) | **19** | [微信网关安全](安全/微信网关/) \| [安全门禁](安全/安全门禁.md) \| 数据加固 |

---

## 📁 目录结构矩阵 (Directory Structure)

```text
wx-miniprogram-doc/
├── AGENTS.md               # AI Agent 专属系统指令与路由指引
├── llms.txt                # LLM 标准大纲索引文件 (llmstxt.org)
├── llms-full.txt           # 全量 4400+ 文档路径与摘要列表
├── INDEX.md                # 分类导航矩阵
├── doc-index.json          # 结构化 JSON 索引库 (4400+ 文档元数据)
├── README.md               # 仓库项目主页
├── LICENSE                 # MIT 开源协议
├── .github/                # GitHub Issue / PR 模板与 Actions 工作流
│   ├── ISSUE_TEMPLATE/
│   ├── PULL_REQUEST_TEMPLATE.md
│   └── workflows/
├── 介绍/                   # 微信小程序背景与接入指南
├── 安全/                   # 网络、代码、数据与运营安全门禁
├── 开发/                   # API、组件、云服务、服务端接口、框架指南
├── 数据/                   # 埋点与数据分析接口
├── 设计/                   # WeUI 视觉与交互规范
└── 运营/                   # 审核规则、违规处理与服务类目要求
```

---

## 🛠️ 在 Cursor / Claude 中使用本仓库 (How to use with AI Agents)

1. **作为知识库关联**:
   在 Cursor 或 Claude 等工具中直接输入 `@AGENTS.md` 或 `@doc-index.json` 作为 Context 提示。
2. **检索具体 API**:
   例如向 Agent 提问：`"查看开发/API/网络/发起请求.md 中的 wx.request 示例"`。
3. **RAG 向量数据库构建**:
   直接解析 `doc-index.json` 即可快速提取所有文档的 `path`、`title`、`category` 和 `summary`。

---

## 🤝 贡献指南 (Contributing)

欢迎对本仓库的文档索引或配置提出改进方案！
1. Fork 本仓库并创建分支。
2. 提交您的改善 (例如修正错别字或优化 `AGENTS.md`)。
3. 发起 Pull Request。

---

## 📄 开源协议 (License)

本项目基于 [MIT License](LICENSE) 协议开源。文档原所有权归微信官方所有。
