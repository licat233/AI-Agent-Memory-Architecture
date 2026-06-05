# ARMOR AI Workspace Architecture V5

## Version

Version: V5  
System: ARMOR AI Workspace  
Primary Agent: Hermes  
Knowledge Steward: Claudian  
Knowledge System: Obsidian  
Purpose: Long-term AI workspace memory architecture

---

# Table of Contents

1. Vision
2. First Principle: SSOT
3. System Roles
4. Memory Model
5. Vault Structure
6. Core Layer
7. Source of Truth Map
8. Facts Layer
9. Rules Layer
10. Insights Layer
11. Research Layer
12. Projects Layer
13. Indexes Layer
14. Temporary Layers
15. Archive Layer
16. Knowledge Triage Rules
17. Knowledge Promotion Framework
18. Conflict Resolution Policy
19. Permission Model
20. Write Speed Policy
21. Memory Write Pipeline
22. Agent Write Rules
23. Retrieval Rules
24. Knowledge Graph Metadata
25. Changelog Requirement
26. File Lifecycle
27. Review and Audit
28. Standard Templates
29. Operating Cadence
30. Success Criteria
31. Ultimate Principle

---

# 1. Vision

目标不是构建一个能记住所有内容的 AI。

目标是构建一个长期稳定、可治理、可扩展、可审计、可执行的 AI 工作系统。

系统必须保证：

- 永远知道事实在哪里
- 永远知道规则在哪里
- 永远知道经验在哪里
- 永远知道研究是否过期
- 永远知道项目是否结束
- 永远知道谁可以修改什么
- 永远知道知识如何晋升
- 永远知道冲突如何解决
- 永远知道什么是唯一权威版本

AI 可以无限生成。

知识库必须持续收敛。

---

# 2. First Principle: SSOT

SSOT = Single Source of Truth.

所有正式知识只能存在一个权威版本。

允许：

- 引用
- 双链
- 聚合视图
- Dataview
- 索引页
- Dashboard
- 摘要型入口

禁止：

- 内容复制
- 多版本事实
- 重复知识
- 平行真相
- 未声明来源的结论
- 已失效知识继续参与默认检索

错误示例：

```text
Product-A-v1.md
Product-A-v2.md
Product-A-final.md
Product-A-final-final.md
```

正确示例：

```text
Product-A.md
```

所有正式更新都发生在同一个权威文件中。

如果需要保留历史变化，使用：

- changelog
- timeline
- Git history
- append-only historical notes

不要用多个平行文件保存多个版本。

---

# 3. System Roles

## 3.1 Obsidian

角色：Knowledge System

职责：

- 长期知识存储
- 知识治理
- 知识演化
- 知识检索
- 知识审计
- 关系图谱维护

原则：

Vault 是唯一长期记忆。

Obsidian 不只是笔记库。

Obsidian 是 AI workspace 的知识操作系统。

---

## 3.2 Hermes

角色：Execution Agent

职责：

- 检索
- 分析
- 写作
- 自动化
- 项目执行
- 研究
- 草稿生成
- 初步分类建议

原则：

Hermes 负责生产内容。

Hermes 不定义真相。

Hermes 不拥有长期记忆。

Hermes 不直接修改核心资产。

所有长期知识必须来自 Vault 检索。

Hermes 可以写入低风险区域。

Hermes 修改高风险知识时，只能生成修改建议。

---

## 3.3 Claudian

角色：Knowledge Steward

职责：

- 分类
- 去重
- 重构
- 双链建设
- 知识审核
- 知识晋升
- 冲突解决
- SSOT 维护
- 过期知识处理
- 项目收尾萃取

原则：

Claudian 负责治理知识。

Claudian 不负责业务执行。

Claudian 是知识系统的守门人。

---

# 4. Memory Model

系统采用四层记忆模型。

---

## 4.1 Layer 1 — Working Memory

生命周期：单任务。

来源：

- 当前会话
- 当前项目
- 当前上下文
- 当前检索结果
- 当前用户输入

特点：

- 临时存在
- 任务结束后销毁
- 不自动成为长期知识
- 不自动参与未来检索

禁止：

- 未审核长期保存
- 直接写入核心知识
- 把临时推理当成事实

---

## 4.2 Layer 2A — Facts Memory

存放：

- 品牌事实
- 产品事实
- 客户事实
- 当前状态
- 已确认参数
- 已确认联系方式
- 已确认业务信息

特点：

- 唯一正确答案
- 有权威来源
- 可被审计
- 可被更新

Facts 分为两类：

### Current Facts

当前事实。

允许更新。

示例：

- 当前产品价格
- 当前品牌定位
- 当前客户目标
- 当前客户联系人
- 当前服务范围

### Historical Facts

历史事实。

默认 append-only。

禁止覆盖历史。

示例：

- 客户 2025 年的目标
- 某次会议中的决策
- 某个历史报价
- 某个项目阶段结果

原则：

当前状态可以覆盖。

历史事实只能追加、补充或标记纠正。

