# Skill: 设计 Agent 规则体系

- 触发场景: 需要为 agent 项目建立规则体系和文件管理规范时
- 步骤:
  1. 分析需要解决的问题（规则更新、任务记录、文档一致性、文件管理）
  2. 创建 `specs/rules-legacy.md`，头部版本号，分章节：规则管理、任务记录、变更联动、文件检查写�?  3. 创建 `specs/file-index.md`，登记所有文件的路径、作用、使用方�?  4. 更新原讨论文档，标记已决策的问题并引用规则文件章�?- 注意事项:
  - 规则文件保持精简（≤500行），超长说明该拆分
  - Skill 同时�?memory MCP �?`specs/skills/` 文件
  - 废弃文件不直接删除，移入 `process/archive/` 并标�?DEPRECATED
- 关联文件:
  - `specs/rules-legacy.md`
  - `specs/file-index.md`
  - `agent-interaction-optimization.md`


