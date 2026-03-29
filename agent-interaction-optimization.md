- prompt优化�?具体示例参�?`esp/sdkconfig-analysis/docs/prompt模板.md/home/cuiyiyi/esp/sdkconfig-analysis/docs/prompt模板.md`
    > * 关于输出要确定的要素: 输出内容 输出格式 输出路径
    > * 若不知道输出内容和格�?-> 需描述最终目的，让agent总结 [注意从人和agent角度考虑]
    > * 最好能有任务原因，要解决什么问题。若不能提炼直接扔任务背景给agent总结，注意review [目的:软性约�?减少理解偏差]
- 可行的agent项目文件结构示例
agent-project/
�?├── docs/                              �?【分析讨论文档】给人看的，记录分析过程和结�?�?  ├── 依赖关系类型影响分析.md
�?  ├── default_if详解与QA风险分析.md
�?  └── 任务方案.md                     �?【给人看�?大致执行方案，主导方向问题�?�?├── specs/                             �?【Agent 执行规范】给 agent 看的，定义怎么�?�?  ├── 规则.md                         �?规则约束[硬约束，可随时庚戌年，保证agent自觉应用更新后的规则]
�?  ├── 文件索引.md                     �?所有文件路径[所有agent会用到的文件/资源指路]
�?  └── prompt模板.md                  �?�?agent �?prompt 模板
�?├── plans/                             �?【执行计划】拆分的具体执行步骤和任务编�?�?  ├── plan.md                        �?【给agent看的 修改后的最终执行方�?技术执行细节�?�?  ├── phase1.md
�?  ├── phase2.md
�?  └── phase3.md
�?├── output/                            �?【分析结果】Agent 生成的正式输�?�?  ├── xxx/
�?  �?  ├── xxx.json                   �?【给agent看的�?�?  �?  ├── xxx.md                     �?【给人看的�?�?  �?  └── 
�?  ├── xxx/
�?  �?  ├── xxx.json
�?  �?  ├── xxx.md
�?  �?  └── 
�?  └── xxx/
�?      └──
�?├── process/                           �?【过程文档】Agent 生成的中间产物，后续可能复用
�?  ├── 
�?  ├── 
�?  ├── 
�?  └── 
�?└── validation/                        �?【验证】dry-run 和金丝雀验证
    ├── dry-run/
    �?  ├── dry_run_report.md            �?dry-run 结果报告
    �?  └── sample_configs/              �?少量样例配置用于人工审查
    └── canary/
        ├── canary_plan.md               �?金丝雀最小验证方�?        ├── canary_configs/              �?最小验证用的配置文�?        └── canary_result.md             �?验证结果
- specs/rules-legacy.md 写什�?�?**已决策，详见 `specs/rules-legacy.md` v1**
> ~~支持规则更新后agent及时应用~~
    - �?方案：规�?md 头部版本�?+ memory 版本比对；规则文件保持精简(�?00�?每次全量读取，约1-2k token可接�?> ~~任务完成后记录完成过程，作为后续参考~~
    - �?方案：完成后自动提炼 skill（memory MCP + specs/skills/）；决策过程写入 process/task-log
> ~~修改完成方式等各种时及时修改对应文档~~
    - �?方案：变更联动规则表，见 `specs/rules-legacy.md` §3
> ~~文件检查与写入规则~~
    - �?方案：内容去重、归属规则、引用决策规则，�?`specs/rules-legacy.md` §4


> 项目特定规则 [目的：让项目可以不用监视自动工作]
    > 




