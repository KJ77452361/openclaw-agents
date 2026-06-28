# Cron Definition: memory_log_compress
> 版本：v1.0.0 | 状态：active | 标准名：`memory_log_compress`

| Field | Value |
|-------|-------|
| **name** | `memory_log_compress` |
| **schedule** | `cron 0 3 * * * @ Asia/Shanghai` |
| **sessionTarget** | isolated |
| **purpose** | 每日内存日志压缩，扫描 .md 文件并压缩超过200行的日志文件 |
