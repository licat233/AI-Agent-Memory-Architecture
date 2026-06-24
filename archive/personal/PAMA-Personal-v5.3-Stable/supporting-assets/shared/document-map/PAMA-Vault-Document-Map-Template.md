---
type: "index"
memory_layer: "core"
status: "active"
authority: "reference"
write_policy: "review_required"
created: "YYYY-MM-DD"
updated: "YYYY-MM-DD"
tags:
  - "vault-map"
  - "navigation"
  - "pama"
retrieval_scope: "default"
---

# PAMA Vault Document Map

Installed architecture:

```text
AI Agent Memory Architecture v1.5.0
PAMA Personal V5.3 Stable
```

> [!important]
> This map is a navigation reference. User sovereignty, the PAMA Constitution, and underlying authority files take precedence.

## Agent Startup Reading Order

1. `00-Core/Vault-Document-Map.md`
2. PAMA Constitution and Stable Architecture
3. Relevant routers and runtime policy
4. `07-Reviews/Document-Registry.base` or targeted search
5. Underlying Reality, Decision, Goal, Truth, or Review files

## Core Entry Points

| Need | Current Entry Point |
| --- | --- |
| Constitution | `00-Core/PAMA Constitution v1.0.md` |
| Stable architecture | `00-Core/PAMA V5.3 Stable.md` |
| Deployment rules | `00-Core/PAMA-Deployment-Spec-v1.0.md` |
| Frontmatter fields | `00-Core/Frontmatter-Standard.md` |
| Field registry | `00-Core/Frontmatter-Registry.md` |
| Prompt classification | `00-Core/PAMA-Prompt-Intake-Router.md` |
| Long-term memory writes | `00-Core/PAMA-Memory-Write-Router.md` |
| Error correction | `00-Core/PAMA-Root-Cause-Fix-Protocol.md` |
| Runtime memory boundary | `00-Core/PAMA-Runtime-Memory-Policy.md` |
| Multi-agent governance | `00-Core/PAMA-Multi-Agent-Shared-Vault-Governance.md` |

## Layer Map

| Layer | Role | Authority | Default Retrieval |
| --- | --- | --- | --- |
| `00-Core/` | Constitution and governance | Highest | Yes |
| `01-Reality/` | Evidence-backed events and outcomes | Raw or approved | Yes |
| `02-Attention/` | Time and energy audit | Reference | Review contexts |
| `03-Decisions/` | Decisions and feedback | Approved or reference | Yes |
| `04-Goals/` | Direction and active goals | Approved | Yes |
| `05-Truth/` | Durable verified personal truth | SSOT | Highest |
| `06-Meta/` | Hypotheses and interpretation | Provisional | No by default |
| `07-Reviews/` | Promotion and alignment reviews | Reference or approved | Review contexts |
| `08-Working-Memory/` | Temporary and uncertain context | None or provisional | Current task only |
| `99-Archive/` | Historical and invalidated memory | Historical | Explicit recall only |

## Task Routing

| Task | Read First | Write Route |
| --- | --- | --- |
| What objectively happened? | Relevant `01-Reality/` | Append evidence or create review candidate |
| Review a decision | `03-Decisions/` + relevant Reality | Decision feedback or Review |
| Review priorities | `02-Attention/` + `04-Goals/` | Review, not immediate Truth |
| Remember something | PAMA Prompt Intake + Memory Write Router | Working Memory or review candidate |
| Fix wrong behavior or memory | PAMA Root-Cause Fix Protocol | Fix source or create candidate |
| Promote durable truth | Constitution + Reviews + evidence | User-approved `05-Truth/` update |
| Add metadata field | Frontmatter Standard + Registry | Registered extension |
| Coordinate agents | PAMA Multi-Agent Governance | Agent-specific working namespace |

## Multi-Agent Namespaces

```text
08-Working-Memory/{agent-name}/
08-Working-Memory/Memory-Candidates/{agent-name}/
08-Working-Memory/Fix-Candidates/{agent-name}/
08-Working-Memory/Logs/{agent-name}/
07-Reviews/{agent-name}/
07-Reviews/Conflict-Reviews/
```

## Dynamic Registry

Open:

```text
07-Reviews/Document-Registry.base
```

Use it to inspect current authority, review candidates, expiration, memory layers, and historical files.

## Maintenance

Update this map when Core entry points, layer meanings, review gates, agent namespaces, or installed versions change.

Do not update it for every new Reality event, working note, or review.

## Changelog

| Date | Change | Source | Approved By |
| --- | --- | --- | --- |
| YYYY-MM-DD | Document map installed | AI Agent Memory Architecture v1.5.0 | user |
