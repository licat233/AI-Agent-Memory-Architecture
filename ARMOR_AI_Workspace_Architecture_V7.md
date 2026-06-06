# ARMOR AI Workspace Architecture V7

## Version

Version: V7  
System: ARMOR AI Workspace  
Primary Agent / Protocol: Hermes  
Knowledge Runtime: Claudian  
Knowledge System: Obsidian Vault  
Purpose: Long-term AI workspace memory architecture  
Status: Proposed complete architecture  
Primary Upgrade from V6: Runtime retrieval, context packing, schema validation, evidence layer, memory evaluation, security and retention governance

---

# Table of Contents

1. Vision
2. First Principle: SSOT
3. System Roles
4. Claudian Runtime Model
5. Hermes Operating Protocol
6. Memory Model
7. Vault Structure
8. Core Layer
9. Source of Truth System
10. Facts Layer
11. Rules Layer
12. Insights Layer
13. Research Layer
14. Projects Layer
15. Records Layer
16. Indexes and Dashboards Layer
17. Temporary Layers
18. Proposals Layer
19. Archive Layer
20. Knowledge Triage Rules
21. Knowledge Promotion Framework
22. Conflict Resolution Policy
23. Permission Model
24. Write Speed Policy
25. Memory Write Pipeline
26. Agent Write Rules
27. Retrieval Runtime Architecture
28. Retrieval Ranking and Scoring
29. Context Packing Policy
30. Retrieval Filter Presets
31. Knowledge Graph Metadata
32. Schema Validation Layer
33. Changelog Requirement
34. Naming Convention
35. File Lifecycle
36. Review and Audit
37. Knowledge Debt Dashboard
38. Memory Evaluation Metrics
39. Security, Privacy, and Retention Policy
40. Backup and Recovery Policy
41. Standard Templates
42. Claudian Skills and Workflows
43. Automation and Enforcement
44. Human Review UX
45. Failure Modes and Recovery
46. Operating Cadence
47. Migration Plan from V6 to V7
48. Success Criteria
49. Ultimate Principle

---

# 1. Vision

目标不是构建一个能记住所有内容的 AI。

目标是构建一个长期稳定、可治理、可扩展、可审计、可执行、可评估的 AI 工作系统。

系统必须保证：

- 永远知道事实在哪里
- 永远知道规则在哪里
- 永远知道经验在哪里
- 永远知道研究是否过期
- 永远知道原始证据在哪里
- 永远知道项目是否结束
- 永远知道谁可以修改什么
- 永远知道知识如何晋升
- 永远知道冲突如何解决
- 永远知道什么是唯一权威版本
- 永远知道 AI agent 通过什么 runtime 操作 Vault
- 永远知道哪些内容可以直接写，哪些内容只能提出修改建议
- 永远知道检索结果为什么被选中
- 永远知道回答用了哪些记忆
- 永远知道记忆系统是否正在变好或变坏

AI 可以无限生成。

知识库必须持续收敛。

V7 的核心目标是从知识治理升级为记忆运行系统：

```text
Governance Design
↓
Runtime Retrieval
↓
Context Packing
↓
Validation
↓
Evaluation
↓
Continuous Improvement
```

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
- Proposal
- Changelog
- Timeline
- Git history
- append-only source records
- superseded records

禁止：

- 内容复制
- 多版本事实
- 重复知识
- 平行真相
- 未声明来源的结论
- 已失效知识继续参与默认检索
- Agent 为了方便而新建重复权威文件
- 把 meeting note 当成 customer current state
- 把 research 当成 fact
- 把 case 当成 rule
- 把 archive 当成 current truth

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
- source records
- proposal records
- superseded records

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
- 文件生命周期管理
- 权威知识承载
- 原始证据承载
- 人类审核界面

原则：

Vault 是唯一长期记忆。

Obsidian 不只是笔记库。

Obsidian 是 AI workspace 的知识操作系统。

---

## 3.2 Claudian

角色：Obsidian Agent Runtime

Claudian 是运行在 Obsidian 内的 AI agent runtime / agent interface。

它让 AI coding agents 可以在 Vault 中工作。

Claudian 提供：

- chat sidebar
- inline edit
- slash commands
- skills
- `@mention` Vault files
- `@mention` subagents
- `@mention` MCP servers
- `@mention` external files
- plan mode
- instruction mode
- multi-tab conversations
- conversation history
- file read
- file write
- file edit
- file search
- bash
- multi-step workflows
- MCP access

原则：

Claudian 是 runtime。

Claudian 不是长期记忆。

Claudian 不是真相来源。

Claudian 不自动保证 SSOT。

Claudian 不自动替代审核。

Claudian 不自动成为 Knowledge Steward。

Claudian 让 agent 可以操作 Vault。

知识治理必须由以下机制共同实现：

- Hermes operating protocol
- Vault structure
- Source of Truth System
- Permission Model
- Retrieval Runtime
- Context Packing Policy
- Schema Validation
- templates
- review queues
- proposal workflow
- human approval
- optional scripts
- optional Claudian skills

---

## 3.3 Hermes

角色：Primary AI Workspace Agent / Operating Protocol

Hermes 是通过 Claudian 操作 Obsidian Vault 的主要 AI 工作协议。

Hermes 可以：

- 检索
- 分析
- 写作
- 自动化
- 项目执行
- 研究
- 草稿生成
- 初步分类建议
- 创建 proposal
- 更新低风险文件
- 生成 review queue 候选
- 协助项目 closeout
- 协助 schema 检查
- 协助检索来源说明
- 协助 memory evaluation

Hermes 必须：

- 尊重 SSOT
- 写入前判断知识类型
- 写入前检查 Source of Truth System
- 遵守 Permission Model
- 对 Class A 资产只生成 proposal
- 不把 Draft 当事实
- 不把 Research 当事实
- 不把 Case 当 Rule
- 不把 Meeting Note 当 Customer Current State
- 不默认检索 Archive / Logs / Drafts
- 给需要来源的内容添加 source
- 给需要复审的内容添加 review_date 或 expires_at
- 对高风险回答说明使用了哪些权威记忆
- 在不确定时降低 authority，而不是伪装成事实

原则：

Hermes 负责生产内容。

Hermes 可以提出知识更新。

Hermes 不单方面定义真相。

Hermes 不拥有长期记忆。

所有长期知识必须来自 Vault 检索、用户确认或明确来源。

---

## 3.4 Human Owner / Reviewer

角色：Final Authority

职责：

- 审核高风险修改
- 批准 Core / Facts / Rules / Source of Truth System 更新
- 确认业务事实
- 确认客户当前状态
- 确认产品事实
- 确认品牌事实
- 处理无法自动解决的冲突
- 接受或拒绝 Hermes proposal
- 定期审查 schema 失败项
- 定期审查 memory evaluation 指标

原则：

Human approval defines truth for high-risk knowledge.

Agent output is not truth until reviewed or explicitly confirmed.

---

## 3.5 Knowledge Steward

角色：Knowledge Operations Owner

Knowledge Steward 可以由 Human Owner 担任，也可以是指定运营角色。

职责：

- 维护 Source of Truth System
- 维护 Review Queues
- 处理 Knowledge Debt Dashboard
- 批量清理 Drafts / Inbox / Logs
- 检查 Archive 是否误参与默认检索
- 审查自动化脚本是否符合治理规则
- 推动项目 closeout
- 监督 V7 架构执行情况

原则：

Knowledge Steward 负责系统健康。

Human Reviewer 负责权威判断。

Hermes 负责执行辅助。

---

# 4. Claudian Runtime Model

Claudian 是 Obsidian 内的 agent runtime，而不是知识治理本体。

因此，本系统必须区分：

```text
Capability ≠ Permission
```

Claudian 可能允许 agent 读写文件、搜索、编辑、运行命令。

但 Hermes 是否可以执行某个动作，必须由本架构的 Permission Model 决定。

---

## 4.1 Runtime Capabilities

Claudian 提供以下能力：

```text
Read files
Write files
Edit files
Search files
Run bash
Use inline edit
Use chat sidebar
Use slash commands
Use skills
Use @mention context
Use plan mode
Use instruction mode
Use MCP servers
Perform multi-step workflows
```

这些能力只代表技术可行。

它们不代表治理许可。

---

## 4.2 Runtime Boundary

Claudian 不负责：

- 自动判断当前事实
- 自动维护唯一权威文件
- 自动决定知识晋升
- 自动解决业务冲突
- 自动批准规则修改
- 自动归档历史项目
- 自动替代人类审核
- 自动区分 raw record 和 current fact
- 自动判断 research 是否仍然有效

Claudian 可以承载这些 workflow。

但 workflow 的规则必须由 Hermes protocol 和 Vault governance 定义。

---

## 4.3 Plan Mode Policy

当任务涉及 Controlled Path 或 Class A 资产时，Hermes 必须使用 Plan Mode 或等效 proposal 流程。

适用范围：

- Core Memory
- Source of Truth System
- Permission Policy
- Retrieval Rules
- Context Packing Policy
- Brand Facts
- Product Facts
- Approved Rules
- Agent Behavior Rules
- Customer current profile
- Reviewed Research
- Learnings promotion
- Schema updates
- Security policy updates

流程：

