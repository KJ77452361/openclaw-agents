# OpenClaw Workspace 标准化总纲

> 版本：v2.0.0
> 建立：2026-06-27
> 上级标准：`~/.openclaw/agents/ceo/STANDARDS.md`（v1.1.0）
> 依据：docs.openclaw.ai + github.com/openclaw 官方规范

---

## 1. 定位

本文档定义 **OpenClaw Workspace（`~/.openclaw/workspace/`）** 的完整标准化规范。

Workspace 是 OpenClaw 系统的**全局共享工作区**，同时是业务执行层 Agent（sales_* / translator_zh）的工作目录。

**上级标准**：`~/.openclaw/agents/ceo/STANDARDS.md`（管辖全生态）
**本地标准**：本文档（管辖 workspace 内规范）

---

## 2. 目录结构标准

### 2.1 顶层规范

```
workspace/
├── SOUL.md              ← 全局灵魂（必须）
├── USER.md              ← 全局用户（必须）
├── AGENTS.md            ← 全局作业流程（必须）
├── MEMORY.md            ← 全局长期记忆（建议）
├── STANDARDS.md         ← 本文件，workspace 标准总纲（必须）
│
├── agents/              ← 业务执行层 Agent（Level 2）
├── MyBrain/             ← 全局知识库（唯一主库）
├── memory/               ← 系统记忆（必须）
├── cron/                 ← Cron Job 定义（必须）
├── logs/                 ← 日志（必须）
└── sys/                 ← 系统配置（必须）
```

> **命名原则**：目录名全部小写（英语）；中文仅用于知识卡片内容（mybrain/cards/）。

### 2.2 完整目录树

```
workspace/
├── SOUL.md
├── USER.md
├── AGENTS.md
├── MEMORY.md
├── STANDARDS.md
│
├── agents/                              ← 业务执行层 Agent
│   └── <agent>/
│       ├── AGENTS.md                    ← 必须
│       ├── SOUL.md                      ← 必须
│       ├── IDENTITY.md                  ← 必须
│       ├── USER.md                      ← 必须
│       ├── MEMORY.md                    ← 建议
│       ├── DREAMS.md                    ← 可选
│       ├── knowledge/
│       │   └── index.md                 ← 可选
│       └── memory/
│           ├── daily/                   ← 可选
│           └── dreams/                  ← 可选
│
├── MyBrain/                             ← 全局知识库（LYT 框架）
│   ├── daily/                           ← Cron 输出 + 每日记录
│   │   ├── YYYY-MM-DD.md               ← 每日摘要（格式：YYYY-MM-DD.md）
│   │   └── Cron*.md                    ← Cron 执行报告（自动生成）
│   ├── cards/                           ← 永久卡片库
│   │   ├── 概念/                        ← 抽象概念
│   │   ├── 方法/                        ← 方法论 / SOP
│   │   └── 案例/                        ← 实际案例
│   ├── projects/                        ← 项目文档
│   ├── calendar/                        ← 日程
│   ├── inbox/                          ← 收集箱（待处理）
│   ├── templates/                       ← 模板
│   └── system/                         ← 系统文档
│       └── INDEX.md                    ← 知识库索引
│
├── memory/                              ← 系统记忆（Dreaming System）
│   ├── daily/                          ← 日记忆文件
│   │   └── YYYY-MM-DD.md
│   └── dreams/                         ← Dreaming 输出
│       ├── light/                      ← 浅梦（日常记录）
│       │   └── YYYY-MM-DD.md
│       ├── deep/                       ← 深梦（深度分析）
│       │   └── YYYY-MM-DD.md
│       ├── rem/                        ← REM 梦（灵感片段）
│       │   └── YYYY-MM-DD.md
│       └── sessions/                   ← Session 语料（自动）
│
├── cron/                                 ← Cron Job 定义
│   ├── definitions/                    ← Job 定义文件
│   │   └── <name>.md
│   └── runs/                           ← 运行记录（自动生成）
│       └── <name>_YYYY-MM-DD_HHmm.jsonl
│
├── logs/                                 ← 日志
│   ├── daily/                          ← 每日日志
│   └── system/                         ← 系统日志
│
└── sys/                                 ← 系统配置
    └── config/
        ├── IDENTITY.md                 ← Workspace 身份卡
        ├── TOOLS.md                   ← 工具配置
        ├── DREAMS.md                  ← 梦想配置
        └── HEARTBEAT.md               ← 心跳配置
```

