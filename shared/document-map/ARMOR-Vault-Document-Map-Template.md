---
type: "index"
memory_layer: "indexes"
status: "active"
authority: "reference"
write_policy: "review_required"
created: "YYYY-MM-DD"
updated: "YYYY-MM-DD"
tags:
  - "vault-map"
  - "navigation"
  - "armor"
permission_class: "B"
retrieval_scope: "default"
---

# ARMOR Vault Document Map

Installed architecture:

```text
AI Agent Memory Architecture v1.4.0
ARMOR Enterprise V7.2 Stable
```

> [!important]
> This map is a navigation reference. When it conflicts with an authority file, the authority file wins and this map must be corrected.

## Agent Startup Reading Order

1. `00-Core/Installed-Memory-Architecture.md`
2. `80-Indexes/Vault-Document-Map.md`
3. Relevant routers and policies in `00-Core/`
4. `80-Indexes/Document-Registry.base` or targeted search
5. Underlying authority files

## Core Entry Points

| Need | Current Entry Point |
| --- | --- |
| Installed version | `00-Core/Installed-Memory-Architecture.md` |
| Core document inventory | `00-Core/Core-Document-Index.md` |
| Enterprise architecture | `00-Core/ARMOR-V7.2-Stable.md` |
| Runtime adaptation | `00-Core/Agent-Runtime-Adaptation-Guide.md` |
| Multi-agent governance | `00-Core/Multi-Agent-Shared-Vault-Governance.md` |
| Frontmatter fields | `00-Core/Frontmatter-Standard.md` |
| Field registry | `70-Schemas/Frontmatter-Registry.md` |
| Prompt classification | `00-Core/Prompt-Intake-Router.md` |
| Long-term memory writes | `00-Core/Memory-Write-Router.md` |
| Error correction | `00-Core/Root-Cause-Fix-Protocol.md` |
| Runtime memory boundary | `00-Core/Runtime-Memory-Policy.md` |
| Write permissions | `00-Core/Permission-Policy.md` |
| Retrieval behavior | `00-Core/Retrieval-Rules.md` |
| SSOT routing | `00-Core/Source-of-Truth-Map.md` |

## Layer Map

| Layer | Role | Authority | Default Truth Retrieval |
| --- | --- | --- | --- |
| `00-Core/` | Architecture and governance | Highest | Yes |
| `01-Facts/` | Confirmed current business truth | SSOT | Yes |
| `02-Rules/` | Approved SOPs and standards | Approved | Yes |
| `03-Insights/` | Validated learning | Approved or provisional | Yes when reviewed |
| `04-Research/00-Inbox/` | Raw research | Provisional | No |
| `04-Research/01-Reviewed/` | Reviewed research | Approved | Yes |
| `05-Projects/` | Active project context | Reference | Relevant project only |
| `06-Records/` | Raw evidence | Raw | Evidence mode only |
| `70-Schemas/` | Schemas, templates, registries | Reference | Operational |
| `80-Indexes/` | Navigation maps and registries | Reference | Navigation |
| `81-Dashboards/` | Health and debt views | Reference | Operational |
| `90-Drafts/` | Working drafts | None | No |
| `91-Inbox/` | Unclassified capture | None | No |
| `92-Logs/` | Execution history | None | No |
| `93-Proposals/` | Pending authority changes | None | No |
| `94-Review-Queues/` | Scheduled review work | None | No |
| `99-Archive/` | Historical and superseded memory | Historical | Explicit recall only |

## Task Routing

| Task | Read First | Write Route |
| --- | --- | --- |
| Answer current business fact | Source of Truth Map + relevant `01-Facts/` | Proposal or controlled Fact update |
| Apply an SOP | Relevant `02-Rules/` | Proposal for rule changes |
| Remember something | Prompt Intake Router + Memory Write Router | Correct layer or proposal |
| Fix wrong behavior or fact | Root-Cause Fix Protocol | Fix source or create proposal |
| Research | Retrieval Rules + research schema | Raw inbox, then reviewed promotion |
| Project execution | Relevant project + execution templates | Project-scoped working files |
| Add metadata field | Frontmatter Standard + Registry | Registry proposal or approved extension |
| Coordinate agents | Multi-Agent Governance | Agent-specific namespace |

## Multi-Agent Namespaces

```text
91-Inbox/{agent-name}/
92-Logs/{agent-name}/
93-Proposals/{agent-name}/
93-Proposals/Conflicts/
```

## Dynamic Registry

Open:

```text
80-Indexes/Document-Registry.base
```

Use it to inspect current authority, review candidates, expiration, proposals, layers, and historical files.

## Maintenance

Update this map when architecture entry points, retrieval rules, namespaces, or installed versions change.

Do not update it for every new Fact, Record, Draft, or Log.

## Changelog

| Date | Change | Source | Approved By |
| --- | --- | --- | --- |
| YYYY-MM-DD | Document map installed | AI Agent Memory Architecture v1.4.0 | human |