```text
Explore
↓
Identify target files
↓
Check Source of Truth System
↓
Check Permission Class
↓
Generate plan
↓
Generate proposal
↓
Human approval
↓
Apply or reject
↓
Changelog
↓
Update indexes / dashboards
```

---

## 4.4 `@mention` Policy

涉及正式知识修改时，Hermes 应显式引用相关上下文。

Class A 修改必须引用：

```text
@Core-Memory.md
@Source-of-Truth-Map.md or registry entry
@Permission-Policy.md
@Relevant-SSOT-File.md
```

客户当前状态修改必须引用：

```text
@Customer/profile.md
@Relevant record
@Relevant timeline entry
@Proposal file
```

规则修改必须引用：

```text
@Relevant rule
@Related facts
@Related cases
@Related learnings
```

Research 晋升必须引用：

```text
@Raw research file
@Reviewed source summary
@Relevant Facts / Rules
@Proposal file
```

---

# 5. Hermes Operating Protocol

Hermes 是在 Claudian runtime 中执行任务的协议层。

Hermes 每次工作都必须遵守以下顺序。

---

## 5.1 Start of Task

任务开始时，Hermes 判断：

```text
Is this execution only?
Is this knowledge retrieval?
Is this knowledge creation?
Is this knowledge update?
Is this high-risk modification?
Is this research?
Is this project work?
Is this source record ingestion?
Is this audit / evaluation?
```

如果只是临时执行，不写长期知识。

如果涉及长期知识，进入 Memory Write Pipeline。

---

## 5.2 Before Retrieval

Hermes 必须判断需要哪些层：

```text
Core principles?
Facts?
Rules?
Learnings?
Reviewed Research?
Active Project?
Records / evidence?
Historical Archive?
Logs?
```

默认不得检索：

- Archive
- Logs
- Drafts
- Inbox
- Deprecated files
- Superseded files
- Raw Records unrelated to task

除非用户明确要求历史追溯、debug、草稿整理、证据核查或冲突处理。

---

## 5.3 Before Writing

Hermes 必须判断：

```text
What type of knowledge is this?
Where is the SSOT?
Is there an existing authority file?
Is this raw evidence or interpreted knowledge?
What is the permission class?
Does this need source?
Does this need review_date?
Does this need expires_at?
Does this need changelog?
Can Hermes write directly?
Should Hermes create a proposal?
```

---

## 5.4 After Writing

Hermes 必须：

- 添加 metadata
- 添加 source
- 添加 related links where useful
- 添加 changelog where required
- 标记 status
- 标记 authority
- 标记 write_policy
- 标记 review_date / expires_at where required
- 避免创建重复权威文件
- 将无法判断的内容放入 Inbox 或 Proposal
- 对高风险写入生成 review queue entry

---

## 5.5 Before Answering with Memory

当回答依赖长期记忆时，Hermes 必须判断：

```text
Did I use SSOT where available?
Did I avoid Draft / Archive / Raw Research as current truth?
Did I distinguish fact from research?
Did I distinguish meeting record from current profile?
Do I need to cite source files in the answer?
Is any retrieved memory stale or needs_review?
```

高风险回答应该说明：

- 使用了哪些权威文件
- 哪些信息是当前事实
- 哪些信息只是历史记录或研究
- 哪些信息需要人工确认

---

# 6. Memory Model

系统采用五层记忆模型。

---

## 6.1 Layer 1 — Working Memory

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

## 6.2 Layer 2A — Facts Memory

存放：

- 品牌事实
- 产品事实
- 客户当前事实
- 当前状态
- 已确认参数
- 已确认联系方式
- 已确认业务信息
- 已确认决策

特点：

- 唯一正确答案
- 有权威来源
- 可被审计
- 可被更新

Facts 分为两类。

### Current Facts

当前事实。

允许更新，但必须保留历史变化。

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
- 某次已确认决策
- 某个历史报价
- 某个项目阶段结果

原则：

当前状态可以覆盖。

历史事实只能追加、补充或标记纠正。

原始会议记录、邮件、转录和 feedback 不直接属于 Facts，它们属于 Records。

---

## 6.3 Layer 2B — Rules Memory

存放：

- SOP
- SEO 规则
- Social 规则
- Agent 规则
- 工作流
- 内容标准
- 审核标准
- 执行规范
- 自动化规范

特点：

- 描述应该如何做
- 具有复用价值
- 需要版本治理
- 修改必须审核

Rules 不是事实。

Rules 不是案例。

Rules 是未来执行的标准。

---

## 6.4 Layer 2C — Insights Memory

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
Postmortems = 对失败或重要事件的复盘
```

原则：

一次事件不是规则。

一次成功不是经验。

多次验证后才能成为 Learning。

稳定可复用后才能成为 Rule。

---

## 6.5 Layer 3 — Research Memory

存放：

- 市场研究
- 竞品研究
- 临时分析
- 外部资料
- 行业趋势
- SERP 分析
- 内容机会
- 技术调研
- 平台规则观察

特点：

- 未成为正式事实
- 可能过期
- 需要来源
- 需要 review_date 或 expires_at
- 默认低于 Facts 和 Rules 的权威等级

Research 可以支持判断。

Research 不直接定义真相。

---

## 6.6 Layer 4 — Records Memory

存放原始证据和事件记录。

包括：

- meeting notes
- call transcripts
- customer emails
- raw feedback
- imported documents
- source screenshots or attachments references
- signed approvals references
- raw interview notes
- unprocessed intake forms

特点：

- 记录发生过什么
- 可以支持 Facts / Cases / Decisions
- 默认不代表当前事实
- 默认不等于已确认结论
- 可以被引用为 source evidence
- 通常 append-only

Records 是证据。

Facts 是结论。

Insights 是解释。

Rules 是标准。

---

## 6.7 Layer 5 — Archive Memory

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
- 必须标记 archived、deprecated 或 superseded

Archive 是历史记录。

Archive 不是当前知识。

---

# 7. Vault Structure

V7 推荐结构：

```text
Vault/

00-Core/
01-Facts/
02-Rules/
03-Insights/
04-Research/
05-Projects/
06-Records/

70-Schemas/
80-Indexes/
81-Dashboards/

90-Drafts/
91-Inbox/
92-Logs/
93-Proposals/
94-Review-Queues/

99-Archive/
```

原则：

- 00 到 06 是正式工作、知识和证据层
- 70 是机器可执行 schema 层
- 80 到 81 是视图、索引和 dashboard 层
- 90 到 94 是临时、日志与审核流层
- 99 是历史层

V7 的关键变化：

```text
Meeting notes / raw feedback / emails / transcripts
不再放在 Facts 默认结构中。
它们进入 06-Records/。
```

原因：

```text
Records = 原始证据
Facts = 当前确认事实
```

---

# 8. Core Layer

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
- Source of Truth System
- Claudian Runtime Policy
- Hermes Operating Protocol
- Retrieval Runtime Policy
- Context Packing Policy
- Schema Validation Policy
- Security and Retention Policy

限制：

- Core-Memory.md 控制在 3000 字以内
- 只保留系统级原则
- 不保存具体品牌细节
- 不保存产品参数
- 不保存客户事实
- 不保存操作细节
- 不保存研究结论

Core Memory 是系统宪法。

不是百科全书。

---

## 8.1 Recommended Core Files

```text
00-Core/
  Core-Memory.md
  Source-of-Truth-Map.md
  Source-of-Truth-Registry.md
  Hermes-Operating-Protocol.md
  Claudian-Runtime-Policy.md
  Knowledge-Triage-Rules.md
  Conflict-Resolution-Policy.md
  Agent-Behavior-Rules.md
  Permission-Policy.md
  Retrieval-Rules.md
  Context-Packing-Policy.md
  Schema-Validation-Policy.md
  Security-and-Retention-Policy.md
  Backup-and-Recovery-Policy.md
