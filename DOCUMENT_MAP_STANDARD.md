# Document Map Standard

This document defines how an AI Agent Memory Architecture Vault should expose its structure to humans and AI agents.

Current alignment:

```text
AI Agent Memory Architecture v1.4.0
ARMOR Enterprise V7.2 Stable
PAMA Personal V5.3 Stable
```

## 1. Purpose

A Document Map answers:

- What does this Vault contain?
- Where is current truth stored?
- Which documents must an agent read first?
- Which folders are evidence, working material, or history?
- Which file controls a specific behavior?
- Which documents need review or are approaching expiration?
- Which files have been superseded?

Frontmatter describes one file.

The Document Map explains the Vault.

## 2. Two-Layer Model

Every installed Vault should use two complementary map layers.

| Layer | Format | Purpose |
| --- | --- | --- |
| Static Vault Map | Markdown | Stable architecture, entry points, authority boundaries, reading order, task routing |
| Dynamic Document Registry | Obsidian `.base` | Metadata-driven views of current files, review state, expiration, proposals, and ownership |

The static map is curated.

The dynamic registry is generated from file properties.

Neither becomes an authority source merely because it lists authoritative files.

## 3. Installation Locations

Recommended ARMOR locations:

```text
80-Indexes/Vault-Document-Map.md
80-Indexes/Document-Registry.base
```

Recommended PAMA locations:

```text
00-Core/Vault-Document-Map.md
07-Reviews/Document-Registry.base
```

ARMOR places navigation in its dedicated index layer.

PAMA keeps the stable map near Core and the dynamic registry in Reviews so the personal top-level architecture remains unchanged.

## 4. Static Vault Map Requirements

The static map should contain:

1. Installed architecture and version.
2. Map authority disclaimer.
3. Agent startup reading order.
4. Top-level directory map.
5. Current authority entry points.
6. Task-to-document routing.
7. Default retrieval sources and exclusions.
8. Multi-agent namespaces when applicable.
9. Dynamic registry location.
10. Maintenance triggers and changelog.

The map should point to SSOT files rather than duplicate their full contents.

Bad:

```text
Copy every rule and fact into the map.
```

Good:

```text
Product facts -> 01-Facts/Products/
Write policy -> 00-Core/Permission-Policy.md
```

## 5. Map Authority

Use:

```yaml
authority: "reference"
```

A map is navigation, not truth authority.

When a map conflicts with Core policy, a Fact, a Rule, a reviewed PAMA Truth, or another branch SSOT:

```text
The underlying authority file wins.
The map must be corrected.
```

Do not resolve a conflict by treating the map as a replacement authority file.

## 6. Agent Startup Use

An agent entering a Vault should:

1. Read the installed architecture marker.
2. Read the static Vault Map.
3. Read only the Core policies relevant to the task.
4. Use the dynamic registry or targeted search to locate candidate files.
5. Open underlying authority files before answering or writing.

The map reduces discovery cost. It does not remove the need to read the actual source files.

## 7. Dynamic Document Registry

The shared `Document-Registry.base` template uses canonical frontmatter from `FRONTMATTER_STANDARD.md`.

Recommended views:

| View | Purpose |
| --- | --- |
| Current Authority | SSOT and approved files that are not archived or superseded |
| Needs Review | Files marked `needs_review`, `pending`, or `candidate` |
| Expiring | Files with `expires_at` |
| Proposals | Proposals and conflict candidates |
| By Memory Layer | All managed documents grouped by `memory_layer` |
| Historical | Archived, deprecated, expired, or superseded files |

Dynamic views are only as reliable as the frontmatter.

Missing or invalid metadata should become a metadata cleanup item, not a silent assumption.

## 8. Frontmatter For Static Maps

Recommended ARMOR map:

```yaml
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
permission_class: "B"
retrieval_scope: "default"
---
```

Recommended PAMA map:

```yaml
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
retrieval_scope: "default"
---
```

Add `author_agent` and `confidence` when an agent creates or substantially rebuilds the map.

## 9. Maintenance Triggers

Update the static map when:

- project or branch version changes
- a Core entry point is renamed, added, archived, or replaced
- the top-level architecture changes
- a new authority domain is introduced
- default retrieval rules change
- agent namespaces change
- Document Registry location or views change

Do not update the static map for every new business fact, record, draft, or log.

The dynamic registry handles file-level growth.

## 10. Audit Rules

Audit the map after installation and architecture updates.

Check:

- every linked entry point exists
- no retired active file is presented as current
- map version matches installed version
- retrieval exclusions match current policy
- authority labels are references, not duplicated truth
- the `.base` file parses as YAML
- Base properties use canonical frontmatter fields
- historical files are not mixed into current-authority views

## 11. Migration

When an existing Vault has old indexes:

1. Preserve or archive old version-specific indexes.
2. Create the current static Vault Map.
3. Create the dynamic Document Registry.
4. Update active index README files.
5. Do not rewrite historical records merely to populate the registry.
6. Apply frontmatter lazily according to `FRONTMATTER_STANDARD.md`.

Examples of old active indexes:

```text
80-Indexes/V7-1-Index.md
80-Indexes/V7-2-draft-index.md
```

## 12. Final Rule

The map should make the Vault faster to understand without becoming a second source of truth.

```text
Map the authority.
Do not duplicate the authority.
```
