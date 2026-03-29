- prompt优化点 具体示例参考 `esp/sdkconfig-analysis/docs/prompt模板.md/home/cuiyiyi/esp/sdkconfig-analysis/docs/prompt模板.md`
    > * 关于输出要确定的要素: 输出内容 输出格式 输出路径
    > * 若不知道输出内容和格式 -> 需描述最终目的，让agent总结 [注意从人和agent角度考虑]
    > * 最好能有任务原因，要解决什么问题。若不能提炼直接扔任务背景给agent总结，注意review [目的:软性约束-减少理解偏差]
- 可行的agent项目文件结构示例
agent-project/
│
├── docs/                              ← 【分析讨论文档】给人看的，记录分析过程和结论
│   ├── 依赖关系类型影响分析.md
│   ├── default_if详解与QA风险分析.md
│   └── 任务方案.md                     ← 【给人看的 大致执行方案，主导方向问题】
│
├── specs/                             ← 【Agent 执行规范】给 agent 看的，定义怎么做
│   ├── 规则.md                         ← 规则约束[硬约束，可随时庚戌年，保证agent自觉应用更新后的规则]
│   ├── 文件索引.md                     ← 所有文件路径[所有agent会用到的文件/资源指路]
│   └── prompt模板.md                  ← 给 agent 的 prompt 模板
│
├── plans/                             ← 【执行计划】拆分的具体执行步骤和任务编排
│   ├── plan.md                        ← 【给agent看的 修改后的最终执行方案 技术执行细节】
│   ├── phase1.md
│   ├── phase2.md
│   └── phase3.md
│
├── output/                            ← 【分析结果】Agent 生成的正式输出
│   ├── xxx/
│   │   ├── xxx.json                   ← 【给agent看的】
│   │   ├── xxx.md                     ← 【给人看的】
│   │   └── 
│   ├── xxx/
│   │   ├── xxx.json
│   │   ├── xxx.md
│   │   └── 
│   └── xxx/
│       └──
│
├── process/                           ← 【过程文档】Agent 生成的中间产物，后续可能复用
│   ├── 
│   ├── 
│   ├── 
│   └── 
│
└── validation/                        ← 【验证】dry-run 和金丝雀验证
    ├── dry-run/
    │   ├── dry_run_report.md            ← dry-run 结果报告
    │   └── sample_configs/              ← 少量样例配置用于人工审查
    └── canary/
        ├── canary_plan.md               ← 金丝雀最小验证方案
        ├── canary_configs/              ← 最小验证用的配置文件
        └── canary_result.md             ← 验证结果
- specs/规则.md 写什么
> 支持规则更新后agent及时应用
    - 每次agent执行都要先检查一遍规则有无更新 [token消耗影响][标记检查？token]
> 任务完成后记录完成过程，作为后续参考(以什么形式记录 skill是否是最合适的？)
> 修改完成方式等各种时及时修改对应文档(做到实现与文档一致性)
    > * 要及时更新哪些文件夹中的文件？
    > * 更新规则 
        - 只修改改动的地方，所有引用该改动的地方都要改动
        - 未改动的地方，不要随意修改
> 文件检查与写入规则
    > * 及时检查各文件记入内容是否有重复，有无耦合
        - 文件内容耦合
        - 检查有无冗余文件
        - 过程中调整方案后，原方案生成的文件是否还有价值？ 内容转移还是直接弃用
    > * 特定内容应该记入什么文件?
        - agent plan写入plan.md
        - 新增文件要在文件索引中新增作用与使用方法
        - 分析写入docs/
    > * 文件引用
        - 引用是否会省token？
        - 遇到引用文件，什么时候去查看被引用的文件 [是否查看的决策依据]


> 项目特定规则 [目的：让项目可以不用监视自动工作]
    > 