```

---

# 9. Source of Truth System

V7 将 V6 的 Source of Truth Map 升级为 Source of Truth System。

Source of Truth System 包含：

```text
1. Human-readable Source-of-Truth-Map.md
2. Machine-readable Source-of-Truth-Registry.md or registry files
3. Index views generated from metadata
4. Duplicate and conflict detection queues
```

目标：

Map 是人类可读视图。

Registry 是可执行配置。

Dashboard 是运营界面。

---

## 9.1 Source of Truth Map

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
| Core principles | 00-Core/Core-Memory.md | Human approved via proposal | Yes |
| Claudian runtime policy | 00-Core/Claudian-Runtime-Policy.md | Human approved via proposal | Yes |
| Hermes behavior rules | 00-Core/Hermes-Operating-Protocol.md | Human approved via proposal | Yes |
| Retrieval policy | 00-Core/Retrieval-Rules.md | Human approved via proposal | Yes |
| Context packing policy | 00-Core/Context-Packing-Policy.md | Human approved via proposal | Yes |
| Brand positioning | 01-Facts/Brand/Positioning.md | Human approved via proposal | Yes |
| Brand voice | 01-Facts/Brand/Tone-of-Voice.md | Human approved via proposal | Yes |
| Product facts | 01-Facts/Products/ | Human approved via proposal | Yes |
| Customer current state | 01-Facts/Customers/{customer}/profile.md | Human approved via proposal | Yes |
| Customer historical timeline | 01-Facts/Customers/{customer}/timeline/ | Hermes append, review later | Monthly |
| Customer meeting records | 06-Records/Customers/{customer}/Meetings/ | Hermes append | Triage for promotion |
| Customer emails | 06-Records/Customers/{customer}/Emails/ | Hermes append | Triage for promotion |
| Customer raw feedback | 06-Records/Customers/{customer}/Feedback/ | Hermes append | Triage for promotion |
| Decisions | 01-Facts/Decisions/ | Hermes proposal or human confirmed | Yes |
| SEO rules | 02-Rules/SEO/ | Human approved via proposal | Yes |
| Social rules | 02-Rules/Social/ | Human approved via proposal | Yes |
| SOPs | 02-Rules/SOP/ | Human approved via proposal | Yes |
| Agent rules | 02-Rules/Agents/ | Human approved via proposal | Yes |
| Cases | 03-Insights/Cases/ | Hermes draft, review later | Yes |
| Learnings | 03-Insights/Learnings/ | Human approved via proposal | Yes |
| Research inbox | 04-Research/00-Inbox/ | Hermes allowed | Review required |
| Reviewed research | 04-Research/01-Reviewed/ | Human approved via proposal | Yes |
| Projects | 05-Projects/ | Hermes allowed | Closeout required |
| Schemas | 70-Schemas/ | Human approved via proposal | Yes |
| Indexes | 80-Indexes/ | Hermes allowed for generated views | No for view updates |
| Dashboards | 81-Dashboards/ | Hermes allowed for generated views | No for view updates |
| Drafts | 90-Drafts/ | Hermes allowed | No |
| Inbox | 91-Inbox/ | Hermes allowed | Triage required |
| Logs | 92-Logs/ | Hermes allowed | No |
| Proposals | 93-Proposals/ | Hermes allowed | Approval required |
| Review queues | 94-Review-Queues/ | Hermes allowed | Human review |
| Archive | 99-Archive/ | Human approved or archive workflow | No |
```

原则：

当不知道知识应该写在哪里时，先查 Source of Truth System。

如果 Map 和 Registry 冲突，创建 conflict proposal。

如果 Map 没有定义，写入 Inbox，等待 Triage。

---

## 9.2 Source of Truth Registry

位置：

```text
00-Core/Source-of-Truth-Registry.md
```

或：

```text
00-Core/Source-of-Truth-Registry/
  Brand.yml
  Products.yml
  Customers.yml
  Rules.yml
  Research.yml
  Records.yml
  Projects.yml
```

推荐 registry 结构：

```yaml
knowledge_domain: products
ssot_root: 01-Facts/Products/
file_pattern: "{Product-Name}.md"
permission_class: A
write_policy: proposal_only
required_schema: product.schema.yml
required_review: true
default_retrieval: true
archive_retrieval: false
```

原则：

Source of Truth Map 可以是人工维护。

Source of Truth Registry 应尽量机器可读。

Indexes 和 dashboards 应尽量从 registry 和 metadata 生成。

---

# 10. Facts Layer

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
  Decisions/
```

作用：

保存已确认事实。

Facts 是“是什么”。

不是“怎么做”。

不是“为什么”。

不是“原始记录”。

---

## 10.1 Brand

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

修改必须通过 proposal 和审核。

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

## 10.2 Products

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

产品修改必须通过 proposal。

---

## 10.3 Customers

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
    assets/
```

注意：

```text
meetings/
emails/
raw feedback/
transcripts/
```

不放在 Facts 默认结构中。

它们放入：

```text
06-Records/Customers/{customer}/
```

---

### profile.md

作用：

保存客户当前状态。

允许更新，但必须审核。

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

Meeting note 不能直接替代 profile。

Record 可以作为更新 profile 的 evidence。

---

### timeline/

作用：

保存客户历史变化。

规则：append-only。

按年度拆分。

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

## 10.4 Decisions

位置：

```text
01-Facts/Decisions/
```

作用：

保存已确认的重要决策。

Decision 与 record 不同。

Record 是原始记录。

Decision 是确认后的结论。

推荐结构：

```text
Decisions/
  2026-06-05-Decision-Name.md
```

必须包含：

- date
- context
- options considered
- decision
- decided by
- reason
- impacted files
- follow-up
- source

---

# 11. Rules Layer

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

## 11.1 Rule Requirements

每条 Rule 必须包含：

- 适用范围
- 输入条件
- 执行步骤
- 输出标准
- 判断标准
- 禁止事项
- 例外情况
- 相关事实
- 相关案例
- review_date
- owner
- changelog

Rule 修改必须通过 proposal 和审核。

过期 Rule 必须标记 deprecated、archived 或 superseded。

---

## 11.2 Rule Qualification Checklist

一条内容成为 Rule 前，必须满足：

```text
1. It is repeatable.
2. It has a clear trigger or input condition.
3. It has a clear output standard.
4. It has explicit exceptions.
5. It cites at least one source or decision.
6. It references at least one supporting case, learning, or domain fact.
7. It has an owner.
8. It has a review_date.
9. It has a changelog.
10. It is approved.
```

不满足以上条件的内容，只能是 Draft、Learning、Case 或 Proposal。

---

# 12. Insights Layer

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

## 12.1 Cases

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

## 12.2 Learnings

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

---

## 12.3 Pattern Qualification

一个观察晋升为 Learning 前，至少满足以下条件之一：

- 多个项目重复出现
- 多个客户重复出现
- 有明确数据支持
- 有人工确认
- 有失败案例对照
- 被 Rule 使用过并证明有效

---

# 13. Research Layer

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

## 13.1 Research Inbox

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

## 13.2 Reviewed Research

位置：

```text
04-Research/01-Reviewed/
```

特点：

- 已审核
- 允许谨慎检索
- 仍不等于事实
- 必须有 review_date
- 必须有 expires_at 或 next_review

---

## 13.3 Reference

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

## 13.4 Research Review Queue

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

## 13.5 Research Archive

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

## 13.6 Expiration Rule

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

# 14. Projects Layer

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

## 14.1 Project Structure

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

## 14.2 Project Closeout

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
- 客户变化 → Customer profile proposal / timeline
- 原始记录 → Records
- 事件记录 → Cases
- 可复用经验 → Learnings
- 可复用流程 → Rules proposal
- 原始项目材料 → Archive

禁止项目结束后继续作为默认检索来源。

---

# 15. Records Layer

位置：

```text
06-Records/
```

作用：

保存原始证据、原始事件记录、导入材料和可追溯 source。

Records 是 V7 的新增正式层。

它解决 V6 中 meeting notes 放在 Facts 下可能导致语义混乱的问题。

---

## 15.1 Records Structure

推荐结构：

```text
06-Records/
  Customers/
    Acme/
      Meetings/
      Emails/
      Calls/
      Feedback/
      Attachments/
  Internal/
    Meetings/
    Decisions-Raw/
    Strategy-Notes/
  Sources/
    Web/
    PDFs/
    Screenshots/
    Imports/
```

---

## 15.2 Records Principles

Records 必须遵守：

- append-only by default
- source required when applicable
- not current truth by default
- not approved conclusion by default
- can be evidence for Facts / Decisions / Cases / Learnings
- can trigger proposal
- can be referenced in changelog

禁止：

- 把 Record 直接当 Fact
- 把单个 customer quote 直接当 Customer profile
- 把会议中提到的想法直接当 Decision
- 把邮件中的临时说法直接当 Product fact

---

## 15.3 Record Promotion

Record 可以触发以下晋升：

```text
Meeting note → Decision proposal
Meeting note → Customer profile proposal
Email → Timeline append
Feedback → Case
Repeated feedback → Learning
Transcript → Project note
Raw source → Research
```

晋升必须通过 Triage。

---

# 16. Indexes and Dashboards Layer

## 16.1 Indexes

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
  Records.md
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

## 16.2 Dashboards

位置：

```text
81-Dashboards/
```

推荐文件：

```text
81-Dashboards/
  Knowledge-Debt-Dashboard.md
  Memory-Evaluation-Dashboard.md
  Proposal-Dashboard.md
  Research-Freshness-Dashboard.md
  Project-Closeout-Dashboard.md
  Security-Retention-Dashboard.md
```

Dashboards 用于运营。

Dashboards 不保存权威事实。

---

# 17. Temporary Layers

## 17.1 Drafts

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

## 17.2 Inbox

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
- 转成 Record
- 转成 Project
- 晋升到正式知识层
- 转成 Proposal

---

## 17.3 Logs

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

但 Hermes 可从 Logs 中提取 recurring failure pattern，整理为：

- Automation Learning proposal
- SOP update proposal
- Agent Rule update proposal

禁止直接把原始 Logs 作为正式知识。

---

# 18. Proposals Layer

位置：

```text
93-Proposals/
```

作用：保存 Hermes 对高风险知识的修改建议。

结构：

```text
93-Proposals/
  Core/
  Facts/
  Rules/
  Customers/
  Research/
  Records/
  Conflicts/
  Promotions/
  Archive/
  Schemas/
  Security/
```

Proposals 是审核队列。

Proposals 不是正式知识。

---

## 18.1 When to Create Proposal

以下情况必须创建 proposal：

