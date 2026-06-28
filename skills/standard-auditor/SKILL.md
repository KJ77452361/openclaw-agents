---
name: standard-auditor
description: CEO 标准化审计 — 检查 Agent 工作区、Skills、Cron Jobs 是否符合规范
version: 1.0.0
metadata:
  openclaw:
    always: false
---

# Standard Auditor

CEO 的标准化合规引擎。定期审计 OpenClaw 生态是否符合规范。

## 审计范围

### 1. Agent 工作区审计
检查每个 Agent 目录是否包含：
- [ ] `AGENTS.md`（必须）
- [ ] `SOUL.md`（必须）
- [ ] `IDENTITY.md`（必须）
- [ ] `USER.md`（必须）
- [ ] `MEMORY.md`（建议）
- [ ] `memory/` 目录存在

### 2. Skill 审计
- [ ] `skills/` 目录中每个 Skill 含 `SKILL.md`
- [ ] SKILL.md frontmatter 含 `name` + `description`
- [ ] name 符合小写+连字符规范
- [ ] description ≤ 160 字符

### 3. Cron Job 审计
- [ ] Job name 符合命名规范
- [ ] 同一目标不超过 1 个自动化 Job
- [ ] delivery.mode 与 target 配置一致
- [ ] 超 2 倍周期未运行的 Job 标记为异常

### 4. 知识库审计
- [ ] `knowledge/index.md` 存在且最新
- [ ] `knowledge/system/` 目录结构完整
- [ ] 无过期或错误链接

## 执行方式

每周日终 `quality_weekly_check` 自动触发。

手动执行：
```
# 读取 STANDARDS.md 确认规范
# 按上述检查项逐项验证
# 输出审计报告到 memory/YYYY-MM-DD_audit.md
```

## 禁止

- ❌ 不在生产环境执行破坏性审计
- ❌ 不修改未明确违反规范的文件
- ❌ 审计报告不含敏感配置信息

---

*version 1.0.0 · King · 2026-06-27*