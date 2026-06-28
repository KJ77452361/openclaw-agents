# Cron Definition: daily_mybrain_sync
> 版本：v1.0.0 | 状态：⚠️ 历史 | 标准名：`sys_mybrain_sync_daily`

| Field | Value |
|-------|-------|
| **name** | daily_mybrain_sync |
| **schedule** | `0 6 * * *` Asia/Shanghai |
| **sessionTarget** | isolated |
| **timeoutSeconds** | 300 |
| **jobId** | `b68d3e42-db0d-4bb0-9356-a7620f87c867` |
| **created** | 2026-06-26 |
| **purpose** | 每日 MyBrain 同步检查 |

## 触发内容

检查 mybrain/ 和 agents/knowledge/ 同步状态

## 输出

写入 `/home/openclaw/.openclaw/agents/ceo/memory/YYYY-MM-DD_sync.md`
