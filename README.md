# AI Agent Memory Architecture v1.6.0

> Long-term, auditable, and governed memory architectures for AI workspaces.  
> 面向 AI 工作空间的长期、可审计、可治理记忆架构。

[English](#english) | [中文](#中文)

---

## English

AI Agent Memory Architecture is a Markdown/Obsidian-based specification for building durable memory systems for AI agents. It treats memory as a governed knowledge operating system rather than a loose folder, vector-store dump, runtime cache, or prompt extension.

The goal is not to remember everything. The goal is to preserve only memory that is useful, source-backed, reviewable, retrievable, and honest about its authority.

**Project version:** v1.6.0

### Active Architecture Branch

| Branch | Version | Scenario | Status |
| --- | --- | --- | --- |
| [ARMOR Enterprise AI Workspace](enterprise/README.md) | V7.2 Stable | Teams, business operations, brand/product/customer knowledge, multi-agent workspaces | Stable |

PAMA Personal V5.3 Stable has been archived under `archive/personal/PAMA-Personal-v5.3-Stable/` and is not part of the active install or update path for new releases.

Runtime note: This project has no dependency on UI-side Obsidian executor plugins. Trusted agent runtimes such as Hermes, Claude Code, Codex, Opencode, Cline, OpenHands, and custom agents can operate the Vault directly when they follow the routers, permission rules, retrieval policy, and proposal workflow.

### Architecture Diagrams

#### ARMOR Enterprise V7.2 Stable

![ARMOR Enterprise V7.2 Stable architecture overview](assets/armor-enterprise-v7-2-overview.svg)

### Branch Overview

#### ARMOR Enterprise AI Workspace

ARMOR is designed for business-critical AI memory. It introduces Single Source of Truth (SSOT), permission classes, proposal-based review, source-based confidence labels, lifecycle rules, retrieval filters, schema validation, and low-maintenance operations.

Use it when a team needs AI agents to manage brand facts, product specs, customer profiles, SOPs, meeting records, research, and project knowledge without letting unreviewed notes become current truth.

### Core Ideas

- **Store lower when uncertain**: uncertain information belongs in drafts, working memory, records, or research, not in authoritative facts.
- **Capture is not authority**: agents may capture quickly, but only governed review can promote memory into truth-bearing layers.
- **Conservative retrieval**: drafts, logs, raw records, inboxes, proposals, and archives are excluded from default truth retrieval.
- **Runtime memory is not long-term memory**: runtime databases, embeddings, and indexes are infrastructure only.

### Governance Pattern

| Layer Type | ARMOR Example | Purpose |
| --- | --- | --- |
| Core governance | `00-Core/` | Constitution, operating protocol, permission and retrieval rules |
| Authoritative truth | `01-Facts/`, `02-Rules/` | Stable facts, rules, and approved standards |
| Validated learning | `03-Insights/` | Cases, lessons, reviews, decision feedback |
| External or uncertain knowledge | `04-Research/` | Research, hypotheses, decaying assumptions |
| Active work | `05-Projects/` | Current execution and project workspaces |
| Evidence | `06-Records/` | Raw source material; evidence is not automatically fact |
| Operations | `70-Schemas/`, `80-Indexes/`, `81-Dashboards/` | Validation, navigation, audits, dashboards |
| Low-authority capture | `90-Drafts/`, `91-Inbox/`, `92-Logs/`, `93-Proposals/` | Fast capture, pending review, no default truth authority |
| Cold storage | `99-Archive/` | Deprecated, expired, superseded, or explicitly recalled history |

Top-level vault structure is treated as a frozen architecture boundary. Domain-specific subfolders may grow, but agents should not invent or merge top-level layers without explicit human approval.

### Memory Promotion Pipeline

```text
Conversation / raw input
        |
        v
Low-authority capture
Working memory / records / drafts / inbox / research inbox
        |
        v
Evidence check + review cycle + proposal when needed
        |
        v
Human approval for high-authority or high-risk changes
        |
        v
Authoritative memory
Facts / rules / truth / validated insights / reviewed research
```

### Agent Runtime Integration

This project separates memory governance from agent execution.

ARMOR defines where memory belongs, what authority it has, how it is promoted, and what must be excluded from default truth retrieval. Runtime tools such as Hermes, Claude Code, Codex, Opencode, MCP servers, embeddings, and local indexes may help agents operate on a Vault, but they do not become sources of truth.

Runtime principle:

```text
Tools provide capability.
The architecture defines permission.
The Vault remains the durable memory system.
```

### Quick Start

1. Use the active [Enterprise](enterprise/README.md) architecture branch.
2. Create an Obsidian Vault or trusted Markdown directory using the branch's frozen top-level structure.
3. Add the required core files, schemas, templates, retrieval rules, and permission rules.
4. Point your AI agent's long-term memory path to the vault.
5. Keep runtime databases, embeddings, and indexes as runtime infrastructure only.
6. Let the agent capture freely into low-authority layers, then promote only source-backed, reviewed memory into authoritative layers.

### Installation

Copy this prompt to your AI agent. It will install the default enterprise ARMOR architecture into your chosen Obsidian Vault or Markdown directory:

```text
Please read and execute AGENT_INSTALL.md from this repository:
https://github.com/licat233/AI-Agent-Memory-Architecture

Help me install AI Agent Memory Architecture.
Install the default enterprise/ARMOR version.
Target Vault path: <paste your Vault or Markdown directory path here>
Do not install any Obsidian UI plugin.
Do not use runtime memory as long-term memory.
Create missing Vault folders, copy missing core documents, the Frontmatter Standard, and the Document Map files, preserve existing files, write an installation log, and run the validation checklist.
```

### Updating

Copy this prompt to your AI agent when an existing Vault needs to be aligned with the latest architecture:

```text
Please read and execute AGENT_UPDATE.md from this repository:
https://github.com/licat233/AI-Agent-Memory-Architecture

Help me update my existing AI Agent Memory Architecture Vault.
Target architecture: AI Agent Memory Architecture v1.6.0.
Default branch: ARMOR Enterprise V7.2 Stable.
Target Vault path: <paste your Vault or Markdown directory path here>
Do not install any Obsidian UI plugin.
Do not use runtime memory as long-term memory.
Preserve user content and history.
Archive superseded active files instead of deleting them.
Update active Core, Indexes, runtime adaptation guides, routers, governance files, the Frontmatter Standard, and the Document Map.
Mark obsolete pending proposals as superseded when they point to retired files.
Write an update log and run the validation checklist.
```

### Documentation

| Document | Description |
| --- | --- |
| [Changelog](CHANGELOG.md) | Release history and notable changes by project version |
| [Architecture Overview](ARCHITECTURE.md) | Single-file architecture orientation for AI agents before reading deeper specs |
| [Agent Vault Bootstrap Rule](AGENT_VAULT_BOOTSTRAP_RULE.md) | Copy-ready startup rule that tells agents where to enter a Vault before searching |
| [Frontmatter Standard](FRONTMATTER_STANDARD.md) | Canonical metadata fields, YAML rules, branch mappings, registry governance, and legacy migration |
| [Document Map Standard](DOCUMENT_MAP_STANDARD.md) | Static Vault maps, dynamic Obsidian Bases registry, reading order, and maintenance rules |
| [Template Automation Guide](TEMPLATE_AUTOMATION_GUIDE.md) | Plain Markdown, Obsidian Core Templates, and safe optional Templater profiles |
| [Agent Installation Guide](AGENT_INSTALL.md) | Instructions an AI agent can follow to install ARMOR into a Vault |
| [Agent Update Guide](AGENT_UPDATE.md) | Instructions an AI agent can follow to update an existing Vault and clean stale active files |
| [Enterprise README](enterprise/README.md) | Enterprise overview, ARMOR quick start, permission model, lifecycle rules |
| [ARMOR V7.2 Stable](enterprise/V7_2_Stable.md) | Full enterprise architecture specification |
| [ARMOR V7.1.5 Governance Patch](enterprise/V7_1_5_Governance_Patch.md) | Governance layer carried forward into V7.2: confidence labels, fact creation gate, write quality rules |
| [ARMOR Prompt Intake Router](enterprise/Prompt_Intake_Router.md) | First-layer intent router for ambiguous or high-risk prompts |
| [ARMOR Memory Write Router](enterprise/Memory_Write_Router.md) | Mandatory routing rules for user-requested permanent memory |
| [ARMOR Root-Cause Fix Protocol](enterprise/Root_Cause_Fix_Protocol.md) | Mandatory protocol for fixing errors at their source layer |
| [ARMOR Runtime Memory Policy](enterprise/Runtime_Memory_Policy.md) | Enterprise policy for keeping runtime memory low-authority and temporary |
| [Agent Runtime Adaptation Guide](enterprise/agent_runtime_adaptation_guide.md) | How to adapt any trusted agent runtime to ARMOR |
| [Multi-Agent Shared Vault Governance](enterprise/multi_agent_shared_vault_governance.md) | How Hermes, Codex, Claude Code, and other agents can safely share one ARMOR Vault |
| [ARMOR Project Execution Workflow](enterprise/Project_Execution_Workflow.md) | Optional low-authority task execution templates for complex project work |
| [Agent Project Execution Prompt](enterprise/Agent_Project_Execution_Prompt.md) | Copy-ready prompt snippets for configuring agents to use project execution templates |
| [Archived Personal Branch](archive/personal/README.md) | Historical PAMA archive; not part of the active install path |

---

## 中文

AI Agent Memory Architecture 是一套基于 Markdown / Obsidian Vault 的 AI 智能体长期记忆架构规范。它不把记忆当作松散文件夹、向量库堆料、运行时缓存或超长 Prompt，而是把记忆视为一套可治理的知识操作系统。

记忆系统的目标不是记住一切，而是只保留有用、有来源、可复核、可检索，并且诚实标注自身权威等级的记忆。

**项目版本：** v1.6.0

### 当前活跃架构分支

| 分支 | 版本 | 场景 | 状态 |
| --- | --- | --- | --- |
| [ARMOR 企业级 AI 工作空间](enterprise/README.md) | V7.2 Stable | 团队、业务运营、品牌/产品/客户知识、多智能体工作区 | 稳定 |

PAMA Personal V5.3 Stable 已归档到 `archive/personal/PAMA-Personal-v5.3-Stable/`，不再属于新版的活跃安装或更新路径。

运行时说明：本项目不依赖 Obsidian UI 侧执行插件。Hermes、Claude Code、Codex、Opencode、Cline、OpenHands 及自定义智能体等受信任运行时只要遵循路由器、权限规则、检索策略和提案工作流，即可直接操作 Vault。

### 架构图

#### ARMOR Enterprise V7.2 Stable

![ARMOR Enterprise V7.2 Stable 架构图](assets/armor-enterprise-v7-2-overview.svg)

### 分支概览

#### ARMOR 企业级 AI 工作空间

ARMOR 面向业务关键场景的 AI 记忆系统。它引入唯一事实源（SSOT）、权限分级、提案人审、基于来源的置信度标签、生命周期规则、检索过滤、Schema 校验和低维护运营机制。

当团队需要 AI 智能体管理品牌事实、产品参数、客户画像、SOP、会议记录、研究资料和项目知识，同时又不能让未经审查的笔记污染当前事实时，应使用 ARMOR。

### 核心思想

- **不确定则向低权层保存**：不确定信息应进入草稿、工作记忆、记录或研究层，而不是直接成为权威事实。
- **捕获不等于授权**：智能体可以快速捕获，但只有经过治理和复核的信息才能晋升为长期真相。
- **默认保守检索**：草稿、日志、原始记录、收件箱、提案和归档默认不得作为当前事实参与检索。
- **运行时记忆不是长期记忆**：运行时数据库、Embedding 和索引只属于基础设施。

### 治理模式

| 层级类型 | ARMOR 示例 | 用途 |
| --- | --- | --- |
| 核心治理 | `00-Core/` | 宪法、运行协议、权限规则、检索规则 |
| 权威真相 | `01-Facts/`, `02-Rules/` | 稳定事实、规则和已批准标准 |
| 验证经验 | `03-Insights/` | 案例、教训、复盘、决策反馈 |
| 外部或不确定知识 | `04-Research/` | 研究、假设、会衰减的推断 |
| 活动工作 | `05-Projects/` | 当前执行和项目工作区 |
| 原始证据 | `06-Records/` | 原始来源材料；证据不自动等于事实 |
| 运维设施 | `70-Schemas/`, `80-Indexes/`, `81-Dashboards/` | 校验、导航、审计、仪表盘 |
| 低权捕获 | `90-Drafts/`, `91-Inbox/`, `92-Logs/`, `93-Proposals/` | 快速捕获、待审查、默认无真相权威 |
| 冷归档 | `99-Archive/` | 失效、过期、被推翻或仅显式召回的历史 |

顶层 Vault 目录属于冻结架构边界。领域子目录可以扩展，但 AI 智能体不得在没有人类明确授权的情况下新增、合并或重命名顶层层级。

### 记忆晋升流水线

```text
会话 / 原始输入
        |
        v
低权捕获
工作记忆 / 原始记录 / 草稿 / 收件箱 / 研究收件箱
        |
        v
证据检查 + 周期复盘 + 必要时生成提案
        |
        v
高权或高风险变更由人类审批
        |
        v
权威记忆
事实 / 规则 / 真理 / 已验证洞察 / 已审查研究
```

### 智能体运行时集成

本项目将记忆治理和智能体执行能力分离。

ARMOR 定义记忆应该存在哪里、具有什么权威、如何晋升，以及哪些内容不得进入默认真相检索。Hermes、Claude Code、Codex、Opencode、MCP servers、Embedding 和本地索引等运行时工具可以帮助智能体操作 Vault，但它们本身不是事实源。

运行时原则：

```text
工具提供能力。
架构定义权限。
Vault 保持为持久记忆系统。
```

### 快速开始

1. 使用当前活跃的 [企业版](enterprise/README.md) 架构分支。
2. 在 Obsidian Vault 或可信 Markdown 目录中创建该分支的冻结顶层结构。
3. 添加必要的核心文件、Schema、模板、检索规则和权限规则。
4. 将 AI 智能体的长期记忆路径指向该 Vault。
5. 运行时数据库、Embedding 和索引只作为运行基础设施使用。
6. 允许智能体自由写入低权层，再将有来源、经复核的信息晋升到权威层。

### 安装教程

复制下面这段内容给你的 AI Agent，它会把默认企业版 ARMOR 架构安装到你指定的 Obsidian Vault 或 Markdown 目录：

```text
请阅读并执行这个仓库里的 AGENT_INSTALL.md：
https://github.com/licat233/AI-Agent-Memory-Architecture

请帮我安装 AI Agent Memory Architecture。
安装默认 enterprise/ARMOR 版本。
目标 Vault 路径：<在这里粘贴你的 Vault 或 Markdown 目录路径>
不要安装任何 Obsidian UI 插件。
不要把 runtime memory 当作长期记忆。
请创建缺失的 Vault 目录、复制缺失的核心架构文档、Frontmatter 规范和 Document Map 文件、保留已有文件、写入安装日志，并执行验证清单。
```

### 更新教程

当已有 Vault 需要对齐到最新架构时，复制下面这段内容给你的 AI Agent：

```text
请阅读并执行这个仓库里的 AGENT_UPDATE.md：
https://github.com/licat233/AI-Agent-Memory-Architecture

请帮我更新现有的 AI Agent Memory Architecture Vault。
目标架构：AI Agent Memory Architecture v1.6.0。
默认分支：ARMOR Enterprise V7.2 Stable。
目标 Vault 路径：<在这里粘贴你的 Vault 或 Markdown 目录路径>
不要安装任何 Obsidian UI 插件。
不要把 runtime memory 当作长期记忆。
请保留用户内容和历史记录。
请归档已被替代的活跃文件，而不是直接删除。
请更新活跃的 Core、Indexes、运行时适配指南、路由器、治理文件、Frontmatter 规范和 Document Map。
如果 pending proposal 指向已退役文件，请将其标记为 superseded 或改指向当前文件。
请写入更新日志，并执行验证清单。
```

### 文档索引

| 文档 | 说明 |
| --- | --- |
| [更新日志](CHANGELOG.md) | 按项目版本记录 release 历史与重要变更 |
| [架构总览](ARCHITECTURE.md) | AI Agent 阅读细分规范前应先读的单文件架构说明 |
| [Agent Vault Bootstrap Rule](AGENT_VAULT_BOOTSTRAP_RULE.md) | 可复制到 agent 启动规则中的 Vault 入场规则，避免进库后直接全库乱搜 |
| [Frontmatter 规范](FRONTMATTER_STANDARD.md) | 统一元数据字段、YAML 格式、分支映射、注册治理和旧字段迁移规则 |
| [Document Map 规范](DOCUMENT_MAP_STANDARD.md) | 静态 Vault 地图、动态 Obsidian Bases 注册表、阅读顺序和维护规则 |
| [模板自动化指南](TEMPLATE_AUTOMATION_GUIDE.md) | Plain Markdown、Obsidian 官方 Templates 与安全可选的 Templater 配置 |
| [Agent 安装指南](AGENT_INSTALL.md) | AI Agent 可直接执行的 ARMOR Vault 安装说明 |
| [Agent 更新指南](AGENT_UPDATE.md) | AI Agent 可直接执行的既有 Vault 更新与旧活跃文件清理说明 |
| [企业版 README](enterprise/README.md) | 企业版总览、ARMOR 快速开始、权限模型、生命周期规则 |
| [ARMOR V7.2 Stable](enterprise/V7_2_Stable.md) | 企业级完整架构规范 |
| [ARMOR V7.1.5 Governance Patch](enterprise/V7_1_5_Governance_Patch.md) | 已并入 V7.2 的治理层：置信度标签、事实创建门禁、写入质量规则 |
| [ARMOR Prompt Intake Router](enterprise/Prompt_Intake_Router.md) | 用于模糊或高风险 prompt 的第一入口意图路由器 |
| [ARMOR Memory Write Router](enterprise/Memory_Write_Router.md) | 用户明确要求长期记忆时的强制写入路由规则 |
| [ARMOR Root-Cause Fix Protocol](enterprise/Root_Cause_Fix_Protocol.md) | 错误必须在源头层级修复的强制协议 |
| [ARMOR Runtime Memory Policy](enterprise/Runtime_Memory_Policy.md) | 运行时 memory 必须保持低权威和临时性的企业策略 |
| [智能体运行时适配指南](enterprise/agent_runtime_adaptation_guide.md) | 任意可信智能体运行时如何接入 ARMOR |
| [多智能体共享 Vault 治理](enterprise/multi_agent_shared_vault_governance.md) | Hermes、Codex、Claude Code 等多个 agent 如何安全共享一个 ARMOR Vault |
| [ARMOR 项目执行工作流](enterprise/Project_Execution_Workflow.md) | 复杂项目工作的可选低权执行模板 |
| [ARMOR Agent 执行提示词](enterprise/Agent_Project_Execution_Prompt.md) | 配置 agent 使用项目执行模板的可复制提示词 |
| [已归档个人分支](archive/personal/README.md) | PAMA 历史归档；不属于当前活跃安装路径 |
