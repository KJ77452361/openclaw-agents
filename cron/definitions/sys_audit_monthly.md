# Cron Definition: monthly_full_audit
> 版本：v1.0.0 | 状态：✅ | 标准名：`quality_monthly_audit`

| Field | Value |
|-------|-------|
| **name** | monthly_full_audit |
| **schedule** | `0 21 L * *` Asia/Shanghai |
| **sessionTarget** | isolated |
| **timeoutSeconds** | 600 |
| **jobId** | `8b3f256b-3324-4614-a50e-f664d0707082` |
| **created** | 2026-06-26 |
| **purpose** | 月度全量审计（月末 21:00） |

## 触发内容

Cron 月报 / Session 月报 / 知识库月报 / 配置变更记录

## 输出

写入 `/home/openclaw/.openclaw/workspace/mybrain/daily/YYYY-MM_月度审计.md`
