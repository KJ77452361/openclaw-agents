---
name: quality-metrics
description: 质量指标统计与分析 — 收集、整理质量数据，生成质量报告
version: 1.0.0
metadata:
  openclaw:
    requires: []
    tags: [quality, metrics, data, COO]
---

# Quality Metrics

> Skill: quality-metrics | v1.0.0 | for: qm
> 适用场景：质量数据收集、指标统计、质量报告生成、合规性评估

## 描述

收集、整理和分析 OpenClaw 生态的质量数据，生成量化的质量报告。
用于 COO 域的质量管理，为 CEO 提供数据支撑的决策依据。

## 前置条件

- 了解 OpenClaw 的质量维度（效率/合规/稳定性/用户满意度）
- 能读取 `system/受控文件清单.md`、`daily/`、`memory/` 等数据源

## 输入

| 字段 | 类型 | 说明 |
|------|------|------|
| metric_type | string | 指标类型：compliance（合规）/ efficiency（效率）/ stability（稳定性）|
| period | string | 统计周期：daily / weekly / monthly |
| output_format | string | 输出格式：brief（简要）/ full（完整）|

## 使用方法

### 触发方式

在 qm session 中调用：

```
请生成 {period} 质量指标报告
指标类型：{compliance/efficiency/stability}
输出格式：{brief/full}
```

## 输出格式

### 合规性报告（compliance）

```markdown
# 质量指标报告：合规性 — {YYYY-MM-DD}

> 统计周期：{period}
> 统计日期：{YYYY-MM-DD}

## 核心指标

| 指标 | 目标 | 实际 | 达标 |
|------|------|------|------|
| 受控文件合规率 | 100% | X% | ✅/❌ |
| frontmatter 完整率 | 100% | X% | ✅/❌ |
| 版本 footer 合规率 | 100% | X% | ✅/❌ |
| 敏感信息泄露数 | 0 | X | ✅/❌ |

## 趋势分析
<!-- 与上一周期对比 -->

## 异常项
| 文件 | 问题 | 修复建议 |
|------|------|---------|
| ... | ... | ... |

## 下周重点
- [ ] ...
```

### 效率报告（efficiency）

```markdown
# 质量指标报告：效率 — {YYYY-MM-DD}

> 统计周期：{period}

## 核心指标

| 指标 | 基准 | 实际 | 变化 |
|------|------|------|------|
| 日均 Token 消耗 | X | Y | +Z%/-Z% |
| 平均响应时间 | Xms | Yms | +Zms/-Zms |
| 任务完成率 | 90% | X% | +Y%/-Y% |

## 趋势分析
<!-- 图表式文字描述 -->

## 异常分析
<!-- 效率明显下降的时段/任务分析 -->

## 建议
- [ ] ...
```

## 限制

- 仅输出客观数据和分析，不做主观评价
- 不做预测性分析（那是战略分析的职责）
- 质量报告仅供 COO/CEO 决策参考，最终决策由 CEO 做出

## 示例

### 示例：周合规报告

**输入：**
```
请生成本周合规性质量报告
指标类型：compliance
统计周期：weekly
输出格式：full
```

**输出：**
```
# 质量指标报告：合规性 — 2026-W26

> 统计周期：2026-06-23 ~ 2026-06-29
> 统计日期：2026-06-29

## 核心指标

| 指标 | 目标 | 实际 | 达标 |
|------|------|------|------|
| 受控文件合规率 | 100% | 98% | ⚠️ |
| frontmatter 完整率 | 100% | 100% | ✅ |
| 版本 footer 合规率 | 100% | 100% | ✅ |
| 敏感信息泄露数 | 0 | 0 | ✅ |

## 异常项
| 文件 | 问题 | 修复建议 |
|------|------|---------|
| agents/vp1/MEMORY.md | 版本记录缺失 | 补录版本记录 |

## 下周重点
- [ ] 修复 vp1 MEMORY.md 版本记录
- [ ] 对 workspace/agents/ 再做一次合规检查
```