---

## 4.3 Layer 2B — Rules Memory

存放：

- SOP
- SEO 规则
- Social 规则
- Agent 规则
- 工作流
- 内容标准
- 审核标准
- 执行规范

特点：

- 描述应该如何做
- 具有复用价值
- 需要版本治理
- 修改必须审核

Rules 不是事实。

Rules 不是案例。

Rules 是未来执行的标准。

---

## 4.4 Layer 2C — Insights Memory

存放：

- Learnings
- Cases
- Patterns
- Postmortems
- Repeated observations

特点：

- 经验知识
- 不是事实
- 不是规则
- 必须经过验证
- 可以晋升为 Rule

Insights 分为：

```text
Cases = 发生了什么
Learnings = 为什么有效或失败
Patterns = 多次出现的现象
```

原则：

一次事件不是规则。

一次成功不是经验。

多次验证后才能成为 Learning。

稳定可复用后才能成为 Rule。

---

## 4.5 Layer 3 — Research Memory

存放：

- 市场研究
- 竞品研究
- 临时分析
- 外部资料
- 行业趋势
- SERP 分析
- 内容机会
- 技术调研

特点：

- 未成为正式知识
- 可能过期
- 需要来源
- 需要 review_date 或 expires_at
- 默认低于 Facts 和 Rules 的权威等级

Research 可以支持判断。

Research 不直接定义真相。

---

## 4.6 Layer 4 — Archive Memory

存放：

- 历史项目
- 历史研究
- 历史案例
- 失效规则
- 旧版本材料
- 关闭的客户记录
- 废弃方案

特点：

- 默认不参与检索
- 只在历史追溯时使用
- 可被引用，但不能作为当前事实
- 必须标记 archived 或 deprecated

Archive 是历史记录。

Archive 不是当前知识。

---

# 5. Vault Structure

```text
Vault/

00-Core/
01-Facts/
02-Rules/
03-Insights/
04-Research/
05-Projects/

80-Indexes/
90-Drafts/
91-Inbox/
92-Logs/
99-Archive/
```

原则：

- 00 到 05 是正式工作与知识层
- 80 是视图与索引层
- 90 到 92 是临时层
- 99 是历史层

---

# 6. Core Layer

位置：

```text
00-Core/
```

角色：系统宪法。

内容：

- 系统原则
- Agent 行为规范
- 决策原则
- 权限原则
- SSOT 原则
- 知识晋升原则
- 冲突处理原则
- Source of Truth Map

限制：

- 控制在 3000 字以内
- 只保留系统级原则
- 不保存具体品牌细节
- 不保存产品参数
- 不保存客户事实
- 不保存操作细节
- 不保存研究结论

Core Memory 是系统宪法。

不是百科全书。

---

## 6.1 Recommended Core Files

```text
00-Core/
  Core-Memory.md
  Source-of-Truth-Map.md
  Knowledge-Triage-Rules.md
  Conflict-Resolution-Policy.md
  Agent-Behavior-Rules.md
  Permission-Policy.md
```

---

# 7. Source of Truth Map

位置：

```text
00-Core/Source-of-Truth-Map.md
```

作用：

明确每类知识的唯一权威位置。

示例：

```markdown
# Source of Truth Map

| Knowledge | SSOT Location | Editable By | Review Required |
|---|---|---|---|
| Core principles | 00-Core/Core-Memory.md | Claudian | Yes |
| Brand positioning | 01-Facts/Brand/Positioning.md | Claudian | Yes |
| Brand voice | 01-Facts/Brand/Tone-of-Voice.md | Claudian | Yes |
| Product facts | 01-Facts/Products/ | Claudian | Yes |
| Customer current state | 01-Facts/Customers/{customer}/profile.md | Claudian | Yes |
| Customer history | 01-Facts/Customers/{customer}/timeline/ | Hermes append, Claudian review | Monthly |
| SEO rules | 02-Rules/SEO/ | Claudian | Yes |
| Social rules | 02-Rules/Social/ | Claudian | Yes |
| SOPs | 02-Rules/SOP/ | Claudian | Yes |
| Agent rules | 02-Rules/Agents/ | Claudian | Yes |
| Cases | 03-Insights/Cases/ | Hermes draft, Claudian review | Yes |
| Learnings | 03-Insights/Learnings/ | Claudian | Yes |
| Research | 04-Research/ | Hermes allowed | Review required |
| Projects | 05-Projects/ | Hermes allowed | Closeout required |
| Drafts | 90-Drafts/ | Hermes allowed | No |
| Inbox | 91-Inbox/ | Hermes allowed | Triage required |
| Logs | 92-Logs/ | Hermes allowed | No |
| Archive | 99-Archive/ | Claudian | No |
```

原则：

当不知道知识应该写在哪里时，先查 Source of Truth Map。

如果 Map 没有定义，写入 Inbox，等待 Triage。

---

# 8. Facts Layer

位置：

```text
01-Facts/
```

包含：

