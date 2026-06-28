---
name: agent-coordinator
description: CEO 多 Agent 协调 — 派发任务、收集结果、汇总报告
version: 1.0.0
metadata:
  openclaw:
    always: false
---

# Agent Coordinator

CEO 的多 Agent 协调引擎。通过 `sessions_spawn` 和 `sessions_send` 协调子 Agent 工作。

## Agent 架构（v3.0.0 精简版）

```
CEO（唯一入口）
├─ COO（运营）─── PM / QM / RS / SA
├─ CTO（技术）─── PE / HE / SE / architect / fullstack_engineer / qa_engineer
├─ CA（合规）
└─ main（系统入口）

业务执行层（workspace/agents/）
└─ sales_executive / sales_operator / sales_orchestrator / translator_zh
```

## 协调流程

### 1. 任务派发
```
sessions_spawn(
  task: "具体任务描述",
  taskName: "唯一标识",
  runtime: "subagent",
  mode: "run"
)
```

### 2. 等待完成
```
sessions_yield(message: "等待子 Agent 完成...")
```

### 3. 结果汇总
收到完成事件后，收集结果并汇总报告。

## 子 Agent 调用规范

| Agent ID | 专长 | 适用场景 | 汇报线 |
|----------|------|---------|--------|
| coo | 运营协调 | 项目进度、资源调配 | CEO |
| cto | 技术架构 | 系统设计、技术选型 | CEO |
| pm | 项目管理 | 任务分解、进度跟踪 | COO |
| qm | 质量保障 | 代码审查、测试验证 | COO |
| rs | 供应链 | 采购、库存管理 | COO |
| sa | 市场分析 | 竞争情报、商业分析 | COO |
| pe | 产品工程 | 结构/DFM | CTO |
| he | 硬件工程 | 电路/PCB | CTO |
| se | 软件工程 | 软件开发 | CTO |
| architect | 架构设计 | 系统架构、技术选型 | CTO |
| fullstack_engineer | 全栈开发 | 前端/后端/全栈 | CTO |
| qa_engineer | 测试质量 | 测试策略、自动化 | CTO |
| ca | 合规审查 | 政策合规、风险评估 | CEO |

## 禁止

- ❌ 不在群聊中共享子 Agent 的私人上下文
- ❌ 不派发需要 CEO 亲自处理的敏感任务给子 Agent
- ❌ 不期望子 Agent 有跨 Agent 的全局视角

---

*version 1.0.0 · King · 2026-06-27 · v3.0.0 精简版架构*