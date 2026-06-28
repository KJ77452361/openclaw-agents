# Cron Definition: weekly_knowledge_audit
> 版本：v1.0.0 | 状态：✅ | 标准名：`knowledge_weekly_audit`

| Field | Value |
|-------|-------|
| **name** | weekly_knowledge_audit |
| **schedule** | `0 22 * * 0` Asia/Shanghai |
| **sessionTarget** | isolated |
| **timeoutSeconds** | 300 |
| **jobId** | `47de8d3b-7eb7-44fa-8899-07273ec96e91` |
| **created** | 2026-06-26 |
| **purpose** | 周知识审计（周日 22:00） |

## 触发内容

审计 mybrain/ 和 agents/knowledge/ 文件完整性

## 输出

写入 `/home/openclaw/.openclaw/agents/ceo/memory/YYYY-MM-DD_knowledge_audit.md`
