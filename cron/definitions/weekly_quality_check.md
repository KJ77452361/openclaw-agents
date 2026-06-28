# Cron Definition: weekly_quality_check
> 版本：v1.0.0 | 状态：✅ | 标准名：`quality_weekly_check`

| Field | Value |
|-------|-------|
| **name** | weekly_quality_check |
| **schedule** | `0 21 * * 0` Asia/Shanghai |
| **sessionTarget** | isolated |
| **timeoutSeconds** | 300 |
| **jobId** | `38f6abda-1ce7-444c-830c-c470f1248720` |
| **created** | 2026-06-26 |
| **purpose** | 周质量检查（周日 21:00） |

## 触发内容

统计本周 Cron / Session / 知识库运行情况

## 输出

写入 `/home/openclaw/.openclaw/workspace/mybrain/daily/YYYY-MM-DD_周质量检查.md`
