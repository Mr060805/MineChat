# MineChat

> 开源 · 多模型 · 本地优先的 Android AI 聊天助手

**MineChat**（包名 `cn.mine.minestars`）是一款运行于 Android 平台的 AI 聊天客户端，支持接入主流的云端大模型服务，同时提供本地模型推理能力。你可以在一个应用里管理多个 AI 提供商、构建专属助手与角色卡，并用知识库、函数调用（MCP）、联网搜索、语音、翻译、图片生成等能力扩展它。

---

## ⚠️ 关于本项目（Fork 声明）

**本项目是 [RikkaHub](https://github.com/rikkahub/rikkahub)（[rikka-ai.com](https://rikka-ai.com)）的分支（Fork），基于 RikkaHub 2.2.5 版本二次开发。**

在此对 RikkaHub 及其贡献者表示诚挚感谢。本项目在其基础上进行了定制与扩展，具体改动可参考仓库内的 [`RIKKA_ALIGN_LOG.md`](./RIKKA_ALIGN_LOG.md)（上游更新适配日志）。

> 如需原始项目，请访问上游仓库：<https://github.com/rikkahub/rikkahub>

---

## 主要功能

- **多提供商 AI 接入**：内置 OpenAI、Gemini、DeepSeek、OpenRouter、硅基流动、阿里云百炼、火山引擎、月之暗面、智谱、OpenCode、Vercel AI Gateway 等，均支持 `OpenAI 兼容` 接口，也可自定义任意兼容端点；支持余额查询。
- **助手管理**：创建多个 AI 助手，自定义系统提示词、人设（Persona）、记忆、开场白、温度等参数，并可一键切换。
- **Tavern 兼容角色扮演**：支持 SillyTavern 生态的角色卡与 JSON 导入、世界书（World Book）、正则脚本（基于 Tavern 正则引擎），适用于角色扮演与创作场景。
- **语音能力**：多提供商 TTS（语音合成）与 ASR（语音识别）。
- **知识库 / RAG**：本地文档切分、向量化与检索增强生成。
- **函数调用 / MCP**：支持 Model Context Protocol，接入外部工具与数据源。
- **工作区（Workspace）**：内置终端（shell）、文件读写、代码编辑工具，AI 可直接在受控目录内操作文件。
- **联网搜索**：为模型提供实时联网检索能力。
- **翻译**：基于选定模型的多语言翻译。
- **AI 图片生成**：通过选定的图片生成模型生成图片。
- **本地模型推理**：通过 MNN 在设备端本地运行模型（离线可用）。
- **实用扩展**：预设（Preset）、快捷消息、技能（Skills）、标签、收藏、会话文件夹、统计面板等。
- **数据迁移**：支持导入 Chatbox 等第三方数据，以及完整的备份与导出。

---

## 技术栈

| 类别 | 技术 |
| --- | --- |
| 语言 | Kotlin |
| UI | Jetpack Compose + Material 3 |
| 架构 | 多模块 + MVVM |
| 依赖注入 | Koin |
| 本地存储 | Room（KSP）|
| 本地推理 | MNN（`libMNN.so`）|
| 最低/目标系统 | Android 8.0（minSdk 26）/ targetSdk 37 |
| JDK | 17 |

---

## 模块结构

| 模块 | 说明 |
| --- | --- |
| `app` | 主应用（`cn.mine.minestars`） |
| `ai` | AI 核心：提供商、模型、推理（含 MNN 本地推理）|
| `core:tavern` | Tavern / SillyTavern 兼容实现 |
| `core:workspace` | 工作区与终端 |
| `common` | 公共工具 |
| `search` | 联网搜索服务 |
| `speech` | TTS / ASR |
| `document` | 文档解析与处理 |
| `rag` | 知识库 / 检索增强生成 |
| `highlight` | 代码高亮 |
| `material3` | Material 3 定制（含 `material-color-utilities` 子模块）|

---

## 构建

### 环境要求

- Android Studio（最新稳定版）
- JDK 17
- CMake + NDK（如需构建 `ai` 模块的 MNN 本地库）

### 步骤

```bash
# 1. 克隆仓库（含子模块）
git clone --recursive https://github.com/Mr060805/MineChat.git
# 或：先克隆，再初始化子模块
# git clone https://github.com/Mr060805/MineChat.git
# cd MineChat && git submodule update --init --recursive

# 2. 使用 Android Studio 打开项目，同步 Gradle 后即可运行
```

> 生成的 `keystore.properties` / `keystore/` 等签名文件不会随仓库分发，发行版会回退使用 `debug` 签名；如需正式签名，请自行配置。

---

## 开源许可

本项目采用 [AGPL v3](https://www.gnu.org/licenses/agpl-3.0.html) 开源协议（另有商业授权选项，详见仓库内 [`LICENSE`](./LICENSE)）。

> 本项目基于 [RikkaHub](https://github.com/rikkahub/rikkahub) 修改，同样须遵守上游项目的许可条款。