---

## 3. 知识库规范（MyBrain/）

### 3.1 唯一性原则

> **只保留一个知识库**：`MyBrain/`。`mybrain/` 废弃，迁移合并。

### 3.2 MyBrain/ vs mybrain/ 合并规则

| 来源 | 迁移目标 | 处理方式 |
|------|---------|---------|
| `mybrain/daily/*.md` | `MyBrain/daily/` | 合并，按日期覆盖 |
| `mybrain/cards/*` | `MyBrain/cards/` | 合并，去重 |
| `mybrain/system/*` | `MyBrain/system/` | 合并，覆盖 |
| `mybrain/calendar/*` | `MyBrain/calendar/` | 迁移 |
| `mybrain/projects/*` | `MyBrain/projects/` | 迁移 |
| `mybrain/templates/*` | `MyBrain/templates/` | 迁移 |
| `mybrain/inbox/*` | `MyBrain/inbox/` | 迁移 |

### 3.3 每日文件格式

```
# YYYY-MM-DD 每日摘要

> 日期：YYYY-MM-DD（星期X，GMT+8）

## 系统状态
<当日系统状态摘要>

## 执行记录
<Cron 运行 / Session 记录>

## 待处理
<待办事项>

---

*最后更新：YYYY-MM-DD HH:MM GMT+8*
```

### 3.4 卡片格式（cards/）

```
# 卡片标题

> 类型：概念 | 方法 | 案例
> 创建：YYYY-MM-DD
> 标签：#标签1 #标签2

## 摘要
<一句话说明>

## 详情
<详细内容>

## 来源
<引用/参考>
```

---

## 4. 记忆规范（memory/）

### 4.1 三层记忆结构

| 层级 | 目录 | 内容 | 生成方式 |
|------|------|------|---------|
| 浅梦 | `memory/dreams/light/` | 日常事件记录 | Dreaming System |
| 深梦 | `memory/dreams/deep/` | 深度分析洞察 | Dreaming System |
| REM | `memory/dreams/rem/` | 灵感片段 | Dreaming System |
| 日记忆 | `memory/daily/` | 每日总结 | Cron/手动 |

### 4.2 Dreaming System 文件命名

```
YYYY-MM-DD.md
```

### 4.3 禁止事项

- ❌ `memory/dreams/` 目录禁止手动编辑（由 Dreaming System 自动生成）
- ❌ 禁止在 `memory/` 目录存放 secrets 或 API key
- ❌ `memory/.dreams/` 为系统内部目录，禁止直接访问

---

## 5. Cron Job 规范（cron/)

### 5.1 定义文件标准格式

```markdown
# Cron Definition: <name>

> 版本：v1.0.0 | 状态：✅ | 标准名：`<std_name>`

| Field | Value |
|-------|-------|
| **name** | <name> |
| **schedule** | `<cron expr>` Asia/Shanghai |
| **sessionTarget** | isolated |
| **timeoutSeconds** | <seconds> |
| **jobId** | `<UUID>` |
| **created** | YYYY-MM-DD |
| **purpose** | <描述> |

## 触发内容

<具体行为>

## 输出

<输出位置>
```

### 5.2 命名规范（v2.0.0）

```
{domain}_{action}_{frequency}
```

### 5.3 状态标识

| 标识 | 含义 |
|------|------|
| ✅ | 符合 v2.0.0 规范 |
| ⚠️ 历史 | 历史遗留，暂保留不强制改名 |
| 🔒 插件 | 插件托管，不可改名 |

---

## 6. Agent 工作区标准（workspace/agents/）

### 6.1 必须文件清单