- 修改 Core Memory
- 修改 Source of Truth System
- 修改 Permission Policy
- 修改 Retrieval Rules
- 修改 Context Packing Policy
- 修改 Schema
- 修改 Security Policy
- 修改 Brand Facts
- 修改 Product Facts
- 修改 Customer profile 当前状态
- 修改 Approved Rules
- 晋升 Learning 为 Rule
- 晋升 Research 为 Reviewed Research
- 标记正式知识为 deprecated
- 标记正式知识为 superseded
- 解决冲突
- 合并重复权威文件
- 恢复 Archive 内容为 active

---

## 18.2 Proposal Lifecycle

```text
Drafted
↓
Pending Review
↓
Approved / Rejected / Needs Revision
↓
Applied
↓
Changelog updated
↓
Indexes updated
↓
Proposal archived
```

---

## 18.3 Proposal Rules

Proposal 必须包含：

- target_file
- proposal_type
- proposed change
- reason
- source evidence
- risk
- affected files
- suggested changelog entry
- reviewer
- decision
- rollback plan for high-risk updates

---

# 19. Archive Layer

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
- 已应用 proposal

原则：

Archive 默认不参与检索。

Archive 只用于历史追溯。

Archive 中的内容不能作为当前事实。

如果 Archive 中的信息重新变得有用，必须重新 Review 后再恢复。

---

# 20. Knowledge Triage Rules

位置：

```text
00-Core/Knowledge-Triage-Rules.md
```

所有写入前必须先判断知识类型。

---

## 20.1 Step 1 — Classify

判断内容属于哪一类：

```text
Current truth → Facts
Historical confirmed event → Timeline
Raw evidence → Records
Confirmed decision → Decisions
How-to instruction → Rules
Repeated verified pattern → Learnings
One-off event with result → Cases
External uncertain info → Research
Work-in-progress → Projects / Drafts
System principle → Core
High-risk update → Proposal
Unclear content → Inbox
```

---

## 20.2 Step 2 — Check SSOT

写入前必须判断：

是否已有权威版本？

如果有：

- 不创建平行版本
- 创建 proposal 或更新原文件
- 添加 changelog
- 关联来源

如果没有：

- 根据 Source of Truth System 创建新文件
- 添加完整 metadata
- 设置 owner 和 review_date

---

## 20.3 Step 3 — Check Permission

判断目标位置属于哪一类权限：

- Class A：只读，必须审核
- Class B：可新增，需规范
- Class C：完全开放
- Class R：Records，append-only evidence

如果是 Class A：

Hermes 只能生成 proposal。

不能直接覆盖。

---

## 20.4 Step 4 — Write or Propose

根据权限执行：

```text
Fast-write area → 直接写入
Records area → append with metadata
Review-required area → 生成 proposal
Unknown area → 写入 Inbox
```

---

# 21. Knowledge Promotion Framework

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
Draft / Inbox / Project / Record
↓
Triage
↓
Facts / Rules / Cases / Research / Records / Projects / Proposal
↓
Validated Learning
↓
Reusable Rule
↓
Core Memory, only if system-level and stable
```

---

## 21.1 Draft → Facts

适用于：

- 已确认产品信息
- 已确认品牌信息
- 已确认客户当前状态
- 已确认决策

要求：

- 有来源
- 有 owner
- 有 review
- 确认无现有 SSOT 冲突
- Class A 必须通过 proposal

---

## 21.2 Record → Facts

适用于：

- 会议中确认了客户当前状态
- 邮件中确认了新联系人
- 签署材料确认了价格或范围
- 录音转录确认了决策

要求：

- Record 本身保持 append-only
- Facts 更新通过 proposal
- profile / product / brand 更新后添加 changelog
- timeline 记录历史变化
- source 指向 Record

---

## 21.3 Draft → Research

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

## 21.4 Project → Case

适用于：

- 完成项目
- 明确行动和结果
- 有可追溯证据

---

## 21.5 Case → Learning

适用于：

- 多个案例支持
- 有明确复用价值
- 有边界条件
- 有人工确认

---

## 21.6 Learning → Rule

适用于：

- 可稳定复用
- 可指导未来执行
- 有清晰步骤
- 有适用范围
- 有例外情况

必须通过 proposal。

---

## 21.7 Rule → Core Memory

适用于：

- 系统级原则
- 长期稳定
- 跨项目适用
- 跨 agent 适用
- 高度抽象
- 不依赖具体业务细节

Core Memory 只能收录原则。

不能收录细节。

必须通过 proposal。

---

# 22. Conflict Resolution Policy

位置：

```text
00-Core/Conflict-Resolution-Policy.md
```

SSOT 的难点不是只有一个文件。

SSOT 的难点是冲突时如何判断。

---

## 22.1 Authority Priority

当两个来源冲突时，按以下优先级判断：

```text
1. Core Memory, only for system principles
2. Approved Rules, only for execution standards
3. Domain Facts SSOT
   - Brand Facts
   - Product Facts
   - Customer profile current state
   - Decisions
4. Historical confirmed facts
   - Timeline
   - Confirmed decision notes
5. Source Records
   - Meeting notes
   - Emails
   - Feedback
   - Transcripts
6. Approved Learnings
7. Reviewed Research
8. Active project notes
9. Raw Research
10. Proposals
11. Drafts / Inbox
12. Logs
13. Archive, only for historical tracing
```

说明：

Core Memory 只对系统原则有最高权威。

Core Memory 不覆盖具体品牌、产品、客户事实。

具体事实仍以对应 Facts SSOT 为准。

Record 比 Draft 权威高，但低于已确认 Facts。

---

## 22.2 Conflict Handling

如果发现冲突：

1. 不直接删除任何原始记录
2. 找到对应 SSOT 文件
3. 判断冲突来源
4. 创建 conflict proposal
5. 更新当前结论或等待审核
6. 添加 source
7. 添加 changelog
8. 必要时创建 conflict note
9. 标记低权威内容为 outdated 或 superseded

---

## 22.3 Conflict Note

位置：

```text
93-Proposals/Conflicts/
```

或：

```text
94-Review-Queues/Conflict-Queue.md
```

格式见 Standard Templates。

---

# 23. Permission Model

系统采用四类权限。

---

## 23.1 Class A — Core Assets

包含：

- Core Memory
- Source of Truth System
- Brand
- Products
- Rules
- Agent behavior rules
- Permission policy
- Retrieval rules
- Context packing policy
- Schema validation policy
- Security policy
- Claudian runtime policy
- Hermes operating protocol

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
Use Plan Mode where possible.
```

---

## 23.2 Class B — Knowledge Assets

包含：

