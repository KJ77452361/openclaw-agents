---
name: cron-manager
description: CEO Cron Job 全生命周期管理 — 创建/更新/删除/验证定时任务
version: 1.0.0
metadata:
  openclaw:
    always: false
---

# Cron Manager

CEO 的自动化调度引擎。统一管理所有 Cron Job。

## 触发条件

- 用户要求创建/修改/删除定时任务
- 系统自检发现 Cron Job 异常
- 日/周/月例行检查

## Job 命名规范

```
{domain}_{action}_{frequency}

domain:    sys | knowledge | agent | channel | quality | memory
action:    health | backup | sync | cleanup | check | audit | report
frequency: daily | hourly | weekly | monthly

示例：
sys_health_daily
knowledge_backup_daily
agent_session_cleanup_daily
quality_weekly_check
```

## Job 创建标准

使用 `cron` 工具创建，必要字段：

```json
{
  "name": "sys_health_daily",
  "schedule": { "kind": "cron", "expr": "0 9 * * *", "tz": "Asia/Shanghai" },
  "sessionTarget": "isolated",
  "payload": { "kind": "agentTurn", "message": "执行系统健康检查..." },
  "delivery": { "mode": "none" },
  "enabled": true
}
```

## 自检机制

每 6 小时运行 `cron_self_health`：
1. 列出所有活跃 Job
2. 检查最近运行时间
3. 标记超 2 倍周期未运行的 Job 为异常
4. 输出异常报告

## 禁止

- ❌ 不在 HEARTBEAT.md 中创建 cron job（用 cron 工具）
- ❌ Cron job 不直接投递到未配置的 channel
- ❌ 不过度创建 Job（同一目标最多 1 个自动化 Job）

---

*version 1.0.0 · King · 2026-06-27*