| 文件 | 内容要求 |
|------|---------|
| `AGENTS.md` | 角色职责、行动准则、标准化声明（版本+日期） |
| `SOUL.md` | 人格定义，≤5 行，含版本注释 |
| `IDENTITY.md` | 身份卡（代号、emoji、定位、汇报线） |
| `USER.md` | 用户信息（版本、创建、更新） |
| `MEMORY.md` | 长时记忆（版本、创建、更新） |

### 6.2 版本标注格式

每个文件首行：

```markdown
# 文件名 — 角色

> 版本：1.0.0
> 创建：YYYY-MM-DD
> 更新：YYYY-MM-DD
```

### 6.3 禁止事项

- ❌ 禁止在 workspace agents 中存放 secrets
- ❌ 禁止 workspace agent 持有 CEO/COO/CTO 级别权限
- ❌ 禁止 workspace agent 直接操作其他 agent 工作区

---

## 7. 系统配置规范（sys/config/）

| 文件 | 必须 | 说明 |
|------|------|------|
| `IDENTITY.md` | ✅ | Workspace 身份卡 |
| `TOOLS.md` | ✅ | 工具配置（含认证状态，不含 secrets） |
| `DREAMS.md` | ✅ | Dreaming System 配置 |
| `HEARTBEAT.md` | ✅ | 心跳任务配置 |

> 敏感信息（API key、secrets）只允许出现在 `~/.openclaw/config.yaml` 中，不允许写在任何 `.md` 文件内。

---

## 8. 敏感信息管理

### 8.1 脱敏规范

| 内容 | 示例 | 处理方式 |
|------|------|---------|
| API Key | `sk-abc...xyz` | 只显示前后 4 位，中间 `***` |
| App Secret | `appSecret: xxx` | 禁止写入任何 .md 文件 |
| Token | `Bearer eyJ...` | 禁止写入任何 .md 文件 |
| 密码 | `password: xxx` | 禁止写入任何 .md 文件 |
| App ID | `cli_a9f5...` | 可接受（非敏感 ID） | 保留原样 |

### 8.2 合规检查

所有新写入的 `.md` 文件，在写入前必须通过敏感信息扫描：

```bash
grep -i -E "secret|password|token|api.?key|bearer" <file>
```

如匹配，人工确认后才可提交。

---

## 9. 目录职责边界

| 目录 | 职责 | 边界 |
|------|------|------|
| `MyBrain/` | 知识积累、经验沉淀 | 知识性内容，不含系统输出 |
| `cron/` | Job 定义 + 运行记录 | 定义可编辑，运行记录只读 |
| `memory/` | Dreaming System、自进化记忆 | 系统自动生成，禁止手动编辑 dreams/ |
| `logs/` | 系统日志、审计日志 | 只读追加 |
| `sys/` | OpenClaw 系统配置 | 配置文件，不含业务数据 |
| `agents/` | 业务执行层 Agent | 业务层，不操作系统层 |

---

## 10. 文件命名规范

