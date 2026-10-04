# 智能体结果验收设计师 · Agent Outcome Acceptance Designer

为会调用工具、改文件或触发外部操作的 AI Agent 设计“结果是否真的落地”的验收包。它不相信模型的一句“完成了”，而是把任务转成终态断言、副作用断言、可复跑用例和证据要求。

## 适用场景

- 验收一个 agent 是否真的把报告、代码、数据或配置写到了目标系统。
- 为自动化增加中断恢复、错误输入和越界副作用检查。
- 将人工口头验收标准整理成任务说明、CI 检查或运行手册。

## 触发词

- “帮我验收这个 AI Agent 是否真的完成了任务”
- “别只看模型自报，设计一套终态检查”
- “design acceptance tests for an agent workflow”
- “verify the agent’s side effects and recovery path”

## 工作流

`观察边界 → 终态与副作用断言 → 最小用例 → 证据包 → 判定与恢复`

1. 明确目标系统、权限和禁止操作。
2. 写出可观察的终态与副作用断言。
3. 覆盖正常、部分完成、错误输入和恢复。
4. 保存输入、日志、终态快照及环境信息。
5. 按 PASS / FAIL / CHECK / INCONCLUSIVE 给出结论。

## 示例

输入：`设计一个验收包，验证客服 agent 是否只给指定客户创建了工单，并在超时后可恢复。`

输出：带只读工单查询、客户范围校验、超时残留检查、恢复验证和证据归档要求的验收表；没有可读终态时，结论保持 `CHECK`，不会凭 agent 文字判定成功。

## 安装

将本目录复制到 Claude Code 的 skills 目录：

```text
~/.claude/skills/agent-outcome-acceptance-designer/
├── SKILL.md
└── README.md
```

本地中文归档目录仅用于整理，不是安装路径：`智能体结果验收设计师（agent-outcome-acceptance-designer）`。

## 发布

建议仓库名：`agent-outcome-acceptance-designer`。发布前先运行 `smoke-test.md` 中的结构与触发检查；仅在新仓库、GitHub CLI 已登录、无需覆盖现有仓库时创建并推送。

## 边界

该 skill 是工程验收设计工具，不构成安全认证、合规结论或生产变更授权。对没有可读取终态的任务，应输出 `CHECK` 或 `INCONCLUSIVE`。
