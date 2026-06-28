# TOOLS.md — 本地工具约定

> 版本：v1.0.0
> 更新：2026-06-25

---

## SSH 连接配置

### Windows 主机（DESKTOP-QQMDSC1）

**私钥路径**：`~/.ssh/id_ed25519`

**连接方式**：
```bash
ssh -i ~/.ssh/id_ed25519 -o StrictHostKeyChecking=no Administrator@172.21.112.1
```

**SFTP 路径格式**：`/C:/Users/Administrator/.openclaw/`

**已知目录**：
- Windows .openclaw 根目录：`/C:/Users/Administrator/.openclaw/`
- 多智能体 agents：`/C:/Users/Administrator/.openclaw/agents/`
- **MyBrain 知识库**：`/C:/Users/Administrator/.openclaw/MyBrain/`（唯一知识库）
- 每日记忆：`/C:/Users/Administrator/.openclaw/memory/daily/`
- CEO 智能体核心文件：`/C:/Users/Administrator/.openclaw/agents/CEO/`
- Workspace 核心文件：`/C:/Users/Administrator/.openclaw/MyBrain/workspace/`

## GitHub CLI

| 项目 | 值 |
|------|-----|
| 账户 | KJ77452361 |
| CLI 路径 | `~/bin/gh` |
| 认证状态 | ✅ 已认证（Personal Access Token） |
| 可用操作 | repo, workflow, codespace, copilot 等 |

### GitHub 仓库
| 仓库 | 类型 |
|------|------|
| KJ77452361/ERP | private |
| KJ77452361/YIRXIT | private |
| KJ77452361/KK1 | private |
| KJ77452361/FPV-3D-print | public |
| KJ77452361/ERP-EXE-Distribution | public |

---

## 工具优先级

| 需求 | 优先 |
|------|------|
| 文件读写 | `read`/`write`/`edit` |
| SSH/SFTP | `exec` + sftp 命令 |
| 定时任务 | `cron` |
| 子任务 | `sessions_spawn` |
| 知识库检索 | `memory_search`/`memory_get` |
| 浏览器操作 | `browser` 工具 |
| PDF 处理 | `pdf` 工具 |

---

## 外部工具接入方式

### 豆包
- 类型：Windows 桌面 AI 助手
- 接入方式：OpenClaw 调度，结果回收写入 MyBrain
- 用途：快速问答、轻量任务、信息查询

### Hermes
- 类型：本地大模型客户端（NousResearch）
- 接入方式：OpenClaw 调度，Obsidian Local REST API 交互
- API 端点：`https://localhost:27124`
- 用途：深度分析、复杂推理、风险评估

### Codex++
- 类型：开发者 AI 编程工具
- 接入方式：OpenClaw 调度
- 用途：代码生成、项目构建、调试排错

---

*版本：v1.0.0*
*更新：2026-06-25*