```text
01-Facts/
  Brand/
  Products/
  Customers/
```

作用：

保存已确认事实。

Facts 是“是什么”。

不是“怎么做”。

不是“为什么”。

---

## 8.1 Brand

位置：

```text
01-Facts/Brand/
```

存放：

- 品牌定位
- 品牌价值观
- 品牌语调
- 品牌视觉规则
- 品牌叙事
- 品牌禁用表达
- 品牌受众定义

原则：

Brand 是品牌事实的 SSOT。

Core Memory 只引用 Brand，不复制 Brand。

默认只读。

修改必须审核。

推荐结构：

```text
Brand/
  Positioning.md
  Tone-of-Voice.md
  Audience.md
  Visual-Guidelines.md
  Messaging.md
```

---

## 8.2 Products

位置：

```text
01-Facts/Products/
```

规则：

一个产品一个权威文件。

示例：

```text
Products/
  Armor-SEO.md
  Armor-AI.md
  Hermes-Agent.md
```

禁止：

```text
Armor-SEO-v2.md
Armor-SEO-new.md
Armor-SEO-final.md
```

产品文件保存：

- 产品定位
- 核心功能
- 当前价格
- 当前套餐
- 当前卖点
- 当前限制
- 目标客户
- 相关规则
- 相关案例

产品历史变化写入 changelog。

---

## 8.3 Customers

位置：

```text
01-Facts/Customers/
```

推荐结构：

```text
Customers/
  Acme/
    profile.md
    timeline/
      2025.md
      2026.md
    meetings/
      2026-01-10.md
      2026-03-15.md
    feedback/
      2026-Q1.md
      2026-Q2.md
    assets/
```

---

### profile.md

作用：

保存客户当前状态。

允许更新。

内容：

- 行业
- 商业模式
- 联系方式
- 当前目标
- 当前痛点
- 当前合作状态
- 当前负责人
- 当前风险
- 当前机会
- 当前服务范围

原则：

profile.md 代表“现在”。

历史变化必须同步记录到 timeline。

---

### timeline/

作用：

保存客户历史变化。

规则：append-only。

按年度拆分。

示例：

```text
timeline/
  2025.md
  2026.md
  2027.md
```

记录：

- 决策
- 合作事件
- 需求变化
- 预算变化
- 关键风险
- 关键里程碑
- 重要结论

禁止：

- 删除历史
- 覆盖历史
- 把当前判断伪装成历史事实

允许：

- 补充 correction
- 标记 obsolete
- 引用新的 SSOT

---

### meetings/

作用：

保存独立会议记录。

示例：

```text
meetings/
  2026-01-10.md
  2026-03-15.md
```

会议记录是原始记录。

会议记录不是客户当前状态。

如果会议产生新的当前事实，必须更新 profile.md。

---

### feedback/

作用：

保存周期性反馈。

示例：

```text
feedback/
  2026-Q1.md
  2026-Q2.md
```

反馈可以成为 Cases 或 Learnings 的来源。

---

# 9. Rules Layer

位置：

```text
02-Rules/
```

包含：

```text
02-Rules/
  SEO/
  Social/
  SOP/
  Agents/
  Content/
  Sales/
  Automation/
```

作用：

保存可复用执行标准。

Rules 是“应该如何做”。

不是“发生过什么”。

不是“某次为什么成功”。

---

## 9.1 Rule Requirements

每条 Rule 必须包含：

- 适用范围
- 执行步骤
- 判断标准
- 禁止事项
- 例外情况
- 相关事实
- 相关案例
- review_date
- owner
- changelog

Rule 修改必须审核。

过期 Rule 必须标记 deprecated 或 archived。

---

## 9.2 Rule Template

```markdown
---
type: rule
memory_layer: rules
status: active
authority: ssot
owner:
created:
updated:
review_date:
expires_at:
source:
confidence: high
write_policy: review_required
related:
tags:
---

# Rule Name

## Purpose

## Applies To

## Rule

## Procedure

## Do

## Do Not

## Exceptions

## Related Facts

## Related Cases

## Changelog
```

---

# 10. Insights Layer

位置：

```text
03-Insights/
```

包含：

```text
03-Insights/
  Cases/
  Learnings/
  Patterns/
  Postmortems/
```

作用：

保存经验知识。

Insights 是“我们从事情中学到了什么”。

不是事实库。

不是规则库。

---

## 10.1 Cases

位置：

```text
03-Insights/Cases/
```

记录：

- 发生了什么
- 谁参与
- 背景是什么
- 采取了什么行动
- 结果是什么
- 可观察证据是什么

原则：

案例不是规则。

案例不是事实。

案例只是事件与结果的记录。

案例可以支持 Learning。

---

## 10.2 Learnings

位置：

```text
03-Insights/Learnings/
```

记录：

- 为什么有效
- 为什么失败
- 在什么条件下成立
- 需要什么证据
- 适用边界是什么
- 是否可复用

Learning 必须经过验证。

一次观察不能成为 Learning。

