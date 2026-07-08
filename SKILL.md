---
name: ai-collaboration-log
description: Organize and append AI collaboration records for coursework, reports, project retrospectives, Obsidian notes, and AI verification logs. Use when the user asks to record conversations with AI, summarize "my question + AI answer/action", create or update an AI校验记录 file, document how AI was used, capture iteration history across multiple agents/windows, or prepare evidence of AI-assisted learning and work.
---

# AI Collaboration Log

Maintain an incremental Obsidian-friendly log of user/AI collaboration. The log is not a raw transcript; it is a structured learning/work record that preserves the user's question, the inferred purpose, the AI's answer summary, and the AI's concrete actions/artifacts.

## Core Workflow

1. **Find or create the log**
   - If the user provides a target file, use it.
   - If no target is provided, create an Obsidian Markdown note in the current vault/workspace.
   - If the user's working language is Chinese, name the note `AI协作记录整理.md`.
   - If the user's working language is English, name the note `ai-collaboration-log.md`.
   - If a matching log already exists, append to it instead of creating a new file.

2. **Preserve existing content**
   - Read the existing log before editing.
   - Continue the existing heading style, numbering, tone, and person.
   - Append new entries at the end unless the user explicitly requests insertion elsewhere.
   - Do not rewrite or reorder prior entries unless asked.

3. **Use one entry per Q&A unit**
   - Treat each user question plus the AI's answer/actions as one unit.
   - If one user request produced several distinct work phases, split into subentries only when it improves readability.
   - Keep records concise but concrete; include enough detail to prove how AI was used.

4. **Include session metadata for multi-agent use**
   - At the top of each entry, include:
     - Time
     - Agent
     - Model
     - Conversation/window id or short label
   - If exact metadata is unavailable, write `未提供` / `unknown` rather than inventing it.
   - If the user provides a preferred label such as `Codex-1`, `ChatGPT网页`, or `窗口A`, use that label.

5. **Record four required sections**
   - `目的推测`: infer the user's goal behind the question.
   - `用户提问原文`: quote or lightly excerpt the user's original question.
   - `AI回答摘要`: summarize the useful answer, reasoning, recommendations, or corrections.
   - `AI行为和产出文件`: list concrete actions, file reads/writes, generated documents, modified paths, or verification steps.

## Entry Template

Use this template for Chinese logs:

```markdown
### N. 简短标题

**时间**：YYYY-MM-DD HH:mm（时区）
**Agent**：Codex / ChatGPT / 其他
**模型**：GPT-5 / 未提供
**对话窗口**：窗口A / thread-id / 未提供

**目的推测**：
用户希望……

**用户提问原文**：
“……”

**AI回答摘要**：
AI 主要说明……

**AI行为和产出文件**：
- 读取/分析了……
- 新建/修改了……
- 将结果同步到……
```

Use this template for English logs:

```markdown
### N. Short title

**Time**: YYYY-MM-DD HH:mm (timezone)
**Agent**: Codex / ChatGPT / other
**Model**: GPT-5 / unknown
**Conversation**: Window A / thread-id / unknown

**Inferred purpose**:
The user wanted to...

**Original user prompt**:
"..."

**AI answer summary**:
The AI explained...

**AI actions and artifacts**:
- Read/analyzed...
- Created/modified...
- Synced results to...
```

## Writing Rules

- Prefer first-person learning-retrospective style when the existing log uses it, e.g. `我要求 AI...`, `AI 帮我...`.
- Preserve key user wording in quotes, but do not paste entire long conversations unless requested.
- Summarize AI answers; do not dump full generated documents into the log.
- Include paths for important artifacts, especially files created or modified.
- Emphasize AI's role beyond answering: topic clarification, task decomposition, drafting, critique, risk review, misconception correction, final polishing, or record keeping.
- For coursework logs, explicitly connect the AI interaction to the assignment requirement or learning outcome.
- For multiple agents/windows, make entries distinguishable through metadata and avoid claiming one agent did work done by another.

## Duplicate Avoidance

Before appending:

1. Check the last few entries.
2. If the same Q&A is already logged, update the existing entry only when the user requests correction; otherwise do not duplicate.
3. If the new entry extends a previous topic, create a new numbered entry and mention the relationship.

## File Editing Guidance

- Use `apply_patch` for Markdown edits where possible.
- For files outside the writable workspace, request required approval or use an already approved command path if available.
- When updating a Git-tracked report before commit, follow any repository secret-scanning requirements from AGENTS.md or project instructions.

## Output to User

After updating the log, report:

- Which log file was updated or created.
- Which entry number/title was added.
- Any related files created or modified.
- Whether verification was performed.
