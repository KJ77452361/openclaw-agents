# Cron Definition: auth_store_backup
> 版本：v1.0.0 | 状态：active | 标准名：`auth_store_backup`

| Field | Value |
|-------|-------|
| **name** | `auth_store_backup` |
| **schedule** | `cron 30 3 * * * @ Asia/Shanghai` |
| **sessionTarget** | isolated |
| **purpose** | 定期备份 Auth Store（身份认证数据），每半月执行一次，确保认证凭据可恢复 |
