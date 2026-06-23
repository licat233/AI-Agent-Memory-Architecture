# Frontmatter Standard

This document is the project-level source of truth for Markdown frontmatter in AI Agent Memory Architecture.

It applies to:

- ARMOR Enterprise Vaults
- PAMA Personal Vaults
- trusted agent runtimes
- templates, schemas, and organization-specific extensions

Current alignment:

```text
AI Agent Memory Architecture v1.3.0
ARMOR Enterprise V7.2 Stable
PAMA Personal V5.3 Stable
```

## 1. Purpose

Frontmatter makes memory machine-readable without changing the authority of the content.

It supports:

- content classification
- directory and memory-layer validation
- lifecycle management
- conservative retrieval
- source and confidence tracking
- multi-agent attribution
- schema validation
- expiration and review

Frontmatter does not make a file true.

Authority still comes from the architecture, evidence, review state, and human approval.

## 2. Governing Principles

1. Use one canonical field name for one concept.
2. Keep core fields stable across ARMOR and PAMA.
3. Add domain fields only through a registry.
4. Store uncertain information lower instead of inflating metadata.
5. Apply the standard immediately to new files and lazily to old files.
6. Do not mass-edit a Vault without explicit human approval.
7. Preserve historical frontmatter in logs, records, and archives unless it breaks parsing or is actively misleading.

## 3. Field Architecture

Frontmatter uses four layers.

| Layer | Purpose | Governance |
| --- | --- | --- |
| Universal Core | Shared classification and lifecycle fields | Fixed by this standard |
| Conditional Governance | Source, review, security, retrieval, and branch-specific controls | Use when applicable |
| Domain Profile | Organization or workflow fields | Registry entry and human approval |
| Tool or Skill Extension | Narrow implementation-specific fields | Registry entry, prefix, and bounded scope |

Recommended field budget:

```text
Target: 8-16 fields
Soft cap: 20 fields
Over 20: allowed only when a registered schema explains why
```

The cap controls metadata growth. It is not a reason to delete required provenance or security fields.

## 4. Universal Core Fields

All managed Markdown memory files should include these fields unless the file format or generated artifact cannot support frontmatter.

| Field | Type | Purpose |
| --- | --- | --- |
| `type` | enum/string | Content type, such as `fact`, `rule`, `record`, `decision`, or `note` |
| `memory_layer` | enum/string | Logical memory layer that should match the target directory |
| `status` | enum | Lifecycle state |
| `authority` | enum | Truth or knowledge authority, not write permission |
| `write_policy` | enum | Modification policy |
| `created` | ISO date | Creation date; immutable after creation |
| `updated` | ISO date | Date of the latest meaningful content change |
| `tags` | YAML list | Internal Obsidian and agent retrieval tags |

Canonical authority values:

```text
ssot
approved
reference
provisional
raw
none
```

Canonical write policy values:

```text
proposal_required
review_required
append_only
open
read_only
```

Recommended status values:

```text
draft
working
candidate
pending
active
needs_review
approved
complete
deprecated
superseded
expired
archived
```

## 5. Agent-Created File Fields

When an agent creates a file, also include:

| Field | Type | Purpose |
| --- | --- | --- |
| `author_agent` | string | Stable agent name, such as `Hermes`, `Claude-Code`, or `Codex` |
| `confidence` | enum | Agent confidence: `high`, `medium`, or `low` |

`author_agent` identifies the creator. It does not grant authority.

`confidence` describes epistemic confidence. It does not replace evidence or review.

Human-created files may use:

```yaml
author_agent: "human"
```

or omit `author_agent` when local policy permits.

## 6. Conditional Governance Fields

Use these fields only when the content needs them.

| Field | Type | Purpose |
| --- | --- | --- |
| `source_type` | enum/string | Kind of source |
| `source_ref` | string/list | File, URL, record, document, or user confirmation reference |
| `permission_class` | enum | ARMOR write class: `A`, `B`, `C`, or `R` |
| `retrieval_scope` | enum | Default retrieval behavior |
| `review_date` | ISO date | Next scheduled review |
| `expires_at` | ISO date | Date after which volatile content must be reviewed |
| `sensitivity` | enum | Data sensitivity |
| `owner` | string | Human or role responsible for the content |
| `approved_by` | string | Human or delegated reviewer who approved authority |
| `user_confirmed` | boolean | PAMA confirmation signal |

Recommended source types:

```text
user_confirmed
official_document
internal_record
system_observed
research
agent_observation
agent_inference
tool_output
conversation
review
```

Recommended retrieval scopes:

```text
default
project_scoped
review_scoped
evidence_only
historical_only
debug_only
excluded
```

Recommended sensitivity values:

