# Agent Vault Bootstrap Rule

This document defines the runtime startup rule that must be added to AI agents that operate an installed AI Agent Memory Architecture Vault.

The Vault can contain a correct Document Map and retrieval policy, but an agent still needs a startup instruction that tells it where to enter.

## Purpose

The bootstrap rule prevents agents from entering a Vault and immediately performing broad keyword search across drafts, logs, proposals, raw records, raw research, or archive material.

It makes the agent do four things first:

1. Open the installed Vault entry map.
2. Classify the task.
3. Select a retrieval preset.
4. Open authority files before answering or writing.

## Copy-Ready Rule

Add this rule to the agent's durable startup instructions, system prompt, profile rule file, project instruction file, or equivalent runtime configuration.

```text
Agent Vault Bootstrap Rule:

When working with an AI Agent Memory Architecture Vault, do not begin with broad full-Vault keyword search.

First open the installed Vault map:
- ARMOR Enterprise: <vault>/80-Indexes/Vault-Document-Map.md

Then classify the task and select a retrieval preset before searching.

For current-truth questions, use the Source-of-Truth Map and Retrieval Rules to decide where to search.

Open underlying authority files before answering or writing. The Vault Map and Document Registry are navigation references, not authority sources.

Do not treat drafts, inbox notes, logs, proposals, raw records, raw research, or archive files as current truth unless the task explicitly requests evidence, audit, debug, review, or historical context. When those files are used, qualify them as evidence, working material, pending proposal, or historical material.
```

## Minimal Rule

Use this smaller version when the agent has limited instruction space.

```text
Before searching an installed AI Agent Memory Architecture Vault, read the installed Vault Map:
ARMOR: <vault>/80-Indexes/Vault-Document-Map.md

Classify the task, choose a retrieval preset, and open authority files before answering. Do not use drafts, inbox, logs, proposals, raw records, raw research, or archive as current truth by default.
```

## ARMOR Default Entry

For ARMOR Enterprise installs:

```text
<vault>/80-Indexes/Vault-Document-Map.md
<vault>/00-Core/Source-of-Truth-Map.md
<vault>/00-Core/Retrieval-Rules.md
```

Default current-truth retrieval should start from:

```text
00-Core/
01-Facts/
02-Rules/
03-Insights/Learnings/
04-Research/01-Reviewed/
05-Projects/ relevant active project only
80-Indexes/
```

Excluded from default current-truth retrieval:

```text
90-Drafts/
91-Inbox/
92-Logs/
93-Proposals/
94-Review-Queues/
99-Archive/
04-Research/00-Inbox/
06-Records/
```

## Runtime Placement

Install the rule in the durable instruction layer for each agent that can access the Vault.

Examples:

| Runtime | Recommended Location |
| --- | --- |
| Hermes | `SOUL.md`, profile rule, or Hermes startup instruction |
| Claude Code | `CLAUDE.md` or project instruction file |
| Codex | `AGENTS.md`, Codex skill, or local reference file |
| Opencode / Cline / OpenHands | Runtime system prompt, project instruction, or workspace rule file |
| Custom agent | System prompt, tool policy, or memory-provider bootstrap code |

Do not rely on runtime memory alone. Runtime memory is temporary infrastructure, not the durable source of the bootstrap rule.

## Validation

After installation, test the agent with:

| Test Prompt | Expected Behavior |
| --- | --- |
| "What is the current product fact for X?" | Reads the Vault Map, then searches Facts or Source-of-Truth target first. |
| "Find the meeting evidence for X." | Enters evidence mode and qualifies records as evidence. |
| "What rule applies here?" | Searches Rules before logs or proposals. |
| "Why did the agent behave this way?" | Enters debug/audit mode and may inspect logs/proposals/archive with qualification. |
| "Search everything for X." | Clarifies scope or reports that full-Vault search is audit/debug, not default truth retrieval. |

## Relationship To Vault Files

The bootstrap rule points the runtime to the installed Vault entry map.

The installed Vault Map controls local navigation:

```text
ARMOR: 80-Indexes/Vault-Document-Map.md
```

The map then points to the relevant routers, source-of-truth map, retrieval rules, document registry, and underlying authority files.

The map is navigation. The underlying authority file wins.
