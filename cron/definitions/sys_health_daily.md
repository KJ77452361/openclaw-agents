# Cron Definition: sys_health_daily
> 版本：v1.0.0 | 状态：✅ | 标准名：`sys_health_daily`

| Field | Value |
|-------|-------|
| **name** | sys_health_daily |
| **schedule** | `0 9 * * *` Asia/Shanghai |
| **sessionTarget** | isolated |
| **timeoutSeconds** | 300 |
| **jobId** | `9bec75a5-dc66-4d6b-b383-42e06a108cff` |
| **created** | 2026-06-26 |
| **purpose** | 系统每日健康检查 |

## 触发内容

执行系统健康检查：检查 openclaw status / cron jobs / sessions / 磁盘 / 内存 / 飞书 channel

## 输出

写入 `/home/openclaw/.openclaw/agents/ceo/memory/YYYY-MM-DD.md`
