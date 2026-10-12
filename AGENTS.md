# AI Agent 阅读与检索指南

本仓库收录微信小程序官方文档，按独立网页去重后共有 3,852 篇完整 Markdown 页面。

## 检索入口

- [llms.txt](llms.txt)：主要功能域与阅读建议。
- [INDEX.md](INDEX.md)：分类导航与文档数量。
- [doc-index.json](doc-index.json)：机器可读索引。`total_pages` 为页面总数，`files` 为相对路径字符串列表，`description` 为索引说明。
- [llms-full.txt](llms-full.txt)：文档路径与摘要映射。

优先从 `doc-index.json` 的 `files` 列表筛选路径，再读取对应 Markdown 文件；需要按内容检索时使用 `rg`。检索结果以完整文档页面为单位，页面内章节通过 Markdown 标题定位。

## 目录路由

| 查询领域 | 目标目录 |
| :--- | :--- |
| 小程序背景、接入与客服 | `介绍/` |
| 前端 JavaScript API | `开发/API/` |
| WXML 组件 | `开发/组件/` |
| 生命周期、WXML/WXSS 与框架模型 | `开发/指南/` |
| 云函数、云数据库与云存储 | `开发/云服务/` |
| 服务端登录校验与后台 API | `开发/服务端/` |
| AI 与高级平台能力 | `开发/平台能力/` |
| 数据统计、埋点与体验分析 | `数据/` |
| 视觉规范、交互与无障碍设计 | `设计/` |
| 安全门禁、微信网关与数据安全 | `安全/` |
| 审核、运营规范与服务条款 | `运营/` |

## 维护约定

保留六大文档目录的官方内容与分类结构。更新文档清单时同步维护索引与导航中的数量和路径，避免为页面锚点创建重复文件。

提交前运行 `.github/workflows/lint-and-validate.yml` 中的校验命令，确认 JSON 能被解析，并保留 `AGENTS.md`、`INDEX.md`、`llms.txt` 与 `llms-full.txt` 四个核心入口文件。
