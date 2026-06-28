---
name: strategic-analysis
description: 战略分析与规划 — 分析外部环境、评估内部能力、制定战略方向
version: 1.0.0
metadata:
  openclaw:
    requires: []
    tags: [strategy, analysis, planning, CA]
---

# Strategic Analysis

> Skill: strategic-analysis | v1.0.0 | for: ca
> 适用场景：战略方向评估、外部环境分析、内部能力评估、战略规划

## 描述

对 OpenClaw 生态的战略方向进行分析，评估外部机会与威胁、内部优势与劣势，
提出战略建议。为 CEO 的战略决策提供数据支撑和可选方案。

## 前置条件

- 了解 OpenClaw 生态的整体架构和现状（参考 `knowledge/system/agents.md`）
- 能获取质量指标（从 qm 的 quality-metrics skill）
- 能获取效率数据（从 cron 输出）

## 输入

| 字段 | 类型 | 说明 |
|------|------|------|
| focus_area | string | 分析焦点：growth（增长）/ efficiency（效率）/ stability（稳定性）|
| scenario | string | 分析场景：opportunity（机会）/ risk（风险）/ decision（决策）|
| data_horizon | string | 数据范围：current（当前）/ 3month（3个月）/ 6month（6个月）|

## 使用方法

### 触发方式

在 ca session 中调用：

```
请对 {焦点领域} 进行战略分析
分析场景：{opportunity/risk/decision}
数据范围：{current/3month/6month}
```

## 输出格式

```markdown
# 战略分析报告：{焦点} — {YYYY-MM-DD}

> 分析场景：{scenario}
> 数据范围：{horizon}
> 分析日期：{YYYY-MM-DD}

## 1. 现状评估
<!-- 当前 OpenClaw 生态在该领域的状态 -->

## 2. SWOT 分析
| 维度 | 内容 |
|------|------|
| 优势 S | ... |
| 劣势 W | ... |
| 机会 O | ... |
| 威胁 T | ... |

## 3. 外部环境分析
<!-- PEST 或波特五力框架 -->

## 4. 战略选项

| 选项 | 描述 | 资源需求 | 风险 | 收益 |
|------|------|---------|------|------|
| A | ... | 低/中/高 | 低/中/高 | 低/中/高 |
| B | ... | 低/中/高 | 低/中/高 | 低/中/高 |

## 5. 推荐方案
| 推荐 | 理由 |
|------|------|
| 方案 X | ... |

## 6. 实施路径
1. ...
2. ...
3. ...

## 7. 监控指标
| 指标 | 目标 | 告警阈值 |
|------|------|---------|
| ... | ... | ... |
```

## 限制

- 不做具体执行（那是 COO/CTO 的职责）
- 不做最终决策（那是 CEO 的职责）
- 战略分析仅提供选项和建议

## 示例

### 示例：生态增长战略分析

**输入：**
```
请对 OpenClaw 的生态扩展进行战略分析
分析场景：opportunity
焦点领域：growth
数据范围：3month
```

**输出：**
```
# 战略分析报告：生态扩展 — 2026-06-27

## 1. 现状评估
- OpenClaw 生态已标准化 v3.0.0
- 21 个 Agent 正常运行
- 15 个 SOP/WF 覆盖核心流程
- CTO/COO/CA 域 Skills 正在部署

## 2. SWOT
| 维度 | 内容 |
|------|------|
| 优势 S | 自动化程度高、自进化机制健全 |
| 劣势 W | 外部工具集成仍需完善 |
| 机会 O | 多 Agent 协作需求增长 |
| 威胁 T | 生态复杂度上升带来的维护成本 |

## 3. 战略选项
| 选项 | 描述 | 风险 | 收益 |
|------|------|------|------|
| A：扩展外部集成 | 深度集成 Codex++、更多 API | 中 | 高 |
| B：深化内部能力 | 完善自进化、做深知识库 | 低 | 中 |

## 5. 推荐方案
**推荐方案 A** — 扩展外部集成

理由：
1. 外部工具集成是当前最大短板（参考 QL_SOP_001）
2. Codex++ 集成后可大幅提升开发效率
3. 收益 > 风险

## 6. 实施路径
1. Q1：完成 Codex++ 集成（COOs 支持）
2. Q2：完善 Feishu failure destination 配置
3. Q3：扩展更多 API 集成
```
