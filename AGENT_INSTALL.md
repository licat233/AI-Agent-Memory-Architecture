# Agent Installation Guide

> Purpose: give this file to an AI agent so it can install AI Agent Memory Architecture into an Obsidian Vault or trusted Markdown directory.
>
> This is an architecture installation, not a software package installation. Do not install Obsidian UI plugins. Do not treat runtime memory, embeddings, SQLite, or indexes as the durable memory source.

---

## 1. Installation Goal

Install one of the supported memory architectures into a user-selected Vault:

| Mode | Architecture | Use Case |
| --- | --- | --- |
| `enterprise` | ARMOR Enterprise AI Workspace | Team, business, product, customer, SOP, research, and project memory |
| `personal` | PAMA Personal AI Memory Architecture | Individual reality tracking, attention audit, decisions, goals, and personal truth |

The installed Vault must preserve the core architecture principles:

- The Vault is the durable source of truth.
- Runtime memory is temporary and low-authority.
- Uncertain information is stored lower.
- Authoritative memory requires evidence, review, and correct routing.
- High-authority changes require proposal or explicit human approval.
- Drafts, inboxes, logs, raw records, proposals, and archives are excluded from default truth retrieval.

---

## 2. Required Questions Before Installing

Before creating or modifying files, ask the user:

1. Which architecture should I install: `personal`, `enterprise`, or `both`?
2. What is the target Vault or Markdown directory path?
3. Is this a new empty Vault or an existing Vault with content?
4. May I create directories and copy architecture documents into the target path?
5. Which agent runtime will operate this Vault, such as Hermes, Claude Code, Codex, Opencode, or another direct-file agent?

If the target path is missing, ask whether to create it.

If the target path already contains memory architecture folders, inspect before changing anything and avoid overwriting user content.

---

## 3. Source Repository Assumptions

The installer should be run from a local checkout of this repository or from a location where these files are available:

```text
README.md
enterprise/
personal/
```

If the repository is not available locally, ask the user to provide the path or clone:

```text
https://github.com/licat233/AI-Agent-Memory-Architecture.git
```

Do not download or install additional tools unless the user explicitly approves.

---

## 4. Enterprise Installation: ARMOR

Use this mode when the user chooses `enterprise`.

### 4.1 Create Top-Level Directories

Create these directories inside the target Vault:

```text
00-Core/
01-Facts/
02-Rules/
03-Insights/
04-Research/
04-Research/00-Inbox/
04-Research/01-Reviewed/
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

Do not rename, merge, or invent top-level layers without explicit user approval.

### 4.2 Copy Core ARMOR Documents

Copy these repository files into the target Vault:

| Source | Destination |
| --- | --- |
| `enterprise/V7_1_Stable.md` | `00-Core/ARMOR-V7.1-Stable.md` |
| `enterprise/V7_1_5_Governance_Patch.md` | `00-Core/ARMOR-Governance-Patch-V7.1.5.md` |
| `enterprise/Prompt_Intake_Router.md` | `00-Core/Prompt-Intake-Router.md` |
| `enterprise/Memory_Write_Router.md` | `00-Core/Memory-Write-Router.md` |
| `enterprise/Root_Cause_Fix_Protocol.md` | `00-Core/Root-Cause-Fix-Protocol.md` |
| `enterprise/Runtime_Memory_Policy.md` | `00-Core/Runtime-Memory-Policy.md` |
| `enterprise/agent_runtime_adaptation_guide.md` | `00-Core/Agent-Runtime-Adaptation-Guide.md` |

If a destination file already exists, do not overwrite it silently. Compare, ask, or write a timestamped candidate under `93-Proposals/` or `90-Drafts/`.

### 4.3 Create Enterprise Starter Files

If missing, create these small placeholder files:

```text
00-Core/Source-of-Truth-Map.md
00-Core/Permission-Policy.md
00-Core/Retrieval-Rules.md
00-Core/Lifecycle-Policy.md
00-Core/Installed-Memory-Architecture.md
```

Each placeholder should state that it must follow ARMOR V7.1 and the governance patch.

---

## 5. Personal Installation: PAMA

Use this mode when the user chooses `personal`.

### 5.1 Create Top-Level Directories

Create these directories inside the target Vault:

```text
00-Core/
01-Reality/
02-Attention/
03-Decisions/
04-Goals/
05-Truth/
05-Truth/Principles/
05-Truth/Knowledge/
05-Truth/Frameworks/
05-Truth/Preferences/
06-Meta/
07-Reviews/
07-Reviews/Weekly/
07-Reviews/Monthly/
07-Reviews/Quarterly/
08-Working-Memory/
08-Working-Memory/Memory-Candidates/
08-Working-Memory/Fix-Candidates/
99-Archive/
```

Do not rename, merge, or invent top-level layers without explicit user approval.

### 5.2 Copy Core PAMA Documents

Copy these repository files into the target Vault:

| Source | Destination |
| --- | --- |
| `personal/PAMA V5.1 Stable.md` | `00-Core/PAMA-V5.1-Stable.md` |
| `personal/PAMA Constitution v1.0.md` | `00-Core/PAMA-Constitution-v1.0.md` |
| `personal/PAMA-Deployment-Spec-v1.0.md.md` | `00-Core/PAMA-Deployment-Spec-v1.0.md` |
| `personal/PAMA_Prompt_Intake_Router.md` | `00-Core/PAMA-Prompt-Intake-Router.md` |
| `personal/PAMA_Memory_Write_Router.md` | `00-Core/PAMA-Memory-Write-Router.md` |
| `personal/PAMA_Root_Cause_Fix_Protocol.md` | `00-Core/PAMA-Root-Cause-Fix-Protocol.md` |
| `personal/PAMA_Runtime_Memory_Policy.md` | `00-Core/PAMA-Runtime-Memory-Policy.md` |

If a destination file already exists, do not overwrite it silently. Compare, ask, or write a timestamped candidate under `08-Working-Memory/Memory-Candidates/`.

### 5.3 Create Personal Starter Files

If missing, create these small placeholder files:

```text
01-Reality/Events.md
01-Reality/Outcomes.md
01-Reality/Metrics.md
02-Attention/Attention-Log.md
03-Decisions/Decision-Records.md
03-Decisions/Lessons.md
04-Goals/Goal-Market.md
06-Meta/Hypotheses.md
00-Core/Installed-Memory-Architecture.md
```

Each placeholder should state that it must follow PAMA V5.1, the PAMA Constitution, and the deployment spec.

---

## 6. Both Mode

If the user chooses `both`, recommend separate Vault roots unless the user has a clear reason to combine them.

Preferred layout:

```text
Memory-Vaults/
  ARMOR-Enterprise/
  PAMA-Personal/
