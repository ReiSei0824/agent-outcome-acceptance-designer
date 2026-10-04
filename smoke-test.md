# Smoke Test — 2026-10-04

## 结构检查

- `name`：`agent-outcome-acceptance-designer`，lowercase-hyphen，PASS。
- `description`：146 字符，PASS。
- 必备章节：核心定位、触发场景、工作流、输出格式、Gotchas，PASS。
- 工作流：6 步，位于 3-8 步范围，PASS。
- Gotchas：6 条，PASS。
- 未填充占位符：未发现，PASS。

## README 检查

- 安装路径为 `~/.claude/skills/agent-outcome-acceptance-designer/`，不误用本地中文归档目录，PASS。
- 仓库名、文件树、触发词均使用 `agent-outcome-acceptance-designer`，PASS。

## 触发干运行

### 中文

输入：`别只看 agent 说完成了，帮我验收它有没有只给指定客户创建工单，并在中断后能恢复。`

预期落点：终态工单查询、客户范围副作用检查、中断残留检查、恢复断言、PASS/FAIL/CHECK/INCONCLUSIVE 判定。

结果：PASS。输入与“验证智能体真实完成、检查副作用和恢复”的触发场景直接匹配，输出可直接形成验收表。

### English

Input: `Design acceptance checks for an agent that updates invoices; verify final state, unintended writes, and timeout recovery.`

Expected routing: final-state assertions, side-effect assertions, timeout/recovery case, evidence bundle, explicit verdict.

Result: PASS. The request matches the skill's stated scope and is not reduced to abstract advice.

## 总结

结论：**修复后通过**。首轮发现 description 长度超限及示例尖括号占位符；已压缩 description 并将示例替换为具体客服工单场景，复检通过。