推荐文件：

```text
Learnings/
  SEO-Learnings.md
  Content-Learnings.md
  Sales-Learnings.md
  Automation-Learnings.md
  Client-Learnings.md
```

---

## 10.3 Pattern Qualification

一个观察晋升为 Learning 前，至少满足以下条件之一：

- 多个项目重复出现
- 多个客户重复出现
- 有明确数据支持
- 有人工确认
- 有失败案例对照
- 被 Rule 使用过并证明有效

---

# 11. Research Layer

位置：

```text
04-Research/
```

结构：

```text
04-Research/
  00-Inbox/
  01-Reviewed/
  80-Reference/
  90-Review-Queue/
  99-Archive/
```

---

## 11.1 Research Inbox

位置：

```text
04-Research/00-Inbox/
```

Hermes 可直接写入。

特点：

- 未验证
- 未审核
- 不作为正式知识
- 默认低可信度
- 必须有来源

---

## 11.2 Reviewed Research

位置：

```text
04-Research/01-Reviewed/
```

特点：

- 已人工审核
- 允许检索
- 仍不等于事实
- 必须有 review_date
- 必须有 expires_at 或 next_review

---

## 11.3 Reference

位置：

```text
04-Research/80-Reference/
```

存放长期参考资料。

示例：

- 行业术语
- 技术背景
- 不频繁变化的外部资料
- 长期有效的分析框架

Reference 仍需要 review_date。

---

## 11.4 Research Review Queue

位置：

```text
04-Research/90-Review-Queue/
```

Research 默认 90 天后进入 Review Queue。

进入条件：

- review_date 到期
- expires_at 到期
- 90 天未被引用
- 来源失效
- 出现更新资料
- 被 agent 标记 uncertain

---

## 11.5 Research Archive

位置：

```text
04-Research/99-Archive/
```

存放：

- 过期研究
- 被替代研究
- 无效市场资料
- 旧竞品资料
- 失效 SERP 观察

默认不参与检索。

---

## 11.6 Expiration Rule

Research 不直接自动归档。

Research 默认 90 天后进入 Review Queue。

满足以下条件之一才归档：

- expires_at 已过
- 90 天未被引用
- owner 未续期
- 被 newer research 替代
- 明确标记为 outdated
- 来源已经失效
- 结论被正式 Facts 或 Rules 否定

---

# 12. Projects Layer

位置：

```text
05-Projects/
```

结构：

```text
05-Projects/
  Project-A/
  Project-B/
  Project-C/
```

项目区允许：

- 自由写作
- 自由实验
- 自由研究
- 临时分析
- 任务计划
- 输出草稿
- 客户交付材料

原则：

Projects 是工作区。

不是长期知识库。

项目结束后必须 closeout。

---

## 12.1 Project Structure

推荐结构：

```text
Project-A/
  brief.md
  plan.md
  research.md
  drafts/
  deliverables/
  notes/
  decisions.md
  closeout.md
```

---

## 12.2 Project Closeout

项目结束时执行：

```text
Project ends
↓
Closeout review
↓
Extract knowledge
↓
Promote to correct layer
↓
Archive project
```

必须萃取：

- 新事实 → Facts
- 客户变化 → Customer profile / timeline
- 事件记录 → Cases
- 可复用经验 → Learnings
- 可复用流程 → Rules
- 原始项目材料 → Archive

禁止项目结束后继续作为默认检索来源。

---

# 13. Indexes Layer

位置：

```text
80-Indexes/
```

作用：

提供聚合视图。

允许使用：

- Dataview
- 手动索引
- 双链索引
- Dashboard
- Review Queue

Indexes 可以引用内容。

Indexes 不复制权威内容。

推荐文件：

```text
80-Indexes/
  Products.md
  Customers.md
  Active-Projects.md
  SEO.md
  Rules.md
  Learnings.md
  Review-Queue.md
  Expiring-Research.md
  Orphan-Notes.md
  Duplicate-Candidates.md
  Deprecated-Knowledge.md
```

原则：

Index 是地图。

不是事实本身。

---

# 14. Temporary Layers

## 14.1 Drafts

位置：

```text
90-Drafts/
```

作用：保存草稿。

特点：

- 完全开放
- Hermes 可写入
- 不参与默认检索
- 可被删除
- 可被晋升

草稿不是知识。

草稿只是候选内容。

---

## 14.2 Inbox

位置：

```text
91-Inbox/
```

作用：保存未分类内容。

特点：

- 允许快速写入
- 等待 Triage
- 不作为正式知识
- 每周清理

进入 Inbox 的内容必须在 Review 中被处理为：

- 删除
- 归档
- 转成 Draft
- 转成 Research
- 转成 Project
- 晋升到正式知识层

---

## 14.3 Logs

位置：

```text
92-Logs/
```

作用：保存 agent 日志。

记录：

- Task
- Error
- Debug
- Tool result
- Automation failure
- Execution trace
- Batch operation summary

原则：

Logs 默认不参与知识检索。

