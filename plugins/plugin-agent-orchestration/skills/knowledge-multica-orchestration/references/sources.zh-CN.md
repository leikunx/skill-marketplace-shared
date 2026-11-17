# Multica 来源索引

[English](sources.md) | **简体中文**

核查日期：**2026-11-17**。证据来自浏览器渲染的官方页面及浅克隆的 Git 源码。
搜索结果仅用于发现资料。源码版本：
`670082cffe0b6c25ea36d62fb31939adbd2d5e93`。

| 编号 | 一手资料 | 支持的结论 |
| --- | --- | --- |
| M1 | [仓库 README](https://github.com/multica-ai/multica/blob/670082cffe0b6c25ea36d62fb31939adbd2d5e93/README.md) | 产品身份、客户端/后端/数据库/守护进程架构。 |
| M2 | [Multica 如何工作](https://multica.ai/docs/how-multica-works)、[固定版本源码](https://github.com/multica-ai/multica/blob/670082cffe0b6c25ea36d62fb31939adbd2d5e93/apps/docs/content/docs/how-multica-works.mdx) | 从触发到结果的流程、执行和数据边界、run 完成与议题完成的区别。 |
| M3 | [守护进程与运行时](https://multica.ai/docs/daemon-runtimes)、[固定版本源码](https://github.com/multica-ai/multica/blob/670082cffe0b6c25ea36d62fb31939adbd2d5e93/apps/docs/content/docs/daemon-runtimes.mdx) | 注册、通知/轮询、心跳、并发、恢复和远程 Qoder 路径这一例外。 |
| M4 | [执行记录](https://multica.ai/docs/tasks)、[固定版本源码](https://github.com/multica-ai/multica/blob/670082cffe0b6c25ea36d62fb31939adbd2d5e93/apps/docs/content/docs/tasks.mdx) | 状态、队列/离线行为、重试默认值与会话延续、停止和完成边界。 |
| M5 | [Squad 团队](https://multica.ai/docs/squads)、[固定版本文档](https://github.com/multica-ai/multica/blob/670082cffe0b6c25ea36d62fb31939adbd2d5e93/apps/docs/content/docs/squads.mdx)、[内置团队参考](https://github.com/multica-ai/multica/blob/670082cffe0b6c25ea36d62fb31939adbd2d5e93/server/internal/service/builtin_skills/multica-platform/references/squads.md) | 领导代理路由、确切提及格式、成员不会自动全部启动、唤醒、状态修改权限和项目工作流。 |
| M6 | [内置子议题参考](https://github.com/multica-ai/multica/blob/670082cffe0b6c25ea36d62fb31939adbd2d5e93/server/internal/service/builtin_skills/multica-platform/references/sub-issues.md) | 阶段关卡、backlog/todo 触发规则、父议题唤醒、代理推进后续阶段和终态类别。 |
| M7 | [Autopilot](https://multica.ai/docs/autopilots)、[固定版本源码](https://github.com/multica-ai/multica/blob/670082cffe0b6c25ea36d62fb31939adbd2d5e93/apps/docs/content/docs/autopilots.mdx) | 计划/webhook 触发、创建议题与仅执行两种模式、与议题唤醒的区别。 |
| M8 | [守护进程执行逻辑](https://github.com/multica-ai/multica/blob/670082cffe0b6c25ea36d62fb31939adbd2d5e93/server/internal/daemon/daemon.go)、[持久化终态报告队列](https://github.com/multica-ai/multica/blob/670082cffe0b6c25ea36d62fb31939adbd2d5e93/server/internal/daemon/terminal_report_queue.go) | 批量领取循环、complete/fail 报告、持久化回调发件队列、重放和取消检查。 |
| M9 | [任务服务](https://github.com/multica-ai/multica/blob/670082cffe0b6c25ea36d62fb31939adbd2d5e93/server/internal/service/task.go)、[队列 SQL](https://github.com/multica-ai/multica/blob/670082cffe0b6c25ea36d62fb31939adbd2d5e93/server/pkg/db/queries/agent.sql) | 领取/状态转换仲裁、事务式完成、幂等终态回调和重试条件。 |
| M10 | [项目资源](https://multica.ai/docs/project-resources)、[固定版本源码](https://github.com/multica-ai/multica/blob/670082cffe0b6c25ea36d62fb31939adbd2d5e93/apps/docs/content/docs/project-resources.mdx) | 仓库 worktree、本地原地编辑的串行机制、明确的 worktree 能力要求和失败行为。 |
| M11 | [安全模型](https://multica.ai/docs/security-model)、[固定版本源码](https://github.com/multica-ai/multica/blob/670082cffe0b6c25ea36d62fb31939adbd2d5e93/apps/docs/content/docs/security-model.mdx) | daemon 用户权限边界；worktree 和单次 run 状态不提供通用沙箱。 |
| M12 | [技能](https://multica.ai/docs/skills)、[固定版本源码](https://github.com/multica-ai/multica/blob/670082cffe0b6c25ea36d62fb31939adbd2d5e93/apps/docs/content/docs/skills.mdx) | 可复用指导、技能分配、导入和刷新语义。 |
| M13 | [CLI 与守护进程指南](https://github.com/multica-ai/multica/blob/670082cffe0b6c25ea36d62fb31939adbd2d5e93/CLI_AND_DAEMON.md) | CLI 诊断及不同 profile 对应的 daemon 状态和日志路径。 |

上述实现观察描述的是这个提交版本，不代表每个托管部署都具备相同行为。
产品页面和 `main` 分支可能独立演进。给出操作建议前，检查部署版本、运行时类型、项目工作流和当前命令帮助。
不要将容易变化的提供商数量、并发上限或超时数值写成普遍要求。
