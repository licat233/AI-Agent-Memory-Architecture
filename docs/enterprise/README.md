<p align="center">
  <h1 align="center">AI Agent Memory Architecture</h1>
  <p align="center"><strong>Long-term, auditable memory architectures for AI agents</strong></p>
</p>

---

## Overview

This repository provides structured memory architectures for AI agent workspaces. Instead of relying on vector stores or ad-hoc file storage, these architectures give AI agents a governed, permission-controlled, lifecycle-managed knowledge system built on Obsidian Vault.

**Current release: Enterprise AI Agent Memory Architecture (V7.1.5)**

| Architecture | Status | Use Case |
|---|---|---|
| [Enterprise](#enterprise-architecture) | ✅ Stable (V7.1.5) | Multi-person teams, business operations, brand/product/customer knowledge management |
| Personal | 🔜 Planned | Individual use, personal knowledge, lightweight governance |

---

## Enterprise Architecture

**Version:** V7.1 Stable + V7.1.5 Governance Patch

A production-grade memory architecture designed for enterprise AI agents managing business-critical knowledge: brand facts, product specifications, customer profiles, operational SOPs, and team workflows.

### Who It's For

- Teams deploying AI agents for business operations
- Organizations needing auditable, source-backed AI memory
- Multi-agent workspaces where knowledge consistency matters
- Use cases requiring human approval for high-authority changes

### Who It's NOT For

- Individual users with personal AI assistants
- Simple chatbot memory (use vector stores instead)
- Scenarios where all knowledge has equal authority
- Use cases that don't need audit trails or governance

### Core Principles

| Principle | Meaning |
|---|---|
| **SSOT** (Single Source of Truth) | Every piece of knowledge has exactly one authoritative location. No parallel truths. |
| **Capture ≠ Authority** | Agents can write freely into low-risk areas, but that doesn't make it true. |
| **Capability ≠ Permission** | The runtime *can* write files, but the protocol decides whether it *may*. |
| **Write ≠ Truth** (V7.1.5) | Write permission does not equal truth authority. Confidence must be validated. |
| **Conservative Retrieval** | Default search excludes drafts, logs, raw research, archive, and unreviewed records. |
| **Low-Maintenance** | Automatic lifecycle rules handle drafts, stale research, and inactive projects. |

### System Architecture

```text
┌─────────────────────────────────────────────────────┐
│                   Human Owner                        │
│              (final authority for                    │
│               high-risk changes)                     │
└──────────────────────┬──────────────────────────────┘
                       │ approves proposals
┌──────────────────────▼──────────────────────────────┐
│                   AI Agent                           │
│         (primary agent / operating protocol)         │
│  retrieve · classify · summarize · propose · write   │
└──────────────────────┬──────────────────────────────┘
                       │ operates within
┌──────────────────────▼──────────────────────────────┐
│               Agent Runtime                          │
│           (Obsidian / file system)                   │
│    file I/O · search · skills · bash · MCP          │
└──────────────────────┬──────────────────────────────┘
                       │ reads/writes
┌──────────────────────▼──────────────────────────────┐
│                 Obsidian Vault                       │
│          (knowledge operating system)                │
│   storage · governance · graph · audit · review      │
└─────────────────────────────────────────────────────┘
```

### Two Operating Tracks

```text
┌─────────────────────────────┐    ┌─────────────────────────────┐
│       CAPTURE TRACK         │    │       AUTHORITY TRACK        │
│                             │    │                              │
│  90-Drafts                  │    │  00-Core                     │
│  91-Inbox                   │    │  01-Facts                    │
│  92-Logs                    │    │  02-Rules                    │
│  93-Proposals               │    │  03-Insights/Learnings       │
│  94-Review-Queues           │    │  04-Research/01-Reviewed     │
│  04-Research/00-Inbox       │    │                              │
│  05-Projects                │    │  Properties:                 │
│  06-Records                 │    │  • Small and stable          │
│                             │    │  • Source-backed             │
│  Properties:                │    │  • Reviewed where needed     │
│  • Fast write               │    │  • Default retrieval         │
│  • Low authority            │    │  • Protected by permissions  │
│  • Not current truth        │    │  • Modified slowly           │
│  • Auto-expires             │    │                              │
│  • May promote later        │    │                              │
└─────────────────────────────┘    └─────────────────────────────┘
         write freely                      change carefully
```

### Permission Model (V7.1)

| Class | Includes | Direct Write | Proposal Required |
|---|---|:---:|:---:|
| **A** | Core, Facts, Rules | No | Yes + Human Approval |
| **B** | Insights, Research, Projects | Create/Append OK | For state changes |
| **C** | Drafts, Inbox, Logs | Yes | No |
| **R** | Records, Evidence | Append only | No |

### V7.1.5 Governance Layer

The governance patch adds quality gates before writing:

**Source-Based Confidence Labels:**

| Label | Sources | Can Write To |
|---|---|---|
| **High** | User confirmed, official docs, verified specs | Class A (with controls), B, C, R |
| **Medium** | Multiple references, research summary | Class B, C, R (NOT Class A directly) |
| **Low** | AI inference, assumptions, weak sources | Class C only |
| **No Memory** | Guesses, temporary, irrelevant | Do NOT store |

**Fact Creation Gate:**

```text
Before creating/updating 01-Facts/:
  → Search existing authoritative memory
  → If exists: update
  → If conflict: create Proposal
  → If new + High confidence: create
  → If new + Medium/Low: store in Insights/Research instead
```

### Vault Structure

```text
Vault/
│
├── 00-Core/                  # System constitution & principles
├── 01-Facts/                 # Confirmed truth (brand, products, customers)
├── 02-Rules/                 # Execution standards (SOPs, guidelines)
├── 03-Insights/              # Validated experience (cases, learnings)
├── 04-Research/              # External knowledge (market, competitor)
│   ├── 00-Inbox/             #   Raw, unreviewed research
│   └── 01-Reviewed/          #   Promoted, source-backed research
├── 05-Projects/              # Active project materials
├── 06-Records/               # Raw evidence (meetings, emails, transcripts)
│
├── 70-Schemas/               # Validation rules & templates
├── 80-Indexes/               # Cross-layer indexes
├── 81-Dashboards/            # Knowledge debt & evaluation dashboards
│
├── 90-Drafts/                # Unapproved working material
├── 91-Inbox/                 # Unclassified incoming content
├── 92-Logs/                  # Agent execution logs
├── 93-Proposals/             # Pending changes awaiting review
├── 94-Review-Queues/         # Scheduled review items
│
└── 99-Archive/               # Historical / deprecated material
```

The top-level structure is **frozen**. Domain-specific subfolders and content within layers are fully extensible.

### Lifecycle & Automation

Knowledge decays automatically:

| Content | Stale After | Archive After |
|---|---|---|
| Drafts | 30 days unused | 180 days unused |
| Inbox | 14 days unclassified | 30 days unresolved |
| Volatile Research | 30 days | 120 days total |
| Normal Research | 90 days | 180 days total |
| Inactive Projects | 30 days | 180 days |
| Logs | 30 days diagnostic value | 90 days |
| Pending Proposals | 30-day reminder | 90 days auto-expire |

---

## Documentation

### Enterprise Architecture Docs

| Document | Description |
|---|---|
| [V7.1 Stable (Full Spec)](docs/enterprise/V7_1_Stable.md) | Complete architecture specification |
| [V7.1.5 Governance Patch](docs/enterprise/V7_1_5_Governance_Patch.md) | Write quality gates, confidence labels, fact creation gate |
| [Hermes Adaptation Guide](docs/enterprise/hermes_adaptation_guide.md) | Step-by-step guide for adapting Hermes agent |

### Version History

| Version | Key Additions |
|---|---|
| V4 | Foundation: SSOT, memory layers, basic vault structure |
| V5 | Knowledge triage, promotion framework, conflict resolution, permission model |
| V6 | Runtime model, proposals layer, retrieval filter presets |
| V7 | Runtime retrieval, context packing, schema validation, security policy |
| V7.1 Stable | Architecture stability, Capture/Authority tracks, automatic lifecycle |
| V7.1.5 | Governance patch: confidence labels, fact creation gate, expiration rules |

---

## Quick Start (Enterprise)

1. **Create the vault structure** using the frozen top-level layout above.
2. **Set up Core files**: `Core-Memory.md`, `Hermes-Operating-Protocol.md`, `Source-of-Truth-Map.md`, `Permission-Policy.md`, `Retrieval-Rules.md`, `Governance-Patch-V715.md`.
3. **Configure your AI agent** following the [Adaptation Guide](docs/enterprise/hermes_adaptation_guide.md) — point long-term memory to the Vault, set SQLite to runtime-only.
4. **Create templates** for Records, Proposals, Rules, and Research in `70-Schemas/Templates/`.
5. **Start capturing** — meeting notes go to Records, research goes to Research/Inbox, ideas go to Drafts.
6. **Review by exception** — only proposals affecting current truth, rules, or customer state need human approval.

---

## Design Philosophy

> The workspace does not optimize for remembering everything.
> It optimizes for preserving only governed, source-backed, reviewable, and useful memory.

- AI may **generate, classify, summarize, capture, archive, and propose**.
- AI may **not** silently convert uncertain information into facts, rules, or core memory.
- Truth is defined by SSOT files.
- Evidence is preserved in Records.
- Authority is controlled by the Permission Model.
- Retrieval is conservative by default.
- Unreviewed memory expires, degrades, or archives automatically.
- Only changes that affect current truth or future behavior require human approval.

---

## Roadmap

- [x] Enterprise AI Agent Memory Architecture (V7.1.5)
- [ ] Personal AI Agent Memory Architecture (lightweight, single-user)
- [ ] Migration guide: Enterprise → Personal
- [ ] Integration examples for popular AI frameworks

---

## License

This project is released as an open architecture. Use it, adapt it, and build on it for your own AI workspace.