Logs 不能直接成为长期知识。

但 Claudian 可从 Logs 中提取 recurring failure pattern，整理为：

- Automation Learning
- SOP update
- Agent Rule update

禁止直接把原始 Logs 作为正式知识。

---

# 15. Archive Layer

位置：

```text
99-Archive/
```

包含：

- 历史项目
- 历史研究
- 历史规则
- 历史案例
- 失效材料
- 关闭客户
- 废弃方案

原则：

Archive 默认不参与检索。

Archive 只用于历史追溯。

Archive 中的内容不能作为当前事实。

如果 Archive 中的信息重新变得有用，必须重新 Review 后再恢复。

---

# 16. Knowledge Triage Rules

位置：

```text
00-Core/Knowledge-Triage-Rules.md
```

所有写入前必须先判断知识类型。

---

## 16.1 Step 1 — Classify

判断内容属于哪一类：

```text
Current truth → Facts
Historical event → Timeline / Cases
How-to instruction → Rules
Repeated verified pattern → Learnings
External uncertain info → Research
Work-in-progress → Projects / Drafts
System principle → Core
Unclear content → Inbox
```

---

## 16.2 Step 2 — Check SSOT

写入前必须判断：

是否已有权威版本？

如果有：

- 更新原文件
- 添加 changelog
- 关联来源
- 不创建平行版本

如果没有：

- 根据 Source of Truth Map 创建新文件
- 添加完整 metadata
- 设置 owner 和 review_date

---

## 16.3 Step 3 — Check Permission

判断目标位置属于哪一类权限：

- Class A：只读，必须审核
- Class B：可新增，需规范
- Class C：完全开放

如果是 Class A：

Hermes 只能生成修改建议。

不能直接覆盖。

---

## 16.4 Step 4 — Write or Propose

根据权限执行：

```text
Fast-write area → 直接写入
Review-required area → 生成修改建议
Unknown area → 写入 Inbox
```

---

# 17. Knowledge Promotion Framework

知识必须晋升。

但晋升不是单一路径。

错误模型：

```text
Draft
↓
Research
↓
Learning
↓
Rule
↓
Core Memory
```

正确模型：

```text
Draft / Inbox / Project
↓
Triage
↓
Facts / Rules / Cases / Research / Projects
↓
Validated Learning
↓
Reusable Rule
↓
Core Memory, only if system-level and stable
```

---

## 17.1 Draft → Facts

适用于：

- 已确认产品信息
- 已确认品牌信息
- 已确认客户当前状态

要求：

- 有来源
- 有 owner
- 有 review
- 确认无现有 SSOT 冲突

---

## 17.2 Draft → Research

适用于：

- 外部资料
- 市场观察
- 竞品研究
- 未验证假设

要求：

- 有 source
- 有 confidence
- 有 review_date
- 有 expires_at

---

## 17.3 Project → Case

适用于：

- 完成项目
- 明确行动和结果
- 有可追溯证据

---

## 17.4 Case → Learning

适用于：

- 多个案例支持
- 有明确复用价值
- 有边界条件
- 有人工确认

---

## 17.5 Learning → Rule

适用于：

- 可稳定复用
- 可指导未来执行
- 有清晰步骤
- 有适用范围
- 有例外情况

---

## 17.6 Rule → Core Memory

适用于：

- 系统级原则
- 长期稳定
- 跨项目适用
- 跨 agent 适用
- 高度抽象
- 不依赖具体业务细节

Core Memory 只能收录原则。

不能收录细节。

---

# 18. Conflict Resolution Policy

位置：

```text
00-Core/Conflict-Resolution-Policy.md
```

SSOT 的难点不是只有一个文件。

SSOT 的难点是冲突时如何判断。

---

## 18.1 Authority Priority

当两个来源冲突时，按以下优先级判断：

```text
1. Core Memory
2. Approved Rules
3. Approved Facts SSOT
4. Customer profile current state
5. Timeline / meeting notes
6. Reviewed Research
7. Project notes
8. Drafts / Inbox
9. Logs
```

说明：

Core Memory 只对系统原则有最高权威。

Core Memory 不覆盖具体品牌、产品、客户事实。

具体事实仍以对应 Facts SSOT 为准。

---

## 18.2 Conflict Handling

如果发现冲突：

1. 不直接删除任何原始记录
2. 找到对应 SSOT 文件
3. 判断冲突来源
4. 更新当前结论
5. 添加 source
6. 添加 changelog
7. 必要时创建 conflict note
8. 标记低权威内容为 outdated 或 superseded

---

## 18.3 Conflict Note

位置：

```text
91-Inbox/Conflicts/
```

或：

```text
80-Indexes/Conflict-Queue.md
```

格式：

```markdown
---
type: conflict
status: open
owner:
created:
related:
---

# Conflict Title

## Conflict

## Source A

## Source B

## Current SSOT

## Proposed Resolution

## Decision

## Changelog
```

---

# 19. Permission Model

