# Cron Definition: knowledge_backup
> 版本：v1.0.0 | 状态：⚠️ 历史 | 标准名：`knowledge_backup_daily`

| Field | Value |
|-------|-------|
| **name** | knowledge_backup |
| **schedule** | `0 3 * * *` Asia/Shanghai |
| **sessionTarget** | isolated |
| **timeoutSeconds** | 300 |
| **jobId** | `7bd20875-d174-4a9e-a8d4-11ffb192be35` |
| **created** | 2026-06-26 |
| **purpose** | 每日知识库备份 |

## 触发内容

备份 knowledge/ 和 mybrain/ 目录

## 输出

写入 `/home/openclaw/.openclaw/agents/ceo/memory/YYYY-MM-DD_backup.md`
