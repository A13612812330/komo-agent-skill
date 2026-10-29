# Changelog

## 2026-10-29

- `README.md` 与 `SKILL.md` 同步 `komo-ppt-skill` 路由，补齐技能清单与示例请求。
- 新增混合 Excel + PPT 场景的主路由规则：以 `komo-ppt-skill` 为主流程，`sn-da-excel-workflow` 负责数据抽取。
- 新增生成前页数确认门禁：必须先给出页数建议与大纲，由用户确认或改写，不套用固定 3 页/10 页限制。
- 新增严格母版复制分支：按母版页数走结构比对，不重绘版式。

## 2026-07-13

- Added `komo-ppt-skill` as the primary route for project-summary PPT, weekly report PPT, PPT style optimization, and dynamic page planning.
- Added the page-count confirmation gate and mixed Excel + PPT routing rule.
- Added strict master-copy routing for approved PPT templates.