系统采用三类权限。

---

## 19.1 Class A — Core Assets

包含：

- Core Memory
- Source of Truth Map
- Brand
- Products
- Rules
- Agent behavior rules
- Permission policy

权限：

- 默认只读
- Hermes 不能直接覆盖
- 修改必须审核
- 必须有 changelog
- 必须有 source
- 必须有 owner

Hermes 行为：

```text
Generate proposal only.
Do not overwrite.
```

---

## 19.2 Class B — Knowledge Assets

包含：

- Customers
- Cases
- Learnings
- Research
- Projects
- Reviewed notes

权限：

- 允许新增
- 遵循结构规范
- 关键字段修改需审核
- Learnings 晋升需审核
- Customer profile 修改需审核
- Timeline append 可快速写入

Hermes 行为：

```text
May create.
May append.
Need review for current-state changes.
```

---

## 19.3 Class C — Temporary Assets

包含：

- Drafts
- Inbox
- Logs
- Project working drafts
- Research inbox

权限：

- 完全开放
- Hermes 可直接写入
- 不参与正式检索
- 必须定期清理

Hermes 行为：

```text
Free write allowed.
No authority.
```

---

# 20. Write Speed Policy

为了避免治理过重，系统区分 Fast Path 和 Controlled Path。

---

## 20.1 Fast Path

允许快速写入：

- Drafts
- Inbox
- Logs
- Project working notes
- Meeting notes
- Timeline append
- Research inbox

特点：

- 写入快
- 权威低
- 后续需要 Triage
- 不自动成为正式知识

---

## 20.2 Controlled Path

必须审核：

- Core Memory
- Brand
- Products
- Rules
- Customer profile
- Learnings
- Reviewed Research
- Source of Truth Map
- Permission Policy

特点：

- 写入慢
- 权威高
- 必须有来源
- 必须有 changelog
- 必须有 owner

---

# 21. Memory Write Pipeline

禁止直接写入核心知识。

统一流程：

```text
Hermes
↓
Draft / Inbox / Project / Research Inbox
↓
Triage
↓
Review
↓
Promote
↓
Merge into SSOT
↓
Changelog
```

---

## 21.1 Stage 1 — Create

Hermes 输出内容。

可进入：

- Drafts
- Inbox
- Projects
- Research Inbox
- Meeting Notes
- Logs

---

## 21.2 Stage 2 — Triage

Claudian 判断：

- 这是事实？
- 这是规则？
- 这是经验？
- 这是案例？
- 这是研究？
- 这是项目材料？
- 是否已有 SSOT？
- 是否重复？
- 是否过期？
- 是否需要审核？

---

## 21.3 Stage 3 — Review

Claudian 审核：

- 是否准确
- 是否重复
- 是否已有权威版本
- 是否有来源
- 是否有 owner
- 是否需要过期时间
- 是否违反 SSOT
- 是否应该归档

---

## 21.4 Stage 4 — Promote

符合条件后晋升到：

- Facts
- Rules
- Insights
- Research Reviewed
- Indexes
- Archive

---

## 21.5 Stage 5 — Merge

如果目标是已有 SSOT：

- 更新原文件
- 不创建新版本
- 添加 changelog
- 添加 related
- 添加 source
- 更新 updated
- 更新 review_date

---

# 22. Agent Write Rules

Hermes 写入前必须执行以下判断。

---

## 22.1 Step 1 — What is this?

```text
Fact?
Rule?
Learning?
Case?
Research?
Project material?
Draft?
Log?
```

---

## 22.2 Step 2 — Is there an existing SSOT?

如果有：

- 不创建新文件
- 生成更新建议
- 引用原文件
- 等待审核

如果没有：

- 根据 Source of Truth Map 创建
- 添加 metadata
- 标记 status

---

## 22.3 Step 3 — Is it a Core Asset?

如果是：

- 不自动覆盖
- 只生成 proposal
- 标明 changed sections
- 标明 reason
- 标明 source

---

## 22.4 Step 4 — Does it need expiration?

以下内容必须有 expires_at 或 review_date：

- Research
- SEO 资料
- 竞品资料
- 市场趋势
- 技术工具信息
- 平台规则
- 价格信息
- 外部资料

---

## 22.5 Step 5 — Does it need source?

以下内容必须有 source：

- Facts
- Rules
- Research
- Learnings
- Customer profile changes
- Product changes
- Brand changes

没有 source 的内容只能进入 Draft 或 Inbox。

---

# 23. Retrieval Rules

任务开始时，优先加载：

```text
1. Core Memory
2. Source of Truth Map
3. Relevant Facts
4. Relevant Rules
5. Relevant Learnings
6. Relevant Reviewed Research
7. Active Project context
```

然后按需检索。

禁止：

- 加载整个 Vault
- 默认检索 Archive
- 默认检索 Logs
- 把 Draft 当成事实
- 把 Research 当成事实
- 把 Case 当成规则
- 把 Meeting Note 当成 Customer Current State

---

