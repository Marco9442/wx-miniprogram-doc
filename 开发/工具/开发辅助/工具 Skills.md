# [#](#开发者工具-Skills) 开发者工具 Skills

微信开发者工具为开发者的编程 Agent 开放一套可操作、可调试、可验证的小程序开发 Skills。

让编程 Agent 能在开发者工具内完成完整的小程序开发流程：打开项目、读取状态、调整配置、编译、操作模拟器、读取日志、定位问题、预览上传、管理云开发资源...

![](https://res8.wxqcloud.qq.com.cn/wxdoc/eb7b138f-0990-4306-81c9-848a37146b47.png)
> AI Agent 可以打开一个精简的模拟调试器，并完成一系列自主规划任务

## [#](#一、能力范围) 一、能力范围

开发者工具 Skills 提供以下能力：

- 项目窗口打开与关闭、项目列表管理
- 页面自动化（点击、输入、滚动、截图、断言）
- 运行时诊断（console、network、运行时信息、wx API 调试）
- 编译相关（单文件编译、构建 npm、模拟器刷新、打开指定页面）
- 预览与发布（推送手机预览、生成预览二维码、上传体验版）
- 云开发操作（云环境、云函数、云数据库、云存储）

## [#](#二、安装-Skills) 二、安装 Skills

在[开发者工具下载页](log#nightly) ，下载 Nightly Electron Build 2.02.2607032 及以上版本安装

安装工具后，打开终端，执行：

```
wechatide
```

复制输出的 Skill 路径，粘贴给你的 Agent。

![](https://res8.wxqcloud.qq.com.cn/wxdoc/5b4348dc-325b-4217-b25b-c31a45ff9243.png)

你也可以在开发者工具菜单栏 → 「导出开发者工具 Skill」→ 导出 skill → 导入你的 AI Agent。

![](https://res8.wxqcloud.qq.com.cn/wxdoc/5eb93385-c3d0-4614-a252-5352d6183e3d.png)

安装过程需注意以下几点：

1. 安装微信开发者工具后，会自动配置 `wechatide` 命令到系统 PATH 中，如果找不到命令，可重启资源管理器或重启电脑后再试。
2. Agent 首次连接时会带 `clientName` （一般是 Agent 的名字）弹窗要求授权，授权后该 `clientName` 后续自动通过。
3. 必须保证已登录微信开发者工具，未登录时大多数操作会受到限制。
4. **项目根目录需包含有效的 `project.config.json`**，且其中 `appid` 字段有效（空字符串、`"touristappid"` 视为无效）。

## [#](#三、开始项目) 三、开始项目

### [#](#方式-A：仅导入项目列表（不打开窗口）) 方式 A：仅导入项目列表（不打开窗口）

适用于先登记项目、后续再打开开发的场景：

```
wechatide -c <clientName> -t project_import --project <项目绝对路径>
```

- 路径已在列表中时返回 `alreadyImported: true`，不视为失败。
- 此操作不做 appid 权限预检，目录无效时由底层报错。

### [#](#方式-B：打开项目窗口（自动导入列表）) 方式 B：打开项目窗口（自动导入列表）

适用于需要立即在模拟器中运行项目的场景：

```
wechatide -c <clientName> -t project_open_window --project <项目绝对路径>
```

**调用前必须完成前置检查**：

1. 读取 `<项目绝对路径>/project.config.json`。
2. 确认 `appid` 存在且不为空，且不是 `"touristappid"`。
3. 若 `project.config.json` 不存在或 `appid` 无效：
   - 调用 `get_user_appids` 获取当前登录用户可管理的 AppID 列表。
   - 选择或提供有效 AppID。
   - 创建或补全 `project.config.json`。
4. 确认登录态有效后再执行 `project_open_window`。

`project.config.json` 最小配置示例：

```
{
  "appid": "wxxxxxxxxxxx",
  "projectname": "my-miniprogram",
  "compileType": "miniprogram",
  "libVersion": "latest",
  "setting": {
    "urlCheck": true,
    "es6": true,
    "enhance": true,
    "postcss": true,
    "minified": true
  }
}
```

## [#](#四、登录与状态检查) 四、登录与状态检查

会话开始时必须检查一次 DevTools 状态：

```
wechatide -c <clientName> -t check_devtools_status --skill-version <skillVersionFromSkillYaml>
```

其中 `<skillVersionFromSkillYaml>` 应读取当前 `miniprogram-dev-skill/skill.yaml` 中的 `version` 字段值，不要硬编码。

判断规则：

- 返回中有 `openid`：登录态正常，可继续。
- 返回中有 `warning`：本地 skill 版本与 DevTools 内置 skill 版本不一致，应按提示路径更新 skill 后重试。
- 无 `openid`：未登录，需触发扫码登录：

```
wechatide -c <clientName> -t scan_login
```

扫码完成后，再次调用 `check_devtools_status` 确认。未确认登录前不得执行其他工具。

## [#](#五、标准使用流程) 五、标准使用流程

确认环境就绪后，按任务意图选择对应 scene：

| 任务目标 | 选择 |
| --- | --- |
| 打开/关闭项目窗口、获取登录/AppID 信息、构建 npm | `skills/initializer/SKILL.md` |
| 管理项目列表（查询、导入、删除） | `skills/project-manager/SKILL.md` |
| 页面点击、输入、滚动、截图、断言 | `skills/automator/SKILL.md` |
| 查看 console/network、运行时诊断、模拟器刷新 | `skills/debugger/SKILL.md` |
| 编译、单文件校验、刷新模拟器、打开指定页面 | `skills/compiler/SKILL.md` |
| 推送预览、生成二维码、上传体验版 | `skills/previewer/SKILL.md` |
| 云环境、云函数、云数据库、云存储 | `skills/cloudbase-operator/SKILL.md` |

所有工具统一调用方式：

```
wechatide -c <clientName> -t <toolName> [flags...]
```

- `-c`：当前 agent 名称（如 `CodeBuddy`、`Claude`）。
- `-t`：工具名，使用下划线分隔（如 `project_open_window`、`automation_element_action`）。
- 参数使用 `--field value` 形式；`object` / `array` 类型字段通过 `--<field>-file path.json` 传递 JSON 文件。
- 工具参数以 `miniprogram-tools/references/tools.yaml` 中 `inputSchema` 为准，不要自行编造工具名或参数结构。

## [#](#六、常用操作示例) 六、常用操作示例

```
# 检查状态
wechatide -c CodeBuddy -t check_devtools_status --skill-version 0.1.18

# 导入项目到列表
wechatide -c CodeBuddy -t project_import --project C:/projects/my-miniprogram

# 打开项目窗口
wechatide -c CodeBuddy -t project_open_window --project C:/projects/my-miniprogram

# 编译并打开指定页面
wechatide -c CodeBuddy -t simulator_open_page --project C:/projects/my-miniprogram --page pages/index/index

# 刷新模拟器
wechatide -c CodeBuddy -t simulator_refresh --project C:/projects/my-miniprogram

# 截图
wechatide -c CodeBuddy -t automation_viewport_action --project C:/projects/my-miniprogram --action screenshot --wait-for-selector .submit-btn --path C:/output/screenshot.png

# 推送手机预览
wechatide -c CodeBuddy -t auto_preview --project C:/projects/my-miniprogram

# 读取 console 报错
wechatide -c CodeBuddy -t get_app_console_content --project C:/projects/my-miniprogram --command "grep -i error"

# 构建 npm
wechatide -c CodeBuddy -t buildnpm --project C:/projects/my-miniprogram
```

## [#](#七、Agent-使用时重要约束与提醒) 七、Agent 使用时重要约束与提醒

1. **不要硬编码 skill 版本号**：`check_devtools_status` 的 `--skill-version` 必须来自当前 `skill.yaml` 的 `version` 字段。
2. **不要重复检查状态**：会话开始时调用一次 `check_devtools_status`，确认 `openid` 且无 `warning` 后，后续直接调用其他工具。
3. **不要编造工具名和参数**：工具名与参数结构以 `miniprogram-tools/references/tools.yaml` 为准。
4. **打开项目前必须先检查 `project.config.json` 与 `appid`**，否则 `project_open_window` 可能失败。
5. **涉及用户交互时必须停下等待**，包括授权弹窗、扫码、选择、确认窗口，不要在用户完成交互前声称已完成。
6. **写操作需用户确认**， `project_remove`、云数据库写操作、云存储上传/删除等会触发确认门，用户拒绝或超时后不要重试破坏性操作。
7. **云存储临时链接不是永久公开 URL**，仅用于当前任务，不要写入代码或长期文档。
8. **模拟器刷新成功不代表编译通过**，`simulator_refresh` 返回成功仅表示刷新动作已触发，需结合单文件编译工具验证。

当 Agent 发起以下任务请求时，会有明确弹窗提示：

- 危险操作（如云函数部署、体验版发布）会弹出明确确认对话框，需你授权后执行。
- 获取 AppID、云环境等敏感信息前，需你主动授权。
- 所有 Skill 调用均在本地开发者工具内完成，代码与日志不上传云端。

  ![](https://res8.wxqcloud.qq.com.cn/wxdoc/9a53a19a-9d16-44af-a63d-059fbee95d41.png)

## [#](#八、目录结构) 八、目录结构

- 根入口说明：`SKILL.md`
- 工具注册表：`miniprogram-tools/references/tools.yaml`
- 打开项目前置检查：`miniprogram-tools/references/open-project-window-guide.md`
- 创建项目流程：`miniprogram-tools/references/create-project-guide.md`
- 交互处理：`references/approval-policy.md`
- 安全边界：`SECURITY.md`
- 各 scene 详细说明：`skills/<scene>/SKILL.md`

## [#](#九、使用效果) 九、使用效果

##### [#](#场景一：云函数报错，AI-直接翻日志破案) 场景一：云函数报错，AI 直接翻日志破案

![](https://res8.wxqcloud.qq.com.cn/wxdoc/5bc0376b-722d-4cac-ad31-26bb8b68d336.png)
> 全程不用离开你的编辑器。

##### [#](#场景二：UI-验收，AI-自己-看-模拟器) 场景二：UI 验收，AI 自己"看"模拟器

![](https://res8.wxqcloud.qq.com.cn/wxdoc/b89b9804-db12-489d-96cf-838ec401a382.png)
> Agent 写完功能自己测试，你无需全程参与。

##### [#](#场景三：一句话需求，自动从-0-运行至手机) 场景三：一句话需求，自动从 0 运行至手机

![](https://res8.wxqcloud.qq.com.cn/wxdoc/2603e831-a2b1-4eb8-be6e-88b03ee35a21.png)
> Agent 自动完成代码编写、编译验证和真机预览全部过程。

##### [#](#场景四：自动截图分析布局) 场景四：自动截图分析布局

![](https://res8.wxqcloud.qq.com.cn/wxdoc/bb32163b-efd9-426b-82d3-8d36e17b90b6.png)
> Agent 自己找图看，不用你参与。

Incorrect translation.