- Customers
- Cases
- Learnings
- Research
- Projects
- Reviewed notes
- Decisions

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
Need proposal for current-state changes.
```

---

## 23.3 Class C — Temporary Assets

包含：

- Drafts
- Inbox
- Logs
- Project working drafts
- Research inbox
- Proposals
- Review queues

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

## 23.4 Class R — Records Assets

包含：

- Meetings
- Emails
- Calls
- Raw feedback
- Transcripts
- Imports
- Source materials

权限：

- Hermes 可 append
- 默认不可覆盖
- 修正必须追加 correction
- 不作为当前事实
- 可作为 evidence
- 敏感内容需遵守 Security Policy

Hermes 行为：

```text
Append records.
Do not rewrite records silently.
Create proposal when record implies current fact update.
```

---

## 23.5 Emergency Override

适用：

- 时间敏感的当前事实
- 客户联系方式临时更正
- 项目状态紧急更新
- 交付风险紧急记录

规则：

- 只能用于 Class B 当前工作流
- 不适用于 Core、Brand、Product、Approved Rules、Security Policy
- 必须标记 status: needs_review
- 必须记录 source
- 必须创建 changelog 或 timeline entry
- 必须在 7 天内审核

---

# 24. Write Speed Policy

为了避免治理过重，系统区分 Fast Path、Records Path 和 Controlled Path。

---

## 24.1 Fast Path

允许快速写入：

- Drafts
- Inbox
- Logs
- Project working notes
- Research inbox
- Proposals

特点：

- 写入快
- 权威低
- 后续需要 Triage
- 不自动成为正式知识

---

## 24.2 Records Path

允许快速追加：

- Meeting notes
- Emails
- Calls
- Transcripts
- Raw feedback
- Imported source documents

特点：

- append-only
- evidence role
- 不自动成为当前事实
- 可触发 proposal
- 必须有 source metadata where applicable

---

## 24.3 Controlled Path

必须审核：

- Core Memory
- Brand
- Products
- Rules
- Customer profile
- Learnings
- Reviewed Research
- Source of Truth System
- Permission Policy
- Claudian Runtime Policy
- Hermes Operating Protocol
- Retrieval Policy
- Context Packing Policy
- Schema Policy
- Security Policy

特点：

- 写入慢
- 权威高
- 必须有来源
- 必须有 changelog
- 必须有 owner
- 必须通过 proposal

---

# 25. Memory Write Pipeline

禁止直接写入核心知识。

统一流程：

```text
Hermes through Claudian runtime
↓
Draft / Inbox / Project / Research Inbox / Record / Proposal
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
↓
Update indexes / dashboards
```

---

## 25.1 Stage 1 — Create

Hermes 输出内容。

可进入：

- Drafts
- Inbox
- Projects
- Research Inbox
- Records
- Logs
- Proposals

---

## 25.2 Stage 2 — Triage

判断：

- 这是事实？
- 这是规则？
- 这是经验？
- 这是案例？
- 这是研究？
- 这是原始证据？
- 这是项目材料？
- 是否已有 SSOT？
- 是否重复？
- 是否过期？
- 是否需要审核？

---

## 25.3 Stage 3 — Review

审核：

- 是否准确
- 是否重复
- 是否已有权威版本
- 是否有来源
- 是否有 owner
- 是否需要过期时间
- 是否违反 SSOT
- 是否应该归档
- 是否含敏感信息
- 是否可参与默认检索

---

## 25.4 Stage 4 — Promote

符合条件后晋升到：

- Facts
- Rules
- Insights
- Research Reviewed
- Records
- Indexes
- Archive

---

## 25.5 Stage 5 — Merge

如果目标是已有 SSOT：

- 更新原文件
- 不创建新版本
- 添加 changelog
- 添加 related
- 添加 source
- 更新 updated
- 更新 review_date
- 归档 proposal

---

# 26. Agent Write Rules

Hermes 写入前必须执行以下判断。

---

## 26.1 Step 1 — What is this?

```text
Fact?
Rule?
Learning?
Case?
Research?
Record?
Project material?
Draft?
Log?
Proposal?
```

---

## 26.2 Step 2 — Is there an existing SSOT?

如果有：

- 不创建新权威文件
- 对 Class A 生成 proposal
- 对 Class B 按权限 append 或 proposal
- 对 Class R append evidence 或创建 promotion proposal
- 引用原文件

如果没有：

- 根据 Source of Truth System 创建
- 添加 metadata
- 标记 status

---

## 26.3 Step 3 — Is it a Core Asset?

如果是：

- 不自动覆盖
- 只生成 proposal
- 标明 changed sections
- 标明 reason
- 标明 source

---

## 26.4 Step 4 — Does it need expiration?

以下内容必须有 expires_at 或 review_date：

- Research
- SEO 资料
- 竞品资料
- 市场趋势
- 技术工具信息
- 平台规则
- 价格信息
- 外部资料
- Reviewed Research
- Rules
- Product facts with volatile details

---

## 26.5 Step 5 — Does it need source?

以下内容必须有 source：

- Facts
- Rules
- Research
- Records
- Learnings
- Customer profile changes
- Product changes
- Brand changes
- Decisions
- Proposals

没有 source 的内容只能进入 Draft 或 Inbox。

---

## 26.6 Step 6 — Does it contain sensitive data?

如果内容包含：

- credentials
- API keys
- passwords
- private customer data
- personal identifiers
- financial information
- legal information
- private business strategy

必须遵守 Security and Retention Policy。

默认不得写入普通知识层。

---

# 27. Retrieval Runtime Architecture

V7 新增运行时检索架构。

目标：

不仅规定“应该检索什么”，还规定 Hermes 实际如何检索、排序、打包和说明来源。

---

## 27.1 Retrieval Modes

系统支持以下检索模式：

```yaml
retrieval_modes:
  - exact_ssot_lookup
  - source_of_truth_registry_lookup
  - metadata_filter_search
  - semantic_search
  - backlink_expansion
  - recency_boosted_search
  - authority_boosted_search
  - project_context_search
  - historical_trace_search
  - evidence_trace_search
  - conflict_search
  - debug_log_search
```

---

## 27.2 Default Retrieval Flow

普通任务默认流程：

```text
1. Identify task type
2. Select retrieval preset
3. Check Source of Truth System
4. Exact lookup for known SSOT
5. Metadata-filtered search
6. Semantic search only within allowed layers
7. Apply ranking and exclusion rules
8. Pack context according to Context Packing Policy
9. Answer or act
10. Optionally report memory sources used
```

---

## 27.3 Writing Retrieval Flow

写入正式知识前：

```text
1. Load Core-Memory.md
2. Load Source of Truth System
3. Load Permission Policy
4. Load relevant schema
5. Load target SSOT file
6. Load active proposal if exists
7. Load evidence records only as needed
8. Create proposal or write according to permission
```

---

## 27.4 Evidence Retrieval Flow

当需要确认事实来源时：

```text
1. Load current SSOT
2. Load changelog entry
3. Follow source links
4. Load relevant Records
5. Check timestamps
6. Check whether newer conflicting evidence exists
7. Return current fact with evidence trail
```

---

## 27.5 Historical Retrieval Flow

历史追溯时：

```text
1. Load timeline
2. Load records
3. Load archive if requested
4. Load superseded files if relevant
5. Mark all outputs as historical
6. Do not update current truth unless proposal is created
```

---

# 28. Retrieval Ranking and Scoring

检索结果必须排序。

不要只依赖语义相似度。

---

## 28.1 Ranking Formula

推荐逻辑：

```text
final_score =
  semantic_relevance
+ authority_weight
+ ssot_weight
+ task_match_weight
+ source_quality_weight
+ freshness_weight
+ project_relevance_weight
+ backlink_weight
- stale_penalty
- draft_penalty
- archive_penalty
- deprecated_penalty
- conflict_penalty
- security_penalty
```

---

## 28.2 Authority Weights

```yaml
authority_weight:
  ssot: 100
  approved: 80
  reference: 50
  provisional: 25
  raw: 15
  none: 0
```

---

## 28.3 Layer Weights

默认执行任务：

```yaml
layer_weight:
  core: 100
  facts: 95
  rules: 90
  insights: 65
  research_reviewed: 50
  projects_active: 45
  records: 35
  research_raw: 20
  proposals: 10
  drafts: -50
  logs: -70
  archive: -80
```

历史任务和 debug 任务可以使用不同权重。

---

## 28.4 Freshness Rules

以下内容 freshness 权重较高：

- customer current profile
- active project notes
- current product facts
- platform rules
- market research
- pricing
- competitor information

以下内容 freshness 权重较低：

- core principles
- historical decisions
- long-term SOPs
- stable brand principles

---

## 28.5 Exclusion Rules

默认强制排除：

```text
status: archived
status: deprecated
status: superseded
status: rejected
memory_layer: draft
memory_layer: logs
memory_layer: inbox
```

除非 retrieval preset 明确允许。

---

# 29. Context Packing Policy

V7 新增 Context Packing Policy。

目标：

在有限上下文中优先放入最权威、最相关、最少污染的记忆。

---

## 29.1 Context Tiers

```text
Tier 0: Task instruction and user request
Tier 1: Exact SSOT files
Tier 2: Relevant approved rules
Tier 3: Relevant current facts
Tier 4: Active project context
Tier 5: Relevant approved learnings
Tier 6: Reviewed research summaries
Tier 7: Source records / evidence excerpts
Tier 8: Raw research / drafts / archive only when explicitly needed
```

---

## 29.2 Packing Rules

Hermes 不应加载整个 Vault。

默认应加载：

```text
1. Minimal Core principles
2. Exact relevant SSOT
3. Relevant rules snippets
4. Active project context if applicable
5. Supporting evidence only when needed
```

---

## 29.3 Summarize vs Load

以下内容优先加载全文：

- target SSOT file
- relevant short rule
- active proposal
- current customer profile
- current project brief

以下内容优先加载摘要：

- long research notes
- long meeting transcripts
- large project histories
- archived materials
- logs

以下内容只加载指针：

- unrelated indexes
- old drafts
- superseded files
- low-quality raw research

---

## 29.4 Context Budget Allocation

推荐比例：

```yaml
context_budget:
  task_instruction: 10%
  exact_ssot: 30%
  rules: 20%
  project_context: 15%
  evidence: 15%
  research_or_insights: 10%
```

高风险写入任务可提高 exact_ssot 和 evidence 比例。

研究任务可提高 research 比例，但仍不得把 research 当 fact。

---

## 29.5 Memory Source Reporting

高风险任务回答时，Hermes 应报告：

```text
Memory used:
- SSOT files
- Rules
- Records / evidence
- Research
- Uncertain or stale items
```

普通低风险任务可以不报告，避免噪音。

---

# 30. Retrieval Filter Presets

为了让检索规则可执行，系统定义以下检索预设。

---

## 30.1 Default Execution Retrieval

用于普通执行任务。

Include：

```yaml
memory_layer:
  - core
  - facts
  - rules
  - insights
  - research
  - projects
status:
  - active
authority:
  - ssot
  - approved
  - reference
```

Exclude：

```yaml
memory_layer:
  - draft
  - inbox
  - logs
  - archive
status:
  - draft
  - archived
  - deprecated
  - superseded
  - needs_review
