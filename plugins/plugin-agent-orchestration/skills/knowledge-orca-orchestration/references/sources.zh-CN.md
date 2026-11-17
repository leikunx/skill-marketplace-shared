# Orca 来源索引

[English](sources.md) | **简体中文**

核查日期：**2026-11-17**。证据来自浏览器渲染的官方页面及浅克隆的 Git 源码。
网络搜索用于发现资料；生命周期行为的依据不采用搜索摘要或第三方教程。
源码版本：`bf33c20951d645619f4027da66f534725bee0bd2`。

| 编号 | 一手资料 | 支持的结论 |
| --- | --- | --- |
| O1 | [编排文档](https://orca.dev/docs/cli/orchestration)、[固定版本源码](https://github.com/stablyai/orca/blob/bf33c20951d645619f4027da66f534725bee0bd2/docs/site/content/docs/cli/orchestration.mdx) | 运行时前提、核心对象、状态、命令、消息、关卡、worker_done 和已退役命令。 |
| O2 | [固定版本编排指南](https://github.com/stablyai/orca/blob/bf33c20951d645619f4027da66f534725bee0bd2/skill-guides/orchestration.md) | 协调者与工作代理的常规流程、结束回合与唤醒、执行位置、后续任务和验收证据。 |
| O3 | [协调者流程](https://github.com/stablyai/orca/blob/bf33c20951d645619f4027da66f534725bee0bd2/skill-guides/orchestration/references/coordinator-loop.md) | 依赖关系、就绪 Task 和多个 Run。 |
| O4 | [执行位置与远程执行](https://github.com/stablyai/orca/blob/bf33c20951d645619f4027da66f534725bee0bd2/skill-guides/orchestration/references/placement-and-remote.md) | 普通文件夹与 worktree 的区别、Run 所在运行时、已连接服务器上的执行位置和路由。 |
| O5 | [恢复与清理](https://github.com/stablyai/orca/blob/bf33c20951d645619f4027da66f534725bee0bd2/skill-guides/orchestration/references/recovery-and-cleanup.md) | 重试链、熔断、取消、放弃分配及释放状态不确定时的处理。 |
| O6 | [数据库实现](https://github.com/stablyai/orca/blob/bf33c20951d645619f4027da66f534725bee0bd2/src/main/runtime/orchestration/db/orchestration-db.ts)、[关系模型定义](https://github.com/stablyai/orca/blob/bf33c20951d645619f4027da66f534725bee0bd2/src/main/runtime/orchestration/db/schema/create-graph-tables-sql.ts) | SQLite/WAL、持久化 Task/Dispatch/关卡记录和身份字段。 |
| O7 | [工作代理报告的终态处理](https://github.com/stablyai/orca/blob/bf33c20951d645619f4027da66f534725bee0bd2/src/main/runtime/orchestration/db/dispatch-context/worker-report-settlement.ts) | 事务式终态确认、重复处理、不匹配/过期/冲突尝试和清理钩子。 |
| O8 | [CLI 终态验证](https://github.com/stablyai/orca/blob/bf33c20951d645619f4027da66f534725bee0bd2/src/cli/orchestration/workers/orchestration-worker-settlement.ts) | 生命周期判定、旧版回读验证，以及结果未确定的修改请求恢复。 |
| O9 | [CLI 发现技能](https://github.com/stablyai/orca/blob/bf33c20951d645619f4027da66f534725bee0bd2/skills/orca-cli/SKILL.md) | 与版本匹配的指南和可执行文件选择。 |

如果安装的是其他版本，应先获取其内置指南并检查对应标签的源码，
再使用与版本有关的命令、重试阈值、邮箱语义或远程限制。
区分文档描述、源码检查与实际运行测试得出的观察结果。
