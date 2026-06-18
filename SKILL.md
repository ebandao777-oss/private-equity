---
name: private-equity
description:
  股权投资技能套件：条款审查、尽调清单、投决备忘录、回报测算、项目筛选、退出分析。
  条款审查: 条款审查, 审TS, 审SPA, term sheet; 尽调清单: 尽调清单, due diligence, DD checklist; 投决备忘录: 投决备忘录, IC memo, 投委会; 回报测算: 回报测算, 算IRR, 回报率, MOIC; 项目筛选: 项目筛选, deal sourcing, 项目初筛; 退出分析: 退出分析, 退出路径, IPO退出。
version: "1.0.1"
author: "智慧半岛"
---

# private-equity -- 股权投资综合技能

本技能是一个综合技能套件，包含多个子技能。接到用户请求后，按以下流程执行。

## 执行流程

### Step 1: 意图识别与路由匹配

分析用户输入，与下方路由表逐一比对。匹配规则：
- 用户输入中包含路由表中「子技能」列的关键词 → 匹配该子技能
- 用户输入中包含路由表中「功能说明」列中提到的场景 → 匹配该子技能
- 多个子技能同时匹配时，选择匹配度最高的
- 无法唯一确定时，向用户确认意图

### Step 2: 加载子技能模板

匹配到子技能后，根据子技能索引表找到对应的文件路径，**必须**使用 `read_text` 工具读取 `references/` 目录下的完整执行模板。

### Step 3: 按模板执行

严格按照加载的模板逐步执行。模板中定义了：
- 输入要求（用户需要提供什么）
- 执行步骤（每一步做什么、如何判断）
- 输出格式（最终产出的结构和规范）
- 质量标准（产出必须满足的底线）

### Step 4: 输出结果

按模板规定的格式输出结果。如果模板要求生成文件，写入后声明产出物。

## 约束规则

1. **必须先读模板再执行**：匹配到子技能后，严禁凭记忆或猜测执行，必须先读取对应的 references 文件
2. **严格遵循模板**：不得跳过步骤、不得省略检查项、不得自行简化流程
3. **输入不足时主动索取**：模板中标注「必填」的输入项缺失时，向用户索取
4. **质量底线不妥协**：模板中的质量标准必须逐条满足

## 路由表

| 子技能 | 功能说明 |
|--------|----------|
| 审条款 | TS/SPA文件 --> 条款审查报告，逐项评估风险等级并给出谈判建议（含九... |
| 尽调清单 | 项目描述 --> 结构化尽调清单（财务/法律/业务/技术+行业专项+架构专项）... |
| 投决备忘录 | 项目信息+尽调发现 --> 投委会IC Memo... |
| 测收益 | 交易条款+退出假设 --> IRR/MOIC/DPI测算结果... |
| 筛项目 | BP/CIM --> 一页项目筛选备忘录... |
| 退出分析 | 被投公司现状 --> 退出路径对比报告（IPO/并购/S基金/回购/清算）... |

## 子技能索引

| 子技能 | 英文标识 | 文件 |
|--------|----------|------|
| 审条款 | `term-sheet-review` | [references/term-sheet-review.md](./references/term-sheet-review.md) |
| 尽调清单 | `due-diligence-checklist` | [references/due-diligence-checklist.md](./references/due-diligence-checklist.md) |
| 投决备忘录 | `investment-memo` | [references/investment-memo.md](./references/investment-memo.md) |
| 测收益 | `return-modeling` | [references/return-modeling.md](./references/return-modeling.md) |
| 筛项目 | `deal-screening` | [references/deal-screening.md](./references/deal-screening.md) |
| 退出分析 | `exit-analysis` | [references/exit-analysis.md](./references/exit-analysis.md) |
## 跨技能协同指引

| 协同技能 | 典型场景 |
|---------|---------|
| 投研分析 | 尽调前先做行业研究和可比公司分析 |
| 企业法务 | 条款审查和尽调清单需配合法务风险评估 |
| 企业财税 | 回报测算需配合财税做税务影响分析 |

> 以上为推荐协同路径。执行复合任务时，请根据实际需求灵活组合。

## 变更日志

### v1.0.1 (2026-06-19)
- 对齐 description 子技能名与路由表名称
- 压缩路由表说明列至40字以内
- 新增跨技能协同指引章节
- 删除冗余英文 description 行