## 23.1 Retrieval Priority

检索优先级：

```text
1. Core system principles
2. Facts SSOT
3. Approved Rules
4. Customer current profile
5. Active project files
6. Learnings
7. Cases
8. Reviewed Research
9. Raw Research
10. Drafts
11. Archive
12. Logs
```

Archive、Logs、Drafts 只有在明确需要时才检索。

---

# 24. Knowledge Graph Metadata

所有正式知识统一 Frontmatter。

---

## 24.1 Standard Metadata

```yaml
type:
memory_layer:
status:
authority:
owner:
created:
updated:
review_date:
expires_at:
source:
confidence:
write_policy:
related:
tags:
```

---

## 24.2 Field Definitions

### type

文档类型。

示例：

```yaml
type: product
type: customer_profile
type: rule
type: case
type: learning
type: research
type: project
type: index
type: log
```

### memory_layer

所属记忆层。

```yaml
memory_layer: core
memory_layer: facts
memory_layer: rules
memory_layer: insights
memory_layer: research
memory_layer: projects
memory_layer: draft
memory_layer: inbox
memory_layer: logs
memory_layer: archive
```

### status

生命周期状态。

```yaml
status: draft
status: active
status: needs_review
status: deprecated
status: archived
status: superseded
```

### authority

权威等级。

```yaml
authority: ssot
authority: approved
authority: reference
authority: provisional
authority: raw
```

### owner

负责人。

```yaml
owner: claudian
owner: armor
owner: hermes
```

### source

来源。

```yaml
source:
  - user-confirmed
  - meeting/2026-03-15
  - project/project-a
  - research/competitor-analysis
```

### confidence

可信度。

```yaml
confidence: high
confidence: medium
confidence: low
confidence: unknown
```

### write_policy

写入权限。

```yaml
write_policy: review_required
write_policy: append_only
write_policy: open
write_policy: read_only
```

---

## 24.3 Example Metadata

```yaml
---
type: product
memory_layer: facts
status: active
authority: ssot
owner: claudian
created: 2026-01-01
updated: 2026-06-05
review_date: 2026-12-01
expires_at:
source:
  - founder-confirmed
confidence: high
write_policy: review_required
related:
  - rule/seo-content
  - customer/acme
tags:
  - seo
  - product
---
```

---

# 25. Changelog Requirement

所有 Class A 文件必须有 Changelog。

推荐格式：

```markdown
## Changelog

| Date | Change | Source | Approved By |
|---|---|---|---|
| 2026-06-05 | Updated product positioning | Founder note | Claudian |
```

Class B 文件建议有 Changelog。

Class C 文件不要求。

---

# 26. File Lifecycle

所有正式知识都必须有生命周期状态。

---

## 26.1 draft

草稿。

不参与正式检索。

---

## 26.2 active

当前有效。

可参与检索。

---

## 26.3 needs_review

需要审核。

可以谨慎检索，但不能作为最终权威。

---

## 26.4 deprecated

已废弃。

默认不参与检索。

可以用于历史解释。

---

## 26.5 archived

已归档。

默认不参与检索。

---

## 26.6 superseded

已被替代。

必须指向替代文件。

示例：

```yaml
status: superseded
superseded_by: 01-Facts/Products/Armor-SEO.md
```

---

# 27. Review and Audit

## 27.1 Knowledge Review

每月执行 Knowledge Review。

检查：

- 重复文件
- 孤立文档
- 未分类内容
- 失效研究
- needs_review 文件
- Inbox 堆积
- Drafts 堆积
- 缺少 metadata 的正式文件
- 过期 review_date
- 失效 source

输出：

```text
80-Indexes/Review-Queue.md
```

---

## 27.2 Knowledge Audit

每季度执行 Knowledge Audit。

检查：

- SSOT 完整性
- Core Memory 体积
- Rule 有效性
- Learning 时效性
- Metadata 完整性
- Graph 连接质量
- Research 过期情况
- Archive 是否误参与检索
- Projects 是否完成 closeout
- Source of Truth Map 是否完整

输出：

```text
80-Indexes/Quarterly-Audit.md
```

---

## 27.3 Review Queues

推荐维护以下队列：

```text
80-Indexes/Review-Queue.md
80-Indexes/Expiring-Research.md
80-Indexes/Needs-Source.md
80-Indexes/Needs-Owner.md
80-Indexes/Duplicate-Candidates.md
80-Indexes/Orphan-Notes.md
80-Indexes/Conflict-Queue.md
80-Indexes/Deprecated-Knowledge.md
```

---

# 28. Standard Templates

## 28.1 Product Template

```markdown
---
type: product
memory_layer: facts
status: active
authority: ssot
owner: claudian
created:
updated:
review_date:
expires_at:
source:
confidence: high
write_policy: review_required
related:
tags:
---

# Product Name

## Positioning

## Target Customer

## Core Features

## Current Offer

## Pricing

## Use Cases

## Limitations

## Related Rules

## Related Cases

## Changelog

| Date | Change | Source | Approved By |
|---|---|---|---|
```

