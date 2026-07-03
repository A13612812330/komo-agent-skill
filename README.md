# Komo Agent Skill

Komo Agent is a Chinese-first routing skill for Codex. It helps users describe a task in plain Chinese and routes the request to the most relevant installed skill, plugin, or MCP capability.

## Install

From this repository:

```bash
npx skills add <repo-url> --skill komo-agent
```

If installing manually, copy the full directory:

```text
skills/komo-agent/
```

to:

```text
%USERPROFILE%\.codex\skills\komo-agent
```

Then restart Codex.

## Expected Companion Capabilities

This skill works best when the user has related skills/plugins installed, such as:

- `context-engineering`
- `create-plan`
- `zh-fuzzy-router`
- `frontend-design`
- `frontend-skill`
- `presentations`
- `sn-ppt-entry`
- `sn-da-excel-workflow`
- `docx-processor`
- `image-utils`
- `archive-manager`
- `github`
- `product-design`
- `figma`
- `browser`
- `browser-testing`
- `playwright`

Missing companion skills are not fatal. Codex should fall back to the best available capability.

## Example Prompts

- 用我的agent处理这个新项目。
- 按我的工作流来，把这个 Excel 周报做成 PPT。
- 一句话处理这个前端页面优化。
- 帮我判断这个任务应该调用哪些已安装能力。