| 类型 | 格式 | 示例 |
|------|------|------|
| 每日笔记 | `YYYY-MM-DD.md` | `2026-06-27.md` |
| Cron 报告 | `Cron*.md` | `Cron自检_2026-06-27_18.md` |
| Cron 运行记录 | `cron_<name>_YYYY-MM-DD_HHmm.jsonl` | `cron_sys_health_2026-06-27_0600.jsonl` |
| 每日日志 | `YYYY-MM-DD.md` | `2026-06-27.md` |
| 梦境文件 | `YYYY-MM-DD.md` | `2026-06-27.md`（在 dreams/*/ 下） |

> **时区**：所有时间戳默认 GMT+8，无特别说明不标注时区。
> **字符集**：文件命名禁止使用特殊字符（仅 `-` / `_` / `.`）。

---

## 11. 空目录处理

| 目录 | 处理方式 |
|------|---------|
| `inbox/` | 保留，作为收集箱入口 |
| `projects/` | 保留，有项目时自然填充 |
| `templates/` | 保留，模板文件待创建 |
| `calendar/` | 保留，日程文件待创建 |
| `cards/概念/` | 保留，卡片随知识积累 |
| `cards/方法/` | 保留，卡片随知识积累 |
| `cards/案例/` | 保留，卡片随知识积累 |
| `logs/daily/` | 保留，日志文件自动生成 |
| `logs/system/` | 保留，系统日志自动生成 |
| `cron/runs/` | 保留，运行记录自动生成 |
| `memory/dreams/sessions/` | 保留，Session 语料自动生成 |
| `memory/archive/` | 保留，历史归档 |

---

## 12. 落地清单

| 编号 | 任务 | 状态 |
|------|------|------|
| WS-001 | workspace STANDARDS.md 建立 | ✅ |
| WS-002 | 4 个 workspace agent AGENTS.md 职责填充 | ✅ |
| WS-003 | cron/definitions/ 文件格式标准化 | ✅ |
| WS-004 | MyBrain/ vs mybrain/ 合并，确立单一知识库 | ✅ |
| WS-005 | memory/daily/ 敏感信息脱敏 | ✅ |
| WS-006 | sys/config/ 文件版本化 | ✅ |
| WS-007 | MyBrain/system/INDEX.md 更新至 v4.0.0 | ✅ |
| WS-008 | Dreaming System 文件规范化安置 | ✅ |
| WS-009 | 空目录填充（inbox/README.md 等） | ✅ |
| WS-010 | IATF16949 §7.5 文件控制规范引入（受控/非受控/作废标识） | ✅ |
| WS-011 | 文件编码规则建立（KB_STD/SOP/WI/REC 体系） | ✅ |
| WS-012 | 卡片生命周期SOP + 文件变更控制SOP 建立 | ✅ |
| WS-013 | 受控文件清单建立（KB_REC_001） | ✅ |

---

## 14. 文件控制规范（对应 IATF16949 §7.5）

### 14.1 受控文件 vs 非受控文件

| 状态 | 标识 | 说明 |
|------|------|------|
| **受控（active）** | `status: active` | 正式发布使用中的文件 |
| **非受控（draft）** | `status: draft` 或含 `_draft` | 草稿/讨论稿，不作正式依据 |
| **作废（obsolete）** | `status: obsolete` 或含 `_obsolete` | 已从受控清单移除 |

### 14.2 文件编码规则

格式：`{域代码}_{类型代码}_{序号}_v{major}.{minor}.{patch}`

| 域代码 | 含义 |
|--------|------|
| KB | 知识库（Knowledge Base） |
| WS | Workspace |
| CR | Cron Job |
| SK | Skill |

| 类型代码 | 含义 |
|----------|------|
| STD | 标准文件 |
| SOP | 作业程序 |
| WI | 工作指导 |
| REC | 记录表单 |

版本变更规则：patch 修正 → minor 增减 → major 重写。

### 14.3 变更控制要求

| 变更级别 | 触发条件 | 版本变化 | 审批要求 |
|---------|---------|---------|---------|
| **patch** | 错别字、格式修正 | v{x}.{y}.{z} → v{x}.{y}.{z+1} | 申请人自检 |
| **minor** | 内容增减 <20% | v{x}.{y}.{z} → v{x}.{y+1}.{0} | 域负责人批准 |
| **major** | 重写 ≥20% | v{x}.{y}.{z} → v{x+1}.{0}.{0} | CEO 批准 |

所有 active 文件变更须保留变更记录（在文件底部变更记录区）。

### 14.4 作废文件处理

- 加 `_obsolete_{日期}` 后缀
- 移入 `memory/archive/`
- 保存 1 年后评估销毁
- 不得在作废文件上直接编辑后重新激活

---

## 15. 与 CEO 标准的关系

| 层面 | 标准文件 | 管辖范围 |
|------|---------|---------|
| CEO 全局 | `agents/ceo/STANDARDS.md` | 全生态标准 |
| Workspace 本地 | `workspace/STANDARDS.md` | workspace 内规范 |

冲突时以上级（CEO STANDARDS.md）为准。

---

*King · 2026-06-27 · v2.0.0*
