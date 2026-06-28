---
name: software-design
description: 软件设计与建模 — 设计系统模块、定义接口规范、编写技术设计文档
version: 1.0.0
metadata:
  openclaw:
    requires: [architecture-review]
    tags: [software, design, CTO]
---

# Software Design

> Skill: software-design | v1.0.0 | for: se
> 适用场景：模块设计、接口规范编写、技术设计文档、技术选型评估

## 描述

对软件系统或模块进行具体设计，输出模块结构、接口规范、数据模型等技术文档。
与 architecture-review 的关系：architecture-review 评估"做什么"，software-design 负责"怎么做"。

## 前置条件

- 理解 OpenClaw 技术栈（Node.js / Shell / Python）
- 了解 architecture-review 的设计结论

## 输入

| 字段 | 类型 | 说明 |
|------|------|------|
| module_name | string | 模块名称 |
| requirements | string | 功能需求描述 |
| constraints | string | 约束条件（可选）|

## 输出格式

```markdown
# 软件设计文档：{模块名称}

## 1. 模块概述
{一句话描述模块职责}

## 2. 模块结构
```text
{模块目录结构}
```

## 3. 接口规范

### 3.1 核心接口

| 接口 | 输入 | 输出 | 说明 |
|------|------|------|------|
| funcA() | {params} | {return} | ... |

## 4. 数据模型

```javascript
// {ModelName}
{
  field: type,  // 说明
}
```

## 5. 依赖关系
| 依赖模块 | 依赖原因 |
|---------|---------|
| ... | ... |

## 6. 错误处理
| 错误码 | 说明 | 处理方式 |
|--------|------|---------|
| E001 | ... | ... |
```

## 示例

**输入：**
```
设计一个新的 Session 记忆缓存模块
需求：支持按 sessionId 存储和读取，TTL 过期机制，容量限制
```

**输出：**
```
# 软件设计文档：Session Memory Cache

## 1. 模块概述
轻量级内存缓存，用于 Session 级别的数据暂存，支持 TTL 过期和 LRU 淘汰。

## 2. 模块结构
```text
session-cache/
├── index.js          # 导出 CacheManager
├── cache.js          # LRU Cache 实现
└── ttl.js           # TTL 管理器
```

## 3. 接口规范

| 接口 | 输入 | 输出 | 说明 |
|------|------|------|------|
| get(key) | string | any | 按 key 读取 |
| set(key, value, ttl?) | string, any, number | void | 写入，TTL 可选 |
| has(key) | string | boolean | 是否存在（含过期检查）|
| clear() | — | void | 清空所有 |

## 4. 错误处理
| 错误码 | 说明 | 处理 |
|--------|------|------|
| E_CACHE_FULL | 缓存满 | LRU 淘汰最旧条目 |
| E_TTL_EXPIRED | TTL 过期 | 自动删除，返回 undefined |
```
