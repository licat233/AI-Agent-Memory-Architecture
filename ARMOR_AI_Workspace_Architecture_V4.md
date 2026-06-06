# ARMOR AI Workspace Architecture V4

## Vision

目标不是构建一个能记住所有内容的 AI。

目标是构建一个长期稳定、可治理、可扩展、可审计的 AI 工作系统。

系统必须保证：

- 永远知道事实在哪里
- 永远知道规则在哪里
- 永远知道经验在哪里
- 永远知道谁可以修改什么
- 永远知道知识如何晋升
- 永远知道知识何时失效

AI 可以生成无限内容。

知识库必须持续收敛。

------

# First Principle

## SSOT

Single Source of Truth

所有正式知识只能存在一个权威版本。

允许：

- 引用
- 双链
- 聚合视图
- Dataview
- 索引页

禁止：

- 内容复制
- 多版本事实
- 重复知识
- 平行真相

错误：

Product-A-v1.md

Product-A-v2.md

Product-A-final.md

Product-A-final-final.md

正确：

Product-A.md

所有更新都发生在同一文件。

------

# System Roles

## Obsidian

角色：

Knowledge System

职责：

- 长期知识存储
- 知识治理
- 知识演化
- 知识检索

原则：

Vault 是唯一长期记忆。

------

## Hermes

角色：

Execution Agent

职责：

- 检索
- 分析
- 写作
- 自动化
- 项目执行
- 研究

原则：

Hermes 负责生产内容。

Hermes 不定义真相。

Hermes 不拥有长期记忆。

所有知识来自检索。

------

## Claudian

角色：

Knowledge Steward

职责：

- 分类
- 去重
- 重构
- 双链建设
- 知识审核
- 知识晋升

原则：

Claudian 负责治理知识。

不负责业务执行。

------

# Memory Model

系统采用四层记忆模型。

------

## Layer 1

Working Memory

生命周期：

单任务

来源：

- 当前会话
- 当前项目
- 当前上下文

任务结束后销毁。

禁止长期保存。

------

## Layer 2A

Facts Memory

存放：

- 品牌事实
- 产品事实
- 客户事实

特点：

唯一正确答案。

允许覆盖更新。

------

## Layer 2B

Rules Memory

存放：

- SOP
- SEO规则
- Social规则
- Agent规则

特点：

规范执行方式。

允许版本迭代。

------

## Layer 2C

Insights Memory

存放：

- Learnings
- Cases

特点：

经验知识。

不是事实。

不是规则。

必须经过验证。

------

## Layer 3

Research Memory

存放：

- 市场研究
- 竞品研究
- 临时分析
- 外部资料

特点：

未成为正式知识。

具有过期可能。

------

## Layer 4

Archive Memory

存放：

- 历史项目
- 历史研究
- 历史案例
- 失效规则

默认不参与检索。

------

# Vault Structure

Vault/

00-Core-Memory/

01-Facts/

02-Rules/

03-Insights/

04-Research/

05-Projects/

90-Drafts/

91-Inbox/

92-Logs/

99-Archive/

------

# Core Memory

位置：

00-Core-Memory/

内容：

- 品牌定位
- 工作原则
- Agent行为规范
- 决策原则
- 系统宪法

要求：

控制在3000字以内。

只保留系统级原则。

禁止细节知识进入。

Core Memory 是系统宪法。

不是百科全书。

------

# Facts Layer

01-Facts/

包含：

Brand/

Products/

Customers/

------

## Brand

存放：

- 品牌定位
- 品牌价值观
- 品牌语调
- 品牌视觉规则

默认只读。

------

## Products

规则：

一个产品一个文件。

示例：

Products/

Armor-SEO.md

Armor-AI.md

禁止：

Armor-SEO-v2.md

Armor-SEO-new.md

------

## Customers

Customers/

Acme/

profile.md

timeline/

meetings/

feedback/

------

### profile.md

当前状态

允许更新

内容：

- 行业
- 商业模式
- 联系方式
- 当前目标
- 当前痛点

------

### timeline

Append Only

按年度拆分

timeline/

2025.md

2026.md

2027.md

记录：

- 决策
- 合作事件
- 需求变化

禁止修改历史。

------

### meetings

独立会议记录

meetings/

2026-01-10.md

2026-03-15.md

------

### feedback

季度反馈

feedback/

2026-Q1.md

2026-Q2.md

------

# Rules Layer

02-Rules/

包含：

SEO/

Social/

SOP/

Agents/

------

规则特点：

描述：

应该如何做。

而不是：

发生过什么。

------

# Insights Layer

03-Insights/