```text
public
internal
confidential
restricted
secret
```

## 7. Canonical Field Semantics

These fields must not be conflated.

### `memory_layer`

Where the memory belongs logically:

```text
facts
rules
records
research
truth
working_memory
```

### `permission_class`

How ARMOR controls writes:

```text
A
B
C
R
```

Do not use `memory_class` for either concept.

### `authority`

How strongly the content may be treated as current knowledge:

```text
ssot
approved
reference
provisional
raw
none
```

Do not use `authority: high | medium | low` for new files.

### `confidence`

How confident the authoring agent is:

```text
high
medium
low
```

Confidence is not authority.

### `write_policy`

How the file may be modified:

```text
proposal_required
review_required
append_only
open
read_only
```

Write policy is not authority.

## 8. YAML Formatting

Use YAML frontmatter at the beginning of the file:

```yaml
---
type: "record"
memory_layer: "records"
status: "active"
authority: "raw"
write_policy: "append_only"
created: "2026-06-23"
updated: "2026-06-23"
tags:
  - "customer-feedback"
  - "evidence"
author_agent: "Codex"
confidence: "high"
---
```

Formatting rules:

- Use double quotes for scalar strings.
- Use `YYYY-MM-DD` for dates and quote them.
- Use YAML lists for arrays such as `tags` and multiple source references.
- Keep booleans and numbers unquoted.
- Use `null` or omit an optional field instead of inventing placeholder text.
- Do not quote template expressions when the template engine requires executable syntax.
- Keep field names in `snake_case`.

Double quotes are a portability convention. Unquoted YAML strings can be valid, but quoting prevents implicit typing and special-character parsing problems.

## 9. ARMOR Directory Defaults

| Directory | Typical `type` | `memory_layer` | `authority` | `write_policy` | `permission_class` |
| --- | --- | --- | --- | --- | --- |
| `00-Core/` | `core` | `core` | `ssot` | `proposal_required` | `A` |
| `01-Facts/` | `fact` | `facts` | `ssot` | `review_required` | `A` |
| `02-Rules/` | `rule` | `rules` | `approved` | `proposal_required` | `A` |
| `03-Insights/` | `insight` | `insights` | `approved` or `provisional` | `review_required` | `B` |
| `04-Research/00-Inbox/` | `research` | `research` | `provisional` | `open` | `C` |
| `04-Research/01-Reviewed/` | `research` | `research` | `approved` | `review_required` | `B` |
| `05-Projects/` | `project` or `note` | `projects` | `reference` | `open` or `review_required` | `B` |
| `06-Records/` | `record` | `records` | `raw` | `append_only` | `R` |
| `90-Drafts/` | `draft` | `drafts` | `none` | `open` | `C` |
| `91-Inbox/` | `note` | `inbox` | `none` | `open` | `C` |
| `92-Logs/` | `log` | `logs` | `none` | `append_only` | `C` |
| `93-Proposals/` | `proposal` | `proposals` | `none` | `open` | `C` |
| `94-Review-Queues/` | `review_item` | `review_queues` | `none` | `open` | `C` |
| `99-Archive/` | preserve original | `archive` | preserve or demote | `read_only` | preserve |

Directory defaults are starting points. A registered schema may narrow them.

## 10. PAMA Directory Defaults

| Directory | Typical `type` | `memory_layer` | `authority` | `write_policy` |
| --- | --- | --- | --- | --- |
| `00-Core/` | `core` | `core` | `ssot` | `proposal_required` |
| `01-Reality/` | `reality` | `reality` | `approved` or `raw` | `review_required` or `append_only` |
| `02-Attention/` | `attention` | `attention` | `reference` | `append_only` |
| `03-Decisions/` | `decision` | `decisions` | `approved` or `reference` | `review_required` |
| `04-Goals/` | `goal` | `goals` | `approved` | `review_required` |
| `05-Truth/` | `truth` | `truth` | `ssot` | `proposal_required` |
| `06-Meta/` | `hypothesis` | `meta` | `provisional` | `open` |
| `07-Reviews/` | `review` | `reviews` | `reference` or `approved` | `review_required` |
| `08-Working-Memory/` | `note` | `working_memory` | `none` or `provisional` | `open` |
| `99-Archive/` | preserve original | `archive` | preserve or demote | `read_only` |

PAMA does not use ARMOR permission classes unless a local hybrid deployment explicitly adopts them.

## 11. File-Type Profiles

### Append-Only Record

Also use:

```yaml
record_type: "meeting"
evidence_role: "raw_evidence"
retrieval_scope: "evidence_only"
sensitivity: "internal"
```

### Proposal

Also use:

