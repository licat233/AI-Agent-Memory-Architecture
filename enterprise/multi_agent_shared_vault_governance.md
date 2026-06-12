# Multi-Agent Shared Vault Governance

> Governance policy for multiple trusted agent runtimes operating on one shared ARMOR Enterprise Vault.

Version: 1.0
Status: Stable
Applies To: ARMOR Enterprise V7.2 Stable, Hermes, Claude Code, Codex, Opencode, Cline, OpenHands, MCP-backed agents, custom agents
Depends On: ARMOR V7.2 Stable + Prompt Intake Router + Memory Write Router + Root-Cause Fix Protocol + Runtime Memory Policy + Agent Runtime Adaptation Guide

---

## Purpose

A shared Obsidian Vault can safely serve as long-term memory for multiple agents only when the Vault is governed like a multi-user knowledge database.

This policy prevents agents from overwriting each other, treating low-authority material as truth, duplicating memory, or leaking runtime cache into durable memory.

---

## Core Principle

Multiple agents may share one Vault.

Only the Vault is durable memory and source of truth.

Agents are execution runtimes.

Agent runtime memory is temporary cache only.

All agent writes are low-authority by default unless routed, reviewed, and approved through the ARMOR permission model.

```text
Shared Vault = durable memory / source of truth / audit layer
Agent runtime = capability layer
Runtime memory = temporary cache
```

---

## Primary Risks

Shared Vault deployments must control these risks:

| Risk | Description | Required Control |
| --- | --- | --- |
| Write conflict | Two agents edit the same file at the same time | Namespaced writes, latest-read-before-patch, conflict notes |
| Authority pollution | Drafts, logs, or raw records are treated as current truth | Conservative retrieval and authority labels |
| Duplicate memory | Same fact or rule appears in multiple places | SSOT search before write |
| Semantic drift | One agent writes a temporary observation and another reads it as a rule | Frontmatter and status fields |
| Runtime backflow | Agent session summaries or runtime memory become durable facts | Runtime memory policy and write router |
| Hidden ownership | Future agents cannot tell who wrote a note or why | Required agent metadata |

---

## Agent Namespaces

Agents should not mix temporary work products in shared flat folders.

Recommended namespaced locations:

```text
91-Inbox/
  Codex/
  Hermes/
  Claude-Code/

92-Logs/
  Codex/
  Hermes/
  Claude-Code/

93-Proposals/
  Codex/
  Hermes/
  Claude-Code/
  Conflicts/
```

Additional agents should use stable, human-readable names:

```text
92-Logs/Opencode/
92-Logs/Cline/
92-Logs/OpenHands/
93-Proposals/Custom-Agent-Name/
```

Agent namespaces reduce accidental overwrites and make audit trails easier to review.

---

## High-Authority Write Boundary

Agents must not directly edit these high-authority layers unless the user explicitly approves the exact authority-changing edit:

```text
00-Core/
01-Facts/
02-Rules/
```

Default target for high-authority changes:

```text
93-Proposals/{agent-name}/
```

Human review or explicitly delegated owner review is required before a proposal becomes authoritative memory.

Trusted file access grants capability, not authority.

---

## Required Frontmatter

Every new agent-created Vault file should include frontmatter unless the target file format forbids it.

Recommended minimum:

```yaml
---
author_agent: Codex
created_at: 2026-06-12
source_type: user_request | agent_observation | document | meeting | research | tool_output
source_ref:
confidence: high | medium | low
authority: low | medium | high
status: draft | candidate | proposal | approved | archived
target_layer: 91-Inbox
review_required: false
---
```

For append-only records, also include:

```yaml
record_type: meeting | transcript | customer_feedback | source_evidence | execution_trace
evidence_role: raw_evidence
```

For proposals, also include:

```yaml
proposal_target:
proposal_type: fact_update | rule_update | core_policy_change | architecture_change | conflict_resolution
review_owner:
decision: pending
```

---

## Retrieval Rules

All agents must use conservative retrieval by default.

Default current-truth sources:

```text
00-Core/
01-Facts/
02-Rules/
03-Insights/
04-Research/01-Reviewed/
05-Projects/ relevant active project only
```

Default exclusions:

```text
90-Drafts/
91-Inbox/
92-Logs/
93-Proposals/
94-Review-Queues/
99-Archive/
04-Research/00-Inbox/
06-Records/ unless evidence mode is requested
```

No agent may treat another agent's draft, log, inbox note, proposal, raw record, or runtime cache as authoritative memory.

Records are evidence. They are not current facts by default.

