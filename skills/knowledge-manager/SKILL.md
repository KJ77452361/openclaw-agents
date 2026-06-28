---
name: knowledge-manager
description: CEO 知识库管理 — 维护知识库索引、同步 MyBrain、审计知识完整性
version: 1.0.0
metadata:
  openclaw:
    always: false
---

# Knowledge Manager

CEO 的知识库引擎。维护本地知识库与全局 MyBrain 的一致性。

## 知识库结构（必须）

```
knowledge/
├── index.md              ← 知识库总索引（必须）
├── system/               ← 系统架构文档（必须）
│   ├── agents.md         ← 智能体架构
│   ├── cron.md           ← Cron Job 清单
│   └── channels.md       ← 渠道配置
├── sandbox/              ← 沙盒验证区
└── memory/               ← 临时记忆引用
```

## 触发条件

1. **架构变更** — Agent 增减、角色调整 → 更新 `knowledge/system/agents.md`
2. **Cron 变更** — Job 创建/删除/修改 → 更新 `knowledge/system/cron.md`
3. **渠道变更** — 渠道配置变化 → 更新 `knowledge/system/channels.md`
4. **日终同步** — 每日日终将日记忆精华同步至 `knowledge/`
5. **知识审计** — 每周日终审计 `knowledge/` 完整性

## 同步原则

| 方向 | 内容 | 频率 |
|------|------|------|
| 本地 → MyBrain | 重大决策、架构变更 | 实时 |
| MyBrain → 本地 | 全局知识更新 | 按需 |
| 日记忆 → 知识库 | 验证过的信息 | 日终 |

## 索引维护

每次修改 `knowledge/` 下的文件后，更新 `knowledge/index.md` 的变更记录。

## 禁止

- ❌ 知识库不含 secrets
- ❌ 不在 `knowledge/` 存放二进制文件（>1MB）
- ❌ 临时文件不放 `knowledge/`，放 `memory/` 或 `sandbox/`

---

*version 1.0.0 · King · 2026-06-27*