---

## 28.2 Customer Profile Template

```markdown
---
type: customer_profile
memory_layer: facts
status: active
authority: ssot
owner: claudian
created:
updated:
review_date:
expires_at:
source:
confidence:
write_policy: review_required
related:
tags:
---

# Customer Name

## Current Status

## Industry

## Business Model

## Contacts

## Current Goals

## Current Pain Points

## Current Services

## Risks

## Opportunities

## Related Timeline

## Related Meetings

## Changelog

| Date | Change | Source | Approved By |
|---|---|---|---|
```

---

## 28.3 Meeting Note Template

```markdown
---
type: meeting_note
memory_layer: facts
status: active
authority: raw
owner: hermes
created:
updated:
review_date:
expires_at:
source:
confidence: medium
write_policy: append_only
related:
tags:
---

# Meeting Title

## Date

## Attendees

## Context

## Discussion

## Decisions

## Action Items

## Potential Fact Updates

## Potential Learnings
```

---

## 28.4 Research Template

```markdown
---
type: research
memory_layer: research
status: needs_review
authority: provisional
owner: hermes
created:
updated:
review_date:
expires_at:
source:
confidence:
write_policy: open
related:
tags:
---

# Research Title

## Question

## Context

## Sources

## Findings

## Analysis

## Limitations

## Expiration Risk

## Recommended Next Step
```

---

## 28.5 Case Template

```markdown
---
type: case
memory_layer: insights
status: active
authority: approved
owner:
created:
updated:
review_date:
expires_at:
source:
confidence:
write_policy: review_required
related:
tags:
---

# Case Title

## Background

## What Happened

## Actions Taken

## Result

## Evidence

## Related Facts

## Related Research

## Possible Learning
```

---

## 28.6 Learning Template

```markdown
---
type: learning
memory_layer: insights
status: active
authority: approved
owner: claudian
created:
updated:
review_date:
expires_at:
source:
confidence:
write_policy: review_required
related:
tags:
---

# Learning Title

## Claim

## Why It Matters

## Evidence

## Conditions Where It Applies

## Conditions Where It Does Not Apply

## Related Cases

## Related Rules

## Should This Become a Rule?
```

---

## 28.7 Rule Template

```markdown
---
type: rule
memory_layer: rules
status: active
authority: ssot
owner: claudian
created:
updated:
review_date:
expires_at:
source:
confidence: high
write_policy: review_required
related:
tags:
---

# Rule Name

## Purpose

## Applies To

## Rule

## Procedure

## Do

## Do Not

## Exceptions

## Related Facts

## Related Cases

## Changelog

| Date | Change | Source | Approved By |
|---|---|---|---|
```

---

## 28.8 Project Closeout Template

```markdown
---
type: project_closeout
memory_layer: projects
status: needs_review
authority: provisional
owner:
created:
updated:
review_date:
expires_at:
source:
confidence:
write_policy: review_required
related:
tags:
---

# Project Closeout

## Project Summary

## Goals

## Work Completed

## Results

## Decisions Made

## New Facts to Promote

## Cases to Create

## Learnings to Extract

## Rules to Update

## Materials to Archive

## Final Status
```

---

# 29. Operating Cadence

## Daily

Hermes may write to:

- Drafts
- Inbox
- Project notes
- Research inbox
- Logs

Hermes should not modify:

- Core
- Brand
- Products
- Rules

---

## Weekly

Claudian reviews:

- Inbox
- Drafts
- Research inbox
- Active project notes
- Conflict queue

Actions:

- delete noise
- classify useful notes
- merge duplicates
- promote valid knowledge
- archive low-value material

---

## Monthly

Run Knowledge Review.

Check:

- review queues
- orphan notes
- duplicate candidates
- expiring research
- missing metadata
- open conflicts

---

## Quarterly

Run Knowledge Audit.

Check:

- SSOT integrity
- rule validity
- Core Memory size
- archive boundaries
- project closeouts
- metadata completeness
- graph quality

---

# 30. Success Criteria

系统运行 12 个月后，必须能够在 30 秒内定位：

- 品牌定位
- 产品参数
- 客户当前状态
- 客户历史变化
- SEO 规范
- Social 规范
- SOP
- Agent 行为规则
- 核心经验
- 项目记录
- 研究来源
- 失效知识
- 当前权威版本

必须能够明确回答：

```text
什么是事实？
什么是规则？
什么是经验？
什么是研究？
什么是草稿？
什么已经失效？
什么是当前版本？
谁可以修改？
来源是什么？
何时需要复审？
```

如果不能回答，说明知识治理失败。

---

# 31. Ultimate Principle

事实只有一个版本。

规则只有一个来源。

经验必须经过验证。

研究必须允许过期。

项目必须允许结束。

历史必须可以追溯。

冲突必须可以解决。

权限必须可以执行。

核心记忆必须持续精简。

AI 可以无限生成。

知识库必须持续收敛。