Proposals are pending changes. They are not approved rules by default.

---

## Write Routing

All agents must use the same routing rules:

| User intent | Required route |
| --- | --- |
| Remember this | `00-Core/Memory-Write-Router.md` |
| Fix this / this is wrong | `00-Core/Root-Cause-Fix-Protocol.md` |
| Ambiguous short command | `00-Core/Prompt-Intake-Router.md` |
| Runtime memory question | `00-Core/Runtime-Memory-Policy.md` |

No runtime may use its own memory feature as a shortcut around these routes.

---

## Conflict Policy

Agents should avoid editing the same file concurrently.

Preferred write pattern:

```text
92-Logs/{agent-name}/YYYY-MM-DD-task.md
93-Proposals/{agent-name}/YYYY-MM-DD-topic.md
91-Inbox/{agent-name}/YYYY-MM-DD-candidate.md
```

Before modifying an existing file, the agent must:

1. Read the latest file content.
2. Identify the exact section to patch.
3. Apply the smallest safe patch.
4. Re-check for unexpected changes if the operation spans multiple steps.
5. Stop and create a conflict note if the file changed in a way that may affect the edit.

Conflict note location:

```text
93-Proposals/Conflicts/YYYY-MM-DD-file-conflict.md
```

Conflict note minimum content:

```yaml
---
author_agent: Codex
status: proposal
proposal_type: conflict_resolution
review_required: true
target_file:
conflict_detected_at: 2026-06-12
---
```

```text
Observed conflict:
Expected edit:
Current file state:
Recommended resolution:
```

---

## Agent Role Model

Teams should assign default responsibilities instead of letting every agent behave as a primary authority.

Example role split:

| Agent | Default Role | Default Write Zone |
| --- | --- | --- |
| Hermes | Primary daily memory operator | `91-Inbox/Hermes/`, `92-Logs/Hermes/`, approved operational paths |
| Codex | Architecture, repo, docs, and patch executor | `92-Logs/Codex/`, `93-Proposals/Codex/` |
| Claude Code | Secondary executor and reviewer | `92-Logs/Claude-Code/`, `93-Proposals/Claude-Code/` |
| Human owner | Final authority for Class A changes | Approval and merge into `00-Core/`, `01-Facts/`, `02-Rules/` |

This role model can be adapted, but one rule is fixed:

```text
No agent is automatically the final authority for Class A memory.
```

---

## Review Cadence

Shared Vaults need recurring review.

Recommended cadence:

| Area | Review Action | Frequency |
| --- | --- | --- |
| `91-Inbox/` | Classify, route, or archive | Weekly |
| `90-Drafts/` | Keep, promote, or archive | Weekly or monthly |
| `92-Logs/` | Retain diagnostic logs, archive old logs | Monthly |
| `93-Proposals/` | Approve, reject, merge, or expire | Weekly |
| `06-Records/` | Extract candidate facts through proposal flow | Monthly or project-based |
| `81-Dashboards/` | Update knowledge debt and memory health | Monthly |

Review outputs should be recorded in:

```text
94-Review-Queues/
81-Dashboards/
92-Logs/{review-agent}/
```

---

## Installation Requirements

When installing ARMOR for a multi-agent workspace, create these directories in addition to the standard ARMOR structure:

```text
91-Inbox/Codex/
91-Inbox/Hermes/
91-Inbox/Claude-Code/
92-Logs/Codex/
92-Logs/Hermes/
92-Logs/Claude-Code/
93-Proposals/Codex/
93-Proposals/Hermes/
93-Proposals/Claude-Code/
93-Proposals/Conflicts/
```

These are starter namespaces only. Add or remove agent namespaces according to the actual deployment.

---

## Validation Tests

Run these tests after multi-agent setup:

1. Ask one agent to remember a new high-authority rule.
   - Expected: it creates a proposal, not a direct Class A edit.

2. Ask another agent a current-fact question.
   - Expected: it retrieves approved facts and rules, not the first agent's proposal.

3. Ask two agents to write logs.
   - Expected: each writes to its own `92-Logs/{agent-name}/` namespace.

4. Ask an agent to use a raw record as a fact.
   - Expected: it marks the record as evidence and searches or proposes a current fact update.

5. Simulate a file conflict.
   - Expected: the agent stops and writes a conflict note under `93-Proposals/Conflicts/`.

---

## Final Principle

Shared Vault memory is safe only when low-authority material stays low-authority.

```text
No agent may treat another agent's draft, log, inbox note, proposal, raw record, or runtime cache as authoritative memory.

Only approved Vault layers may serve as current truth.
```
