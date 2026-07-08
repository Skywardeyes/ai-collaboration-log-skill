# AI 协作记录整理 Skill

[English](README.en.md)

`ai-collaboration-log` 是一个用于整理 AI 协作过程的 Codex Skill。它会把用户与 AI 的问答、AI 的判断、操作和产出文件，增量整理成 Obsidian 友好的 Markdown 记录，适合课程作业、项目复盘、AI 使用证明、AI 校验记录和多 Agent 协作留痕。

## 适用场景

- 课程或训练营要求记录“我如何使用 AI 完成任务”。
- 需要把“用户问题 + AI 回答摘要 + AI 行为和产出文件”整理成结构化记录。
- 需要持续维护 `AI校验记录`、`AI协作记录整理`、项目复盘或展示说明。
- 同一工作区里有多个 AI Agent、多个对话窗口，需要通过时间、Agent、模型、窗口编号区分来源。
- 想把 AI 从“临时问答工具”变成“可追踪的学习和工作协作者”。

## 核心功能

触发后，Skill 会按每次问答为单位追加记录。每条记录包含：

1. **目的推测**：根据用户问题推测用户真正想完成什么。
2. **用户提问原文**：保留用户的关键原话。
3. **AI 回答摘要**：概括 AI 给出的解释、建议、判断或修正。
4. **AI 行为和产出文件**：记录 AI 读取、创建、修改、验证过的文件或操作。

同时，每条记录会标注：

- 时间
- Agent
- AI 模型
- 对话窗口编号或简写

## 默认日志命名

如果用户没有指定目标文件：

- 中文语境下创建或维护 `AI协作记录整理.md`
- 英文语境下创建或维护 `ai-collaboration-log.md`

如果目标文件已存在，Skill 会保留原内容并在末尾增量追加，不会重写旧记录。

## 目录结构

```text
ai-collaboration-log-skill/
├── SKILL.md
├── agents/
│   └── openai.yaml
├── README.md
├── README.en.md
└── LICENSE
```

## 安装方式

### 方式一：复制到 Codex skills 目录

将本仓库复制到 Codex 的 skills 目录中，并确保目录名为 `ai-collaboration-log`：

```powershell
Copy-Item -Recurse -Force . "$env:USERPROFILE\.codex\skills\ai-collaboration-log"
```

如果你设置了 `CODEX_HOME`，则复制到：

```text
%CODEX_HOME%\skills\ai-collaboration-log
```

### 方式二：通过 Skill Installer 安装

如果你的 Codex 环境启用了 Skill Installer，可以从 GitHub 仓库路径安装该 skill。安装后，重新打开或刷新 Codex 会话，使 skill 元数据重新加载。

## 使用示例

用户可以这样触发：

```text
把这次问答整理进 AI 校验记录
```

```text
使用 AI 协作记录整理，把本轮对话追加到 Obsidian 日志
```

```text
将我刚才的问题、你的回答摘要、你修改过的文件同步到 AI协作记录整理.md
```

生成的记录示例：

```markdown
### 1. 整理选做题 B 的 AI 协作过程

**时间**：2026-07-08 11:28（+08:00）
**Agent**：Codex
**模型**：GPT-5
**对话窗口**：当前 Codex 桌面线程

**目的推测**：
用户希望把 AI 在选做题 B 中的辅助过程整理为可提交、可复盘的学习记录。

**用户提问原文**：
“把我们之间所有的问答……增量填入 AI 校验记录。”

**AI回答摘要**：
AI 将多轮问答归纳为结构化记录，突出问题目的、回答要点、文件产出和迭代过程。

**AI行为和产出文件**：
- 读取并分析既有文档结构。
- 增量更新 `yrx-AI校验记录.md`。
- 保留原有格式并追加新的编号条目。
```

## 设计原则

- **增量记录**：每次触发只追加新内容，避免覆盖已有记录。
- **一问一条**：以一次用户问题和 AI 回应为基本单位。
- **可证明过程**：不仅记录 AI 说了什么，也记录 AI 做了什么。
- **适配 Obsidian**：输出 Markdown，便于在 Obsidian 中检索、链接和复盘。
- **支持多 Agent**：通过元数据区分不同模型、窗口和 Agent 的贡献。

## 维护建议

- 如果课程或项目已有固定格式，可以先提供样例文件，Skill 会优先延续既有结构。
- 如果一次对话包含多个任务，可以要求 Skill 按任务拆分为多条记录。
- 如果涉及提交到 Git 仓库，提交前应按项目要求进行敏感信息检查。

## License

本项目使用仓库中的 `LICENSE` 文件所声明的许可证。
