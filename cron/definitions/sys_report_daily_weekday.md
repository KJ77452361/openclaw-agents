# Cron Definition: daily_report_weekday
> 版本：v1.0.0 | 状态：⚠️ 历史 | 标准名：`sys_report_weekday_daily`

| Field | Value |
|-------|-------|
| **name** | daily_report_weekday |
| **schedule** | `0 8 * * 1-5` Asia/Shanghai |
| **sessionTarget** | isolated |
| **timeoutSeconds** | 300 |
| **jobId** | `096662d8-f075-4124-8a89-7e73e2d4f9f8` |
| **created** | 2026-06-26 |
| **purpose** | 工作日报告生成 |

## 触发内容

汇总昨日事件 / Cron 运行记录 / 生成当日待办预览

## 输出

写入 `/home/openclaw/.openclaw/workspace/mybrain/daily/YYYY-MM-DD.md`
