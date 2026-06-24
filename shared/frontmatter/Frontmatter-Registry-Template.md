# Frontmatter Field Registry

This file is the installed Vault's registry for frontmatter fields.

Recommended location:

```text
ARMOR: 70-Schemas/Frontmatter-Registry.md
```

Project standard:

```text
00-Core/Frontmatter-Standard.md
```

## Registry Rules

- Canonical fields come from the project Frontmatter Standard.
- Domain fields require a proposal and human approval.
- Tool or skill fields require a registry entry before use.
- Do not create aliases for existing canonical fields.
- Use `snake_case`.
- Prefix extension fields when collision is possible.
- Target 8-16 fields per profile.
- More than 20 fields requires a registered schema justification.

## Canonical Fields

| Field | Layer | Type | Required When | Owner |
| --- | --- | --- | --- | --- |
| `type` | Universal Core | string/enum | Managed Markdown memory file | Architecture |
| `memory_layer` | Universal Core | string/enum | Managed Markdown memory file | Architecture |
| `status` | Universal Core | enum | Managed Markdown memory file | Architecture |
| `authority` | Universal Core | enum | Managed Markdown memory file | Architecture |
| `write_policy` | Universal Core | enum | Managed Markdown memory file | Architecture |
| `created` | Universal Core | ISO date | Managed Markdown memory file | Architecture |
| `updated` | Universal Core | ISO date | Managed Markdown memory file | Architecture |
| `tags` | Universal Core | YAML list | Managed Markdown memory file | Architecture |
| `author_agent` | Agent Attribution | string | Agent-created file | Architecture |
| `confidence` | Agent Attribution | enum | Agent-created knowledge claim | Architecture |
| `source_type` | Conditional Governance | enum/string | Source-backed content | Architecture |
| `source_ref` | Conditional Governance | string/list | Source-backed content | Architecture |
| `permission_class` | Conditional Governance | enum | ARMOR governed file | ARMOR |
| `retrieval_scope` | Conditional Governance | enum | Non-default retrieval behavior | Architecture |
| `review_date` | Conditional Governance | ISO date | Scheduled review | Architecture |
| `expires_at` | Conditional Governance | ISO date | Volatile content | Architecture |
| `sensitivity` | Conditional Governance | enum | Sensitive content | Architecture |
| `owner` | Conditional Governance | string | Owned knowledge | Architecture |
| `approved_by` | Conditional Governance | string | Approved authority | Architecture |

## Domain Profile Registry

Add organization or workflow fields only after approval.

| Profile | Field | Type | Required/Optional | Purpose | Approved By | Approved Date | Schema/Template |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Example | `example_field` | string | optional | Replace this row | human | YYYY-MM-DD |  |

Delete the example row when the first real field is registered.

## Tool And Skill Extension Registry

| Tool/Skill | Field | Type | Purpose | Prefix Used | Registered Date | Files Affected |
| --- | --- | --- | --- | --- | --- | --- |
| Example | `example_tool_field` | string | Replace this row | yes | YYYY-MM-DD |  |

Delete the example row when the first real field is registered.

## Deprecated Field Map

| Deprecated Field | Canonical Replacement | Meaning Check Required | Migration Notes |
| --- | --- | --- | --- |
| `memory_class` | `permission_class` or `memory_layer` | yes | Determine whether the old value means A/B/C/R or a directory layer |
| `created_at` | `created` | no | Preserve date |
| `target_layer` | `memory_layer` | yes | Normalize the value |
| `review_required` | `write_policy` or `review_date` | yes | Convert based on intent |
| `expires` | `expires_at` | no | Preserve date |
| `expired_date` | `expires_at` | no | Preserve date |
| `default_truth_retrieval` | `retrieval_scope` | yes | Normalize boolean or scope |

## Registered File Profiles

| Profile | Required Fields | Optional Fields | Authority Rule | Schema/Template |
| --- | --- | --- | --- | --- |
| ARMOR Core | Universal Core + `permission_class` | `owner`, `approved_by` | `authority: ssot` |  |
| ARMOR Fact | Universal Core + source fields + `permission_class` | review/security fields | Candidate until reviewed |  |
| ARMOR Record | Universal Core + source fields + `permission_class` | `record_type`, `sensitivity` | `authority: raw` |  |
| ARMOR Proposal | Universal Core + proposal fields + `permission_class` | reviewer fields | `authority: none` |  |

## Change Log

| Date | Change | Proposal | Approved By |
| --- | --- | --- | --- |
| YYYY-MM-DD | Registry installed |  | human |