```yaml
proposal_target: "01-Facts/Products/example.md"
proposal_type: "fact_update"
review_owner: "human"
decision: "pending"
```

### Volatile Research

Also use:

```yaml
source_type: "research"
source_ref:
  - "https://example.com/source"
review_date: "2026-09-23"
expires_at: "2026-12-23"
retrieval_scope: "default"
```

### PAMA Truth Candidate

Also use:

```yaml
truth_candidate: true
user_confirmed: false
review_gate: "explicit_user_approval"
retrieval_scope: "review_scoped"
```

Truth candidates remain low-authority until approved.

## 12. Registry and Extensions

Every installed Vault should have a frontmatter registry.

Recommended installation:

```text
ARMOR: 70-Schemas/Frontmatter-Registry.md
PAMA:  00-Core/Frontmatter-Registry.md
```

The registry records:

- canonical fields
- branch-specific fields
- domain profiles
- tool or skill extensions
- schemas and templates using each field
- field owner and approval date
- deprecated aliases and migration targets

Domain fields require a proposal and human approval.

Tool or skill fields must:

- be registered
- use a clear prefix when collision is possible
- remain narrowly scoped
- avoid duplicating canonical fields
- keep affected file profiles near the recommended field budget

Organization-specific fields such as website domains, product platform fields, SEO publishing metadata, or internal skill fields belong in the installed Vault registry, not in this public core standard.

## 13. Legacy Field Migration

Use this mapping for new files and meaningful updates.

| Legacy Field | Canonical Field | Migration |
| --- | --- | --- |
| `memory_class` used as A/B/C/R | `permission_class` | Rename |
| `memory_class` used as folder layer | `memory_layer` | Rename after checking meaning |
| `created_at` | `created` | Rename |
| `target_layer` | `memory_layer` | Convert value to canonical layer |
| `review_required` | `write_policy` or `review_date` | Convert based on meaning |
| `authority: high` | `authority: ssot` or `approved` | Decide from source and review state |
| `authority: medium` | `authority: reference` or `provisional` | Decide from evidence |
| `authority: low` | `authority: raw` or `none` | Decide from role |
| `expires` | `expires_at` | Rename |
| `expired_date` | `expires_at` | Rename |
| `default_truth_retrieval: false` | `retrieval_scope: excluded` | Rename and normalize |
| `default_truth_retrieval: project_scoped` | `retrieval_scope: project_scoped` | Rename |
| `source` used as a source category | `source_type` | Rename |
| `source` used as a citation | `source_ref` | Rename |

Migration policy:

1. New files use canonical fields immediately.
2. Significantly updated files migrate relevant legacy fields.
3. Existing untouched files may remain unchanged.
4. Logs, records, and archives are not mass-rewritten merely to remove legacy names.
5. A migration must not change the substantive meaning or authority of a file.

## 14. Validation

Before writing:

- confirm required universal fields
- confirm directory and `memory_layer` agree
- confirm `authority`, `confidence`, and `write_policy` are not conflated
- confirm agent-created files include `author_agent`
- confirm source-backed authority includes `source_type` and `source_ref`
- confirm conditional fields are used only when applicable
- confirm domain and tool fields are registered
- confirm YAML parses
- confirm field count is reasonable

Validation severity:

| File Class | Failure Behavior |
| --- | --- |
| ARMOR Class A or PAMA Core/Truth | Block direct write; create proposal or correction candidate |
| ARMOR Class B or reviewed PAMA memory | Write only as draft/candidate or mark `needs_review` |
| Low-authority working file | Allow write and queue metadata cleanup |
| Append-only evidence | Preserve urgent evidence and mark metadata incomplete |

## 15. Minimal Examples

### ARMOR Fact Candidate

```yaml
---
type: "fact"
memory_layer: "facts"
status: "candidate"
authority: "provisional"
write_policy: "review_required"
created: "2026-06-23"
updated: "2026-06-23"
tags:
  - "product"
author_agent: "Codex"
confidence: "high"
source_type: "official_document"
source_ref: "06-Records/Product-Specifications/source.pdf"
permission_class: "A"
retrieval_scope: "excluded"
---
```

This candidate must not be treated as an approved Fact until reviewed.

### PAMA Working Note

```yaml
---
type: "note"
memory_layer: "working_memory"
status: "working"
authority: "none"
write_policy: "open"
created: "2026-06-23"
updated: "2026-06-23"
tags:
  - "decision-candidate"
author_agent: "Claude-Code"
confidence: "low"
user_confirmed: false
retrieval_scope: "excluded"
---
```

## 16. Final Rule

Frontmatter describes memory.

It does not grant authority.

When metadata and file content disagree, stop and resolve the conflict through the branch governance workflow.
