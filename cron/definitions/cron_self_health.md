# Cron Definition: cron_self_health
> 版本：v1.0.0 | 状态：✅ | 标准名：`sys_cron_self_health`

| Field | Value |
|-------|-------|
| **name** | cron_self_health |
| **schedule** | `0 */6 * * *` Asia/Shanghai |
| **sessionTarget** | isolated |
| **timeoutSeconds** | 180 |
| **jobId** | `08e91f4a-ac26-4dc7-9663-eb3ab261ddc8` |
| **created** | 2026-06-26 |
| **purpose** | Cron 自检（每6h） |

## 触发内容

检查所有 cron job 状态，标记异常项

## 输出

写入 `/home/openclaw/.openclaw/agents/ceo/memory/YYYY-MM-DD_cron_health.md`
