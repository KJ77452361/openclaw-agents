# Cron Definition: session_cleanup
> 版本：v1.0.0 | 状态：⚠️ 历史 | 标准名：`sys_session_cleanup_daily`

| Field | Value |
|-------|-------|
| **name** | session_cleanup |
| **schedule** | `0 2 * * *` Asia/Shanghai |
| **sessionTarget** | isolated |
| **timeoutSeconds** | 180 |
| **jobId** | `ec61c448-5fb1-4c98-a830-2a70145106d4` |
| **created** | 2026-06-26 |
| **purpose** | 每日 session 清理 |

## 触发内容

清理超过 7 天的历史 session（排除当前 main session）

## 输出

写入 `/home/openclaw/.openclaw/agents/ceo/memory/YYYY-MM-DD_cleanup.md`
