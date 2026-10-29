---
name: komo-agent
description: >-
  Chinese-first master routing skill for Codex project work. Use when the user gives broad, casual, one-sentence, or mixed project requests and wants Codex to select the best installed skill, plugin, or MCP capability. Trigger phrases include 用我的agent, 用总控, 一句话处理, 按我的工作流来, 帮我直接开始这个项目, 按已安装能力处理, 用我装好的技能来做.
---

# Komo Agent

## Overview

Use this skill as a single routing entry for project work. Interpret casual Chinese requests, choose the most specific installed skill/plugin/MCP, follow confirmation rules for risky operations, and keep output concise.

## Core Rules

1. Prefer already installed skills, plugins, and MCP servers over manual implementation.
2. If the task is complex, risky, or clearly more than 3 steps, propose a short plan before execution.
3. If the task writes files, modifies files, deletes files, performs system actions, changes databases, performs authorization, or pushes to a remote repository, explain the action and wait for user confirmation.
4. Keep responses concise and use Chinese by default.
5. When multiple skills apply, choose the most specific one first and combine only what is necessary.
6. For new projects, start by identifying the project type, working directory, desired output, and whether GitHub backup is needed.

## Routing

- Excel, CSV, table analysis, charts, weekly report data -> `sn-da-excel-workflow`
- PPT, slides, weekly report deck, presentation updates -> `sn-ppt-entry` or `presentations`
- Weekly report PPT, project-summary PPT, PPT style optimization, dynamic page planning -> `komo-ppt-skill`
- Strict master PPT copy, replace text only, preserve approved layout -> `komo-ppt-skill` (`master-copy` mode)
- Word, contracts, reports, document formatting -> `docx-processor`
- Frontend, page polish, layout, UI, website visuals -> `frontend-design`, `frontend-skill`, or `frontend-polish-review`
- Browser preview, web testing, clicks, screenshots -> `browser`, `browser-testing`, `playwright`, or `screenshot`
- GitHub sync, backup, rollback, PR, issue, CI -> `github`, `gh-address-comments`, or `gh-fix-ci`
- Images, OCR, screenshots, crop, compress, convert -> `image-utils`
- Archives, zip, rar, 7z, pack, unpack -> `archive-manager`
- PDF tasks -> `pdf`
- Product requirements, PRD, UX, design thinking -> `product-design`
- Figma design files and design system work -> `figma`
- Video, motion, website-to-video -> `hyperframes-router` or `remotion`
- Survey cleaning, codebook, panel data, variable recoding -> `codebook-pass`
- Authorized crawling, endpoint discovery, website enumeration -> `katana-crawl`
- SQLite and local `.db` work -> `sqlite-mcp-server`
- Trend checks and hot-topic monitoring -> `hot-monitor`

For mixed Excel + PPT requests, use `komo-ppt-skill` as the primary workflow and combine `sn-da-excel-workflow` for data extraction when needed.

Before generating any PPT, the routed workflow must estimate the page count, show the page outline and ask the user to confirm or override the number of pages. Do not apply a fixed 3-page or 10-page limit.
When the user explicitly requests strict master replication, use the master page count and run structure comparison; do not redraw the layout.

If a routed skill is not installed, state that briefly and continue with the best available fallback.

## New Project Workflow

When the user starts a new project:

1. Identify the project type from the request.
2. Select the working folder or ask for it if missing.
3. Decide the primary skill stack and say which one will be used.
4. Ask for confirmation before any write, install, system, destructive, database, or remote repository action.
5. Offer GitHub backup before major milestones or large updates instead of auto-pushing by default.
6. After implementation, verify outputs and report file locations clearly.

## Example Requests

- 用我的agent把这个 Excel 周报做成 PPT。
- 先告诉我这份周报建议做多少页，再生成 PPT。
- 参考这个 PPT 优化样式，但保留数据可编辑。
- 把项目总结、周报数据和竞品分析合成一份 PPT。
- 按我的工作流来，整理这个新前端项目并直接开始。
- 帮我直接开始这个项目，先判断该用哪些已安装技能。
- 用我装好的技能来做这个网页优化。
- 一句话处理这份调查数据，按 codebook 清洗并输出报告。

## Safety

- Do not perform system-level operations, installs, file writes, deletions, database changes, authorization operations, or remote pushes without user confirmation.
- Do not expand a security or crawling task beyond the authorized target.
- Prefer the smallest working scope that can complete the request.