```

---

## 30.2 Writing Retrieval

用于准备写入正式知识。

Must include：

```text
Core-Memory.md
Source-of-Truth-System
Permission-Policy.md
Relevant schema
Relevant SSOT file
Relevant proposal if exists
```

Optional include：

```text
Relevant Records
Relevant timeline
Relevant changelog
```

Exclude by default：

```text
Archive
Logs
Drafts unrelated to current task
```

---

## 30.3 Research Retrieval

用于研究任务。

Priority：

```text
Reviewed Research
Reference
Current Facts
Approved Rules
Raw Research
External sources
```

Raw Research 必须标记为未审核。

---

## 30.4 Evidence Retrieval

用于事实核查。

Include：

```text
Facts SSOT
Changelog
Decisions
Records
Timeline
Approved source references
```

Requirement：

输出必须区分：

```text
Current fact
Supporting evidence
Historical note
Unresolved conflict
```

---

## 30.5 Historical Retrieval

用于历史追溯。

Include：

```text
Archive
Timeline
Records
Old projects
Superseded files
```

Requirement：

所有输出必须明确标记为 historical，不得作为 current truth。

---

## 30.6 Debug Retrieval

用于 agent/debug/automation failure。

Include：

```text
Logs
Automation notes
Error reports
Related SOPs
```

Requirement：

Logs 只能用于诊断，不能直接成为正式知识。

---

# 31. Knowledge Graph Metadata

所有正式知识统一 Frontmatter。

---

## 31.1 Required Metadata

所有正式文件必须包含：

```yaml
type:
memory_layer:
status:
authority:
owner:
created:
updated:
source:
write_policy:
```

---

## 31.2 Conditional Required Metadata

以下字段按条件必填：

```yaml
review_date: required for rules, research, customer_profile, product, brand, learning
expires_at: required for research, market data, platform rules, pricing, competitor info
confidence: required for research, insights, provisional knowledge, records
changelog: required for Class A and recommended for Class B
superseded_by: required when status is superseded
approved_by: required when authority is approved or ssot after proposal
retention_until: required for sensitive records and logs
sensitivity: required for records, customer files, private documents
schema: recommended for all formal files
```

---

## 31.3 Recommended Metadata

推荐但不强制：

```yaml
related:
tags:
source_quality:
reviewer:
last_verified:
retrieval_scope:
canonical_id:
```

---

## 31.4 Field Definitions

### type

文档类型。

```yaml
type: product
type: customer_profile
type: decision
type: rule
type: case
type: learning
type: research
type: project
type: record
type: proposal
type: index
type: dashboard
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
memory_layer: records
memory_layer: draft
memory_layer: inbox
memory_layer: logs
memory_layer: proposal
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
status: pending
status: approved
status: rejected
status: applied
```

### authority

权威等级。

```yaml
authority: ssot
authority: approved
authority: reference
authority: provisional
authority: raw
authority: none
```

### source_quality

来源质量。

```yaml
source_quality: user_confirmed
source_quality: primary_source
source_quality: internal_record
source_quality: external_official
source_quality: external_secondary
source_quality: ai_generated
source_quality: unknown
```

### write_policy

写入权限。

```yaml
write_policy: review_required
write_policy: append_only
write_policy: open
write_policy: read_only
write_policy: proposal_only
```

### sensitivity

敏感度。

```yaml
sensitivity: public
sensitivity: internal
sensitivity: confidential
sensitivity: restricted
sensitivity: secret
```

### retrieval_scope

默认检索范围。

```yaml
retrieval_scope: default
retrieval_scope: evidence_only
retrieval_scope: historical_only
retrieval_scope: debug_only
retrieval_scope: excluded
```

---

## 31.5 Example Metadata

```yaml
---
type: product
memory_layer: facts
status: active
authority: ssot
owner: human
created: 2026-01-01
updated: 2026-06-05
review_date: 2026-12-01
expires_at:
source:
  - founder-confirmed
source_quality: user_confirmed
confidence: high
write_policy: review_required
approved_by: human
sensitivity: internal
retrieval_scope: default
schema: product.schema.yml
related:
  - rule/seo-content
  - customer/acme
tags:
  - seo
  - product
---
```

---

# 32. Schema Validation Layer

V7 新增 Schema Validation Layer。

位置：

```text
70-Schemas/
```

作用：

把治理规则变成可检查规则。

---

## 32.1 Recommended Schemas

```text
70-Schemas/
  product.schema.yml
  customer_profile.schema.yml
  rule.schema.yml
  learning.schema.yml
  research.schema.yml
  record.schema.yml
  decision.schema.yml
  proposal.schema.yml
  project_closeout.schema.yml
```

---

## 32.2 Validation Checks

自动检查：

```text
Missing required metadata
Missing source
Missing owner
Missing review_date
Invalid authority
Invalid memory_layer
Class A file without changelog
Research without expires_at
Rule without exceptions
Learning without evidence
Record without sensitivity
Superseded file without superseded_by
Archived file included in default retrieval
Customer profile modified without proposal
Product file modified without proposal
```

---

## 32.3 Schema Failure Handling

Schema 失败不一定阻止写入。

处理方式：

```text
Class A schema failure → block direct write, create proposal
Class B schema failure → allow draft or needs_review
Class C schema failure → allow write, add to cleanup queue
Class R schema failure → allow append if urgent, mark needs_metadata
```

---

## 32.4 Example Product Schema

```yaml
schema: product
required:
  - type
  - memory_layer
  - status
  - authority
  - owner
  - created
  - updated
  - source
  - source_quality
  - write_policy
  - review_date
  - approved_by
rules:
  type: product
  memory_layer: facts
  authority: ssot
  write_policy: review_required
  changelog_required: true
```

---

# 33. Changelog Requirement

所有 Class A 文件必须有 Changelog。

推荐格式：

```markdown
## Changelog