包含：

Cases/

Learnings/

------

## Cases

记录：

发生了什么。

案例不是规则。

案例不是事实。

案例只是事件。

------

## Learnings

记录：

为什么有效。

为什么失败。

必须经过验证。

示例：

SEO-Learnings.md

Content-Learnings.md

Sales-Learnings.md

Automation-Learnings.md

------

# Research Layer

04-Research/

00-Inbox/

01-Reviewed/

99-Archive/

------

## Inbox

Hermes 可直接写入。

未经验证。

------

## Reviewed

通过人工审核。

允许检索。

------

## Archive

过期研究。

默认不检索。

------

## Expiration Rule

Research 超过90天未被引用：

自动归档。

------

# Projects Layer

05-Projects/

Project-A/

Project-B/

Project-C/

------

项目区允许：

- 自由写作
- 自由实验
- 自由研究

项目结束：

归档。

------

# Temporary Layer

90-Drafts/

91-Inbox/

92-Logs/

------

## Drafts

草稿。

自由写入。

------

## Inbox

未分类内容。

等待处理。

------

## Logs

Agent日志。

记录：

- Task
- Error
- Debug

禁止进入知识检索层。

------

# Archive Layer

99-Archive/

包含：

- 历史项目
- 历史研究
- 历史规则
- 历史案例

默认不参与检索。

------

# Knowledge Promotion Framework

知识必须晋升。

禁止直接进入核心层。

------

Draft

↓

Research

↓

Learning

↓

Rule

↓

Core Memory

------

## Draft → Research

值得记录。

------

## Research → Learning

多次验证。

------

## Learning → Rule

具备稳定复用价值。

------

## Rule → Core Memory

系统级原则。

长期稳定。

------

# Knowledge Graph Metadata

所有正式知识统一 Frontmatter。

```yaml
type:
status:
owner:
review_date:
created:
updated:
related:
tags:
```

示例：

```yaml
type: product

status: active

owner: armor

review_date: 2026-12-01

related:
  - customer/acme
  - case/seo-growth

tags:
  - seo
  - ai
```

作用：

构建轻量知识图谱。

支持关系检索。

支持未来RAG增强。

------

# Permission Model

## Class A

核心资产

包含：

Core Memory

Brand

Products

Rules

权限：

默认只读。

修改必须审核。

------

## Class B

知识资产

包含：

Customers

Cases

Learnings

Research

Projects

允许新增。

遵循结构规范。

------

## Class C

临时资产

包含：

Drafts

Inbox

Logs

完全开放。

------

# Memory Write Pipeline

禁止直接写入核心知识。

统一流程：

Hermes

↓

Draft

↓

Review

↓

Promote

↓

SSOT

------

## Stage 1

Create Draft

Hermes 输出。

进入：

Drafts

Research

Projects

------

## Stage 2

Review

Claudian 审核：

- 是否重复
- 是否准确
- 是否已有SSOT

------

## Stage 3

Promote

符合条件：

升级进入正式知识层。

------

## Stage 4

Merge

更新唯一权威文件。

不创建平行版本。

------

# Agent Write Rules

写入前必须判断：

------

Step 1

这是事实？

还是经验？

事实：

进入 Facts

经验：

进入 Learnings

事件：

进入 Cases

------

Step 2

是否已有权威版本？

有：

更新原文件。

无：

创建新文件。

------

Step 3

是否属于核心资产？

如果是：

生成修改建议。

不自动覆盖。

------

# Retrieval Rules

任务开始：

优先加载：

1 Core Memory

2 Relevant Facts

3 Relevant Rules

4 Relevant Learnings

然后：

按需检索。

禁止：

加载整个 Vault。

------

# Knowledge Review

每月执行：

Knowledge Review

检查：

- 重复文件
- 孤立文档
- 未分类内容
- 失效研究

------

# Knowledge Audit

每季度执行：

Knowledge Audit

检查：

- SSOT完整性
- Core Memory体积
- Rule有效性
- Learning时效性
- Metadata完整性
- Graph连接质量

------

# Success Criteria

系统运行12个月后：

能够在30秒内定位：

- 品牌定位
- 产品参数
- 客户状态
- SEO规范
- SOP
- 核心经验
- 项目记录

能够明确回答：

什么是事实？

什么是规则？

什么是经验？

什么已经失效？

如果不能回答。

说明知识治理失败。

------

# Ultimate Principle

事实只有一个版本。

规则只有一个来源。

经验必须经过验证。

研究必须允许过期。

项目必须允许结束。

核心记忆必须持续精简。

AI 可以无限生成。

知识库必须持续收敛。