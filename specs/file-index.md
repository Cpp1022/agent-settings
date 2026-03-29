# 文件索引

> Agent 工作前查阅本文件，了解项目中所有文件的位置、作用和使用方法�?> 新增/删除任何文件后必须同步更新此索引�?
---

## 项目结构总览

```
agent-settings/
├── agent-interaction-optimization.md          �?交互优化方案讨论（给人看的）
├── docs/                     �?分析讨论文档
├── specs/                    �?Agent 执行规范
�?  ├── 规则.md               �?Agent 硬约束规�?�?  ├── 文件索引.md           �?本文�?�?  └── skills/               �?可复用操作步骤记�?├── plans/                    �?执行计划
├── output/                   �?正式输出
├── process/                  �?过程文档与中间产�?�?  └── archive/              �?废弃文件归档
└── validation/               �?验证相关
```

---

## 文件详细索引

### 根目�?
| 文件 | 作用 | 使用方法 |
|------|------|---------|
| `agent-interaction-optimization.md` | 记录 agent 交互优化的方案讨论、项目文件结构示例、待解决问题 | 人阅读参考；agent 需要了解项目背景时读取 |

### specs/ �?Agent 执行规范

| 文件 | 作用 | 使用方法 |
|------|------|---------|
| `specs/rules-legacy.md` | Agent 硬约束规则，包含规则管理、任务记录、变更联动、文件写入等规范 | **每次任务开始前必须读取**，检查版本号是否有更�?|
| `specs/file-index.md` | 所有文件路径、作用与使用方法的索�?| 新增/删除文件后必须更新；不确定文件作用时查阅 |
| `specs/skills/` | 存放可复用操作步骤的 skill 文件 | 任务完成后自动生成；执行类似任务前搜索已�?skill |
| `specs/skills/design-agent-rules-system.md` | 建立规则体系和文件管理规范的操作步骤 | 新项目需要建�?agent 规范时参�?|

### docs/ �?分析讨论文档

| 文件 | 作用 | 使用方法 |
|------|------|---------|
| _（待项目补充）_ | 给人看的分析过程和结�?| 分析结论写入此目�?|

### plans/ �?执行计划

| 文件 | 作用 | 使用方法 |
|------|------|---------|
| _（待项目补充）_ | Agent 的技术执行步骤和任务编排 | agent plan 写入 `plans/plan.md` |

### output/ �?正式输出

| 文件 | 作用 | 使用方法 |
|------|------|---------|
| _（待项目补充）_ | Agent 生成的最终交付物 | �?|

### process/ �?过程文档

| 文件 | 作用 | 使用方法 |
|------|------|---------|
| _（待项目补充）_ | 中间产物和任务日�?| 决策日志写入 `process/task-log-{日期}-{摘要}.md` |
| `process/archive/` | 废弃文件归档 | 方案调整后旧文件移入此处，标�?`[DEPRECATED]` |

### validation/ �?验证

| 文件 | 作用 | 使用方法 |
|------|------|---------|
| _（待项目补充）_ | dry-run 和金丝雀验证 | �?|



---

## 2026-03-29 Incremental Update

| File | Purpose | Usage |
|------|---------|-------|
| `AGENTS.md` | Repository root enforcement entry, including hard "plan-before-execution" gate and rule references | Read first in each session; block execution if planning mode is active |