| Date | Change | Source | Proposal | Approved By |
|---|---|---|---|---|
| 2026-06-05 | Updated product positioning | Founder note | 93-Proposals/Facts/... | Human |
```

Class B 文件建议有 Changelog。

Class R 文件默认 append-only，可以使用 Correction Log。

Class C 文件不要求。

---

# 34. Naming Convention

统一命名减少重复和检索混乱。

---

## 34.1 General Rules

- 使用清晰英文或固定项目语言
- 避免 `final`、`new`、`v2`、`copy`
- 日期使用 `YYYY-MM-DD`
- 一个权威实体一个文件
- 历史变化写入 changelog 或 timeline
- 原始记录使用日期和来源命名

---

## 34.2 Naming Patterns

```text
Products: Product-Name.md
Brand: Positioning.md / Tone-of-Voice.md
Customer profile: profile.md
Timeline: YYYY.md
Meeting records: YYYY-MM-DD-Customer-Topic.md
Email records: YYYY-MM-DD-From-To-Topic.md
Call records: YYYY-MM-DD-Customer-Topic.md
Decisions: YYYY-MM-DD-Decision-Name.md
Rules: Domain-Rule-Name.md
Research: YYYY-MM-DD-Topic.md
Cases: YYYY-MM-DD-Case-Name.md
Learnings: Domain-Learnings.md
Projects: YYYY-Client-Project-Name
Proposals: YYYY-MM-DD-Target-Change.md
Logs: YYYY-MM-DD-Agent-Task.md
```

---

# 35. File Lifecycle

所有正式知识都必须有生命周期状态。

---

## 35.1 draft

草稿。

不参与正式检索。

---

## 35.2 active

当前有效。

可参与检索。

---

## 35.3 needs_review

需要审核。

可以谨慎检索，但不能作为最终权威。

---

## 35.4 deprecated

已废弃。

默认不参与检索。

可以用于历史解释。

---

## 35.5 archived

已归档。

默认不参与检索。

---

## 35.6 superseded

已被替代。

必须指向替代文件。

示例：

```yaml
status: superseded
superseded_by: 01-Facts/Products/Armor-SEO.md
superseded_reason: merged into product SSOT
superseded_date: 2026-06-05
```

---

# 36. Review and Audit

## 36.1 Knowledge Review

每月执行 Knowledge Review。

检查：

- 重复文件
- 孤立文档
- 未分类内容
- 失效研究
- needs_review 文件
- Inbox 堆积
- Drafts 堆积
- Proposal 堆积
- Records 未分类证据
- 缺少 metadata 的正式文件
- 过期 review_date
- 失效 source
- schema validation failures

输出：

```text
94-Review-Queues/Monthly-Review-Queue.md
```

---

## 36.2 Knowledge Audit

每季度执行 Knowledge Audit。

检查：

- SSOT 完整性
- Core Memory 体积
- Rule 有效性
- Learning 时效性
- Metadata 完整性
- Graph 连接质量
- Research 过期情况
- Records 是否误作为 Facts
- Archive 是否误参与检索
- Projects 是否完成 closeout
- Source of Truth System 是否完整
- Schema 是否仍符合实际运行
- Claudian skills 是否仍符合 governance policy
- Hermes behavior 是否符合 write rules

输出：

```text
81-Dashboards/Quarterly-Audit.md
```

---

## 36.3 Review Queues

推荐维护以下队列：

```text
94-Review-Queues/Review-Queue.md
94-Review-Queues/Expiring-Research.md
94-Review-Queues/Needs-Source.md
94-Review-Queues/Needs-Owner.md
94-Review-Queues/Duplicate-Candidates.md
94-Review-Queues/Orphan-Notes.md
94-Review-Queues/Conflict-Queue.md
94-Review-Queues/Deprecated-Knowledge.md
94-Review-Queues/Proposal-Queue.md
94-Review-Queues/Project-Closeout-Queue.md
94-Review-Queues/Schema-Failures.md
94-Review-Queues/Security-Review.md
94-Review-Queues/Records-Triage.md
```

---

# 37. Knowledge Debt Dashboard

位置：

```text
81-Dashboards/Knowledge-Debt-Dashboard.md
```

作用：

量化知识治理债务。

必须追踪：

```text
Inbox items count
Drafts older than 30 days
Research past review_date
Files missing owner
Files missing source
Files missing required metadata
Schema failures
Open conflicts
Pending proposals
Rejected proposals not archived
Projects without closeout
Records waiting for triage
Superseded files missing superseded_by
Archive files accidentally indexed
Logs older than retention policy
Sensitive records without retention_until
```

原则：

知识债务必须可见。

不可见的债务最终会污染默认检索。

---

# 38. Memory Evaluation Metrics

V7 新增 Memory Evaluation。

目标：

判断记忆系统是否变好。

---

## 38.1 Core Metrics

必须追踪：

```text
Memory Precision
Memory Recall
Stale Knowledge Rate
Duplicate Knowledge Rate
Proposal Aging
Review Debt
Retrieval Contamination Rate
Answer Attribution Rate
SSOT Lookup Success Rate
Schema Pass Rate
Records Promotion Rate
Archive Leakage Rate
```

---

## 38.2 Metric Definitions

### Memory Precision

检索到的内容中，真正相关且可用的比例。

### Memory Recall

任务需要的关键记忆中，被成功检索到的比例。

### Stale Knowledge Rate

回答或执行中使用了过期知识的比例。

### Duplicate Knowledge Rate

同一知识出现多个候选权威文件的比例。

### Proposal Aging

Proposal 从创建到处理的平均时间。

### Review Debt

过期 review_date、needs_review、schema failure 的总量。

### Retrieval Contamination Rate

回答中错误使用 Draft / Raw Research / Archive / Logs / Records 作为当前事实的比例。

### Answer Attribution Rate

高风险回答中明确说明来源的比例。

### SSOT Lookup Success Rate

需要权威事实时，能否在 SSOT 中找到答案的比例。

### Schema Pass Rate

正式文件通过 schema 检查的比例。

### Records Promotion Rate

有效 Records 被正确转为 Facts / Decisions / Cases / Learnings / Proposals 的比例。

### Archive Leakage Rate

Archive 内容误参与默认检索的比例。

---

## 38.3 Evaluation Dashboard

位置：

```text
81-Dashboards/Memory-Evaluation-Dashboard.md
```

推荐字段：

```text
Metric
Current Value
Target
Trend
Owner
Action Needed
```

---

# 39. Security, Privacy, and Retention Policy

V7 新增安全、隐私和保留策略。

位置：

```text
00-Core/Security-and-Retention-Policy.md
```

---

## 39.1 Sensitive Data Policy

以下内容不得写入普通知识层：

- passwords
- API keys
- access tokens
- private keys
- recovery codes
- unredacted financial records
- unnecessary personal identifiers
- highly sensitive customer private data

如果确实需要记录，只能写入受限位置，并标记：

```yaml
sensitivity: restricted
retrieval_scope: excluded
retention_until:
```

---

## 39.2 Customer Data Policy

客户资料必须区分：

```text
Public business facts
Internal working notes
Confidential client information
Restricted personal data
```

Hermes 默认只可处理 public / internal 级别信息。

Confidential 和 restricted 信息必须遵守人工确认和访问控制。

---

## 39.3 Retention Policy

推荐保留周期：

```yaml
logs: 30-90 days
raw drafts: 30 days
inbox items: 7-30 days
research inbox: 90 days before review
records: according to business need
sensitive records: explicit retention_until required
proposals: archive after applied or rejected
projects: archive after closeout
```

---

## 39.4 Deletion Policy

删除规则：

- 不删除历史事实，除非错误或合规要求
- Records 默认不覆盖，只追加 correction
- Sensitive data 可根据 retention policy 删除或 redacted
- 删除前应记录 deletion note when appropriate

---

## 39.5 Export Policy

导出 Vault 或客户资料前必须检查：

- sensitivity
- customer ownership
- confidential records
- internal strategy
- private credentials
- archive leakage

---

# 40. Backup and Recovery Policy

位置：

```text
00-Core/Backup-and-Recovery-Policy.md
```

目标：

保证长期记忆不会因误写、误删、错误晋升而不可恢复。

---

## 40.1 Backup Requirements

推荐：

- Git versioning
- local backup
- encrypted cloud backup if appropriate
- weekly snapshot
- pre-audit snapshot
- pre-bulk-operation snapshot

---

## 40.2 Recovery Requirements

任何批量操作前必须有：

```text
operation summary
affected files list
rollback path
backup confirmation
```

---

## 40.3 Rollback Policy

Class A 更新必须可回滚。

Proposal 中必须包含 rollback plan。

Bulk changes 必须保留 operation log。

---

# 41. Standard Templates

## 41.1 Product Template

```markdown
---
type: product
memory_layer: facts
status: active
authority: ssot
owner: human
created:
updated:
review_date:
expires_at:
source:
source_quality:
confidence: high
write_policy: review_required
approved_by:
sensitivity: internal
retrieval_scope: default
schema: product.schema.yml
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

| Date | Change | Source | Proposal | Approved By |
|---|---|---|---|---|
```

---

## 41.2 Customer Profile Template

```markdown
---
type: customer_profile
memory_layer: facts
status: active
authority: ssot
owner: human
created:
updated:
review_date:
expires_at:
source:
source_quality:
confidence:
write_policy: review_required
approved_by:
sensitivity: confidential
retrieval_scope: default
schema: customer_profile.schema.yml
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

## Related Records

## Changelog

| Date | Change | Source | Proposal | Approved By |
|---|---|---|---|---|
```

---

## 41.3 Record Template

```markdown
---
type: record
memory_layer: records
status: active
authority: raw
owner: hermes
created:
updated:
record_date:
source:
source_quality: internal_record
confidence: medium
write_policy: append_only
sensitivity: internal
retention_until:
retrieval_scope: evidence_only
schema: record.schema.yml
related:
tags:
---

# Record Title

## Record Type

meeting | email | call | feedback | transcript | import | source

## Date

## Participants / Source

## Context

## Raw Notes / Summary

## Decisions Mentioned

## Action Items

## Potential Fact Updates

## Potential Learnings

## Required Proposals

## Correction Log

| Date | Correction | Source | By |
|---|---|---|---|
```

---

## 41.4 Research Template

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
source_quality:
confidence:
write_policy: open
sensitivity: internal
retrieval_scope: evidence_only
schema: research.schema.yml
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

## 41.5 Case Template

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
source_quality:
confidence:
write_policy: review_required
approved_by:
sensitivity: internal
retrieval_scope: default
schema: case.schema.yml
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

## Related Records

## Related Research

## Possible Learning
```

---

## 41.6 Learning Template

```markdown
---
type: learning
memory_layer: insights
status: active
authority: approved
owner: human
created:
updated:
review_date:
expires_at:
source:
source_quality:
confidence:
write_policy: review_required
approved_by:
sensitivity: internal
retrieval_scope: default
schema: learning.schema.yml
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

## 41.7 Rule Template

```markdown
---
type: rule
memory_layer: rules
status: active
authority: ssot
owner: human
created:
updated:
review_date:
expires_at:
source:
source_quality:
confidence: high
write_policy: review_required
approved_by:
sensitivity: internal
retrieval_scope: default
schema: rule.schema.yml
related:
tags:
---

# Rule Name

## Purpose

## Applies To

## Input Conditions

## Rule

## Procedure

## Output Standard

## Do

## Do Not

## Exceptions

## Related Facts

## Related Cases

## Changelog

| Date | Change | Source | Proposal | Approved By |
|---|---|---|---|---|
```

---

## 41.8 Project Closeout Template

```markdown
---
type: project_closeout
memory_layer: projects
status: needs_review
authority: provisional
owner: hermes
created:
updated:
review_date:
expires_at:
source:
source_quality:
confidence:
write_policy: review_required
sensitivity: internal
retrieval_scope: evidence_only
schema: project_closeout.schema.yml
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

## Customer Profile Updates to Propose

## Records to Preserve

## Cases to Create

## Learnings to Extract

## Rules to Update

## Materials to Archive

## Final Status
```

---

## 41.9 Proposal Template

```markdown
---
type: proposal
memory_layer: proposal
status: pending
authority: none
owner: hermes
created:
updated:
target_file:
proposal_type: update
source:
source_quality:
confidence:
write_policy: open
reviewer: human
approved_by:
sensitivity: internal
retrieval_scope: excluded
schema: proposal.schema.yml
related:
tags:
---

# Proposal Title

## Target File

## Proposal Type

update | merge | deprecate | supersede | promote | archive | conflict_resolution | schema_update | security_update

## Current State

## Proposed Change

## Reason

## Source Evidence

## Risk

## Affected Files

## Suggested Changelog Entry

## Rollback Plan

## Decision

pending | approved | rejected | needs_revision | applied

## Reviewer Notes
```

---

## 41.10 Conflict Template

```markdown
---
type: conflict
memory_layer: proposal
status: pending
authority: none
owner: hermes
created:
updated:
source:
write_policy: open
reviewer: human
sensitivity: internal
retrieval_scope: excluded
related:
tags:
---

# Conflict Title

## Conflict

## Source A

## Source B

## Current SSOT

## Proposed Resolution

## Risk

## Decision

## Changelog
```

---

## 41.11 Decision Template

```markdown
---
type: decision
memory_layer: facts
status: active
authority: approved
owner: human
created:
updated:
source:
source_quality:
confidence: high
write_policy: review_required
approved_by:
sensitivity: internal
retrieval_scope: default
schema: decision.schema.yml
related:
tags:
---

# Decision Title

## Date

## Context

## Options Considered

## Decision

## Decided By