```

Install ARMOR into `ARMOR-Enterprise/` and PAMA into `PAMA-Personal/`.

Do not mix `01-Facts/` and `01-Reality/` in one top-level Vault unless the user explicitly approves a custom combined architecture.

---

## 7. Runtime Integration

After installing files, explain this to the user and the operating agent:

```text
The Vault is long-term memory.
The agent runtime provides capability.
Runtime memory, SQLite, embeddings, and indexes are temporary infrastructure.
They are not authoritative memory.
```

If the runtime is Hermes:

- Point Hermes long-term memory or workspace path to the installed Vault.
- Keep Hermes SQLite or Hindsight memory as runtime cache unless explicitly configured otherwise.
- Use the relevant Prompt Intake Router before ambiguous, high-risk, fix, or remember requests.
- Use the relevant Memory Write Router before storing permanent memory.
- Use the relevant Root-Cause Fix Protocol when correcting errors.
- Use the Runtime Memory Policy to keep runtime memory temporary and low-authority.

---

## 8. Installation Log

Write an installation log after successful installation.

Enterprise destination:

```text
92-Logs/YYYY-MM-DD-Memory-Architecture-Install.md
```

Personal destination:

```text
08-Working-Memory/YYYY-MM-DD-Memory-Architecture-Install.md
```

The log should include:

```yaml
architecture: ARMOR | PAMA
version: V7.1 + V7.1.5 | V5.1
installed_at: YYYY-MM-DD
source_repository: AI-Agent-Memory-Architecture
target_vault: /absolute/path
agent_runtime: Hermes | Claude Code | Codex | Opencode | other
files_created:
files_copied:
existing_files_preserved:
open_questions:
```

---

## 9. Validation Checklist

Before reporting completion, verify:

- The target Vault exists.
- Required top-level directories exist.
- Core architecture documents were copied to `00-Core/`.
- Existing user files were not overwritten silently.
- Runtime memory was not configured as the durable source of truth.
- No Obsidian UI plugin was installed.
- The user knows which path to point their AI agent at.
- The installation log exists.

For ARMOR, also verify:

- `93-Proposals/` exists.
- `06-Records/` exists.
- `90-Drafts/`, `91-Inbox/`, and `92-Logs/` exist.
- `00-Core/Memory-Write-Router.md` exists.

For PAMA, also verify:

- `08-Working-Memory/Memory-Candidates/` exists.
- `07-Reviews/Weekly/`, `Monthly/`, and `Quarterly/` exist.
- `05-Truth/` exists and remains small/empty unless the user explicitly provided reviewed truth.
- `00-Core/PAMA-Memory-Write-Router.md` exists.

---

## 10. Completion Response

After installation, report:

1. Which architecture was installed.
2. Target Vault path.
3. Core documents copied.
4. Important files preserved or skipped.
5. Any user approvals still needed.
6. The next instruction the user's AI agent should follow.

Keep the response concise. Do not claim that memory has been promoted into truth unless the appropriate review or proposal process happened.

---

## 11. Final Rule

Installing the architecture only creates the governed memory system.

It does not make every future note authoritative.

The agent must continue to follow the routers, permission model, retrieval policy, runtime memory policy, and proposal or review workflow every time it reads or writes memory.
