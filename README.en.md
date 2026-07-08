# AI Collaboration Log Skill

[中文](README.md)

`ai-collaboration-log` is a Codex Skill for maintaining structured records of AI collaboration. It turns user prompts, AI reasoning summaries, concrete actions, and produced files into incremental Obsidian-friendly Markdown logs. It is useful for coursework, project retrospectives, AI usage evidence, verification logs, and multi-agent collaboration records.

## Use Cases

- Recording how AI was used for a course assignment or training project.
- Summarizing “user question + AI answer + AI actions/artifacts” in a structured format.
- Maintaining AI verification logs, collaboration logs, project retrospectives, or presentation notes.
- Distinguishing contributions from multiple AI agents or conversation windows in the same workspace.
- Turning AI assistance from an informal chat into a traceable learning or work record.

## Core Behavior

When triggered, the skill appends one entry per Q&A unit. Each entry includes:

1. **Inferred purpose**: what the user was likely trying to accomplish.
2. **Original user prompt**: the user’s key wording.
3. **AI answer summary**: the useful explanation, recommendation, reasoning, or correction.
4. **AI actions and artifacts**: files read, created, modified, verified, or synced.

Each entry also records:

- Time
- Agent
- AI model
- Conversation/window id or short label

## Default Log Names

If the user does not specify a target file:

- Chinese context: create or maintain `AI协作记录整理.md`
- English context: create or maintain `ai-collaboration-log.md`

If the log already exists, the skill preserves existing content and appends new entries at the end.

## Repository Layout

```text
ai-collaboration-log-skill/
├── SKILL.md
├── agents/
│   └── openai.yaml
├── README.md
├── README.en.md
└── LICENSE
```

## Installation

### Option 1: Copy to the Codex skills directory

Copy this repository into your Codex skills directory and name the folder `ai-collaboration-log`:

```powershell
Copy-Item -Recurse -Force . "$env:USERPROFILE\.codex\skills\ai-collaboration-log"
```

If you use `CODEX_HOME`, copy it to:

```text
%CODEX_HOME%\skills\ai-collaboration-log
```

### Option 2: Install with Skill Installer

If your Codex environment has Skill Installer enabled, install the skill from the GitHub repository path. Reopen or refresh your Codex session afterward so the skill metadata is loaded.

## Example Prompts

```text
Record this conversation in my AI verification log.
```

```text
Use AI Collaboration Log to append this exchange to my Obsidian note.
```

```text
Summarize my prompt, your answer, and the files you modified into ai-collaboration-log.md.
```

Example output:

```markdown
### 1. Document AI collaboration for optional assignment B

**Time**: 2026-07-08 11:28 (+08:00)
**Agent**: Codex
**Model**: GPT-5
**Conversation**: Current Codex desktop thread

**Inferred purpose**:
The user wanted to turn AI assistance during optional assignment B into a submit-ready learning record.

**Original user prompt**:
"Append all of our Q&A into the AI verification log..."

**AI answer summary**:
The AI organized the conversation into structured entries, emphasizing the user’s intent, answer highlights, generated files, and iteration process.

**AI actions and artifacts**:
- Read and analyzed the existing document structure.
- Incrementally updated `yrx-AI校验记录.md`.
- Preserved the existing format and appended new numbered entries.
```

## Design Principles

- **Incremental logging**: append new records without overwriting old ones.
- **One Q&A per entry**: use a user prompt plus AI response/actions as the basic unit.
- **Evidence-oriented**: record not only what AI said, but also what AI did.
- **Obsidian-friendly**: write Markdown that is easy to search, link, and review.
- **Multi-agent aware**: distinguish agents, models, and windows through metadata.

## Maintenance Tips

- If a course or project already has a required format, provide a sample log and the skill will follow it.
- If one conversation includes multiple tasks, ask the skill to split them into multiple entries.
- If the log is committed to Git, run any required secret scan before committing.

## License

This project is licensed under the terms described in the repository `LICENSE` file.