## Reason

## Impacted Files

## Follow-up

## Changelog
```

---

# 42. Claudian Skills and Workflows

Claudian 支持 slash commands 和 skills。

本系统应把重复治理动作封装为 Vault-level skills。

---

## 42.1 Recommended Vault-Level Skills

```text
/triage-note
/classify-memory
/check-ssot
/create-proposal
/review-proposal
/promote-research
/promote-record
/project-closeout
/check-conflict
/update-changelog
/validate-schema
/audit-vault
/review-expiring-research
/find-duplicate-candidates
/find-orphan-notes
/generate-knowledge-debt-dashboard
/generate-memory-evaluation-dashboard
/security-review
/retention-cleanup
```

---

## 42.2 Skill Rules

所有 governance skills 必须遵守：

- 不直接覆盖 Class A
- 不跳过 Source of Truth System
- 不把 raw research 晋升为 fact
- 不把 raw record 晋升为 fact without proposal
- 不删除历史记录
- 不把 proposal 当批准结果
- 不默认检索 Archive / Logs / Drafts
- 不绕过 schema validation
- 不绕过 security policy

---

## 42.3 Suggested Skill Behaviors

### /triage-note

输入：当前 note 或 selected text。

输出：

- knowledge type
- suggested location
- required metadata
- whether proposal is needed

### /check-ssot

输入：主题或目标文件。

输出：

- existing SSOT candidates
- duplicate risk
- recommended target file

### /create-proposal

输入：目标文件和修改内容。

输出：

- proposal file
- source evidence
- suggested changelog
- risk assessment
- rollback plan

### /promote-record

输入：Record file。

输出：

- possible Facts update
- possible Decision
- possible Timeline append
- possible Case
- required proposals

### /project-closeout

输入：项目文件夹。

输出：

- facts to promote
- records to preserve
- cases to create
- learnings to extract
- rules to propose
- archive checklist

### /validate-schema

输入：文件或 folder。

输出：

- missing metadata
- invalid values
- required review
- queue entry

### /audit-vault

输入：Vault 或 folder。

输出：

- missing metadata
- stale research
- duplicate candidates
- orphan notes
- pending proposals
- knowledge debt metrics
- archive leakage
- schema failures

---

# 43. Automation and Enforcement

V7 鼓励把治理规则自动化。

---

## 43.1 Automation Targets

优先自动化：

- metadata completeness check
- schema validation
- expired research detection
- orphan note detection
- duplicate candidate detection
- pending proposal aging
- archive leakage detection
- records triage queue generation
- project closeout queue generation
- knowledge debt dashboard generation

---

## 43.2 Enforcement Levels

```text
Level 0: Manual guidance
Level 1: Warning only
Level 2: Add to review queue
Level 3: Block direct write
Level 4: Require human approval
```

推荐：

```text
Class A → Level 3 or 4
Class B → Level 2 or 3
Class R → Level 2
Class C → Level 1
```

---

## 43.3 Automation Safety

自动化不得：

- 删除 Class A 文件
- 批量覆盖 SSOT
- 自动批准 proposal
- 自动把 Research 变成 Fact
- 自动把 Record 变成 current profile
- 自动修改 Security Policy

---

# 44. Human Review UX

系统必须降低人工审核成本。

---

## 44.1 Review Queue Design

每条 review item 应显示：

```text
Title
File
Type
Risk
Age
Source
Required action
Recommended action
```

---

## 44.2 Proposal Review UX

Proposal 页面必须让 reviewer 快速看到：

- 改哪里
- 为什么改
- 依据是什么
- 风险是什么
- 不改会怎样
- rollback 怎么做
- changelog 怎么写

---

## 44.3 Review Outcomes

允许的结果：

```text
approve
reject
needs_revision
apply_with_changes
archive
merge
supersede
request_more_evidence
```

---

# 45. Failure Modes and Recovery

V7 明确常见失败模式和修复方式。

---

## 45.1 Common Failure Modes

```text
Duplicate SSOT files
Draft used as fact
Research used as fact
Record used as current profile
Archive used as current truth
Rule created from one anecdote
Customer profile stale
Product facts outdated
Meeting notes never triaged
Projects never closed out
Proposal backlog grows
Schema ignored
Security-sensitive data stored in ordinary notes
Logs pollute retrieval
```

---

## 45.2 Recovery Actions

对应修复：

```text
Duplicate SSOT → create merge proposal
Draft used as fact → mark contamination and correct answer/source
Research used as fact → downgrade authority and create review proposal
Record used as current profile → create customer profile proposal
Archive leakage → update retrieval filters
Rule from anecdote → downgrade to Learning or Case
Stale profile → review customer records and update via proposal
Untriaged records → run /promote-record queue
Project not closed → run /project-closeout
Schema ignored → add schema failure queue
Sensitive data exposed → redact or move, then security review
```

---

# 46. Operating Cadence

## 46.1 Daily

Hermes may write to:

- Drafts
- Inbox
- Project notes
- Research inbox
- Records
- Logs
- Proposals

Hermes should not directly modify:

- Core
- Brand
- Products
- Rules
- Customer current profile
- Security policy
- Schema policy

---

## 46.2 Weekly

Review:

- Inbox
- Drafts
- Research inbox
- Records triage
- Active project notes
- Proposal queue
- Conflict queue
- Schema failures

Actions:

- delete noise
- classify useful notes
- merge duplicates
- promote valid knowledge
- archive low-value material
- approve or reject proposals
- create records promotion proposals

---

## 46.3 Monthly

Run Knowledge Review.

Check:

- review queues
- orphan notes
- duplicate candidates
- expiring research
- missing metadata
- open conflicts
- pending proposals
- records triage
- project closeout queue
- knowledge debt dashboard
- memory evaluation dashboard

---

## 46.4 Quarterly

Run Knowledge Audit.

Check:

- SSOT integrity
- rule validity
- Core Memory size
- archive boundaries
- project closeouts
- metadata completeness
- graph quality
- source quality
- schema health
- records promotion health
- Claudian skills compliance
- Hermes protocol compliance
- security and retention compliance

---

# 47. Migration Plan from V6 to V7

## 47.1 Migration Goals

把 V6 平滑升级到 V7。

不推倒重来。

只做必要结构调整和运行层补强。

---

## 47.2 Step 1 — Add New Directories

新增：

```text
06-Records/
70-Schemas/
81-Dashboards/
94-Review-Queues/
```

---

## 47.3 Step 2 — Move Meeting Notes

将：

```text
01-Facts/Customers/{customer}/meetings/
```

迁移到：

```text
06-Records/Customers/{customer}/Meetings/
```

并在 customer profile 或 timeline 中保留 links。

---

## 47.4 Step 3 — Update Source of Truth Map

增加：

- Records entries
- Schema entries
- Retrieval runtime entries
- Context packing entries
- Security policy entries

---

## 47.5 Step 4 — Add Metadata Fields

为正式文件逐步补充：

```yaml
sensitivity:
retrieval_scope:
schema:
retention_until:
```

---

## 47.6 Step 5 — Create Initial Schemas

优先创建：

```text
product.schema.yml
customer_profile.schema.yml
rule.schema.yml
research.schema.yml
record.schema.yml
proposal.schema.yml
```

---

## 47.7 Step 6 — Create Dashboards

新增：

```text
81-Dashboards/Knowledge-Debt-Dashboard.md
81-Dashboards/Memory-Evaluation-Dashboard.md
81-Dashboards/Proposal-Dashboard.md
```

---

## 47.8 Step 7 — Update Hermes Protocol

让 Hermes 在工作前额外检查：

- retrieval preset
- context packing
- schema requirement
- record vs fact distinction
- security and retention

---

# 48. Success Criteria

系统运行 12 个月后，必须能够在 30 秒内定位：

- 品牌定位
- 产品参数
- 客户当前状态
- 客户历史变化
- 已确认决策
- 原始会议记录
- 原始 feedback
- SEO 规范
- Social 规范
- SOP
- Agent 行为规则
- 核心经验
- 项目记录
- 研究来源
- 失效知识
- 当前权威版本
- 待审核 proposal
- 开放冲突
- schema failures
- records triage 队列
- 知识债务状态
- memory evaluation 状态

必须能够明确回答：

```text
什么是事实？
什么是规则？
什么是经验？
什么是研究？
什么是原始证据？
什么是草稿？
什么是 proposal？
什么已经失效？
什么是当前版本？
谁可以修改？
来源是什么？
何时需要复审？
哪个文件是 SSOT？
这个修改是否需要 approval？
这个内容是否可参与默认检索？
这个回答用了哪些记忆？
这个记忆是否过期？
这个文件是否通过 schema？
这个内容是否包含敏感信息？
```

如果不能回答，说明知识治理失败。

---

# 49. Ultimate Principle

事实只有一个版本。

规则只有一个来源。

经验必须经过验证。

研究必须允许过期。

原始记录必须区别于当前事实。

项目必须允许结束。

历史必须可以追溯。

冲突必须可以解决。

权限必须可以执行。

Schema 必须可以检查。

检索必须可以解释。

Context 必须可以打包。

评估必须可以量化。

敏感信息必须可以保护。

Proposal 必须可审核。

Runtime capability 不等于 write permission。

核心记忆必须持续精简。

AI 可以无限生成。

知识库必须持续收敛。
