# Template Automation Guide

This guide defines how AI Agent Memory Architecture uses Markdown templates with Obsidian and AI agents.

Current alignment:

```text
AI Agent Memory Architecture v1.5.0
ARMOR Enterprise V7.2 Stable
PAMA Personal V5.3 Stable
```

## 1. Principle

Templates improve consistency. They do not grant authority.

```text
Template = file creation aid
Frontmatter Standard = metadata contract
Router and permission policy = write authority
```

An automatically created Fact, Rule, Truth, or Core note is not automatically approved.

## 2. Three Template Profiles

| Profile | Intended User | Dependency | Automation |
| --- | --- | --- | --- |
| Plain Markdown | AI agents, scripts, any Markdown editor | None | Runtime fills placeholders |
| Obsidian Core Templates | Users who prefer official Obsidian features | Obsidian Templates core plugin | Manual insertion; title/date/time variables |
| Templater | Users who want folder-based automatic templates | Community Templater plugin | Automatic folder or regex templates |

All profiles must generate frontmatter compatible with `FRONTMATTER_STANDARD.md`.

## 3. Repository Locations

```text
shared/templates/
  armor/
    plain/
    obsidian-core/
    templater/
  pama/
    plain/
    obsidian-core/
    templater/
  templater/
    armor-folder-templates.json
    pama-folder-templates.json
```

## 4. Installation Locations

Recommended ARMOR location:

```text
70-Schemas/Templates/
```

Recommended PAMA location:

```text
08-Working-Memory/Templates/Note-Types/
```

Keep only one active syntax profile in an installed template folder. Mixing `{{date}}` and `<% tp.date.now() %>` in the same active template causes unresolved placeholders.

## 5. Plain Markdown

Plain templates use explicit placeholders:

```text
YYYY-MM-DD
Agent-Name
Note-Title
```

AI agents and scripts replace them before writing.

Use Plain Markdown when:

- the Vault may be opened outside Obsidian
- no plugin dependency is desired
- agents create most files directly
- templates are distributed across different runtimes

## 6. Obsidian Core Templates

The official Templates core plugin supports:

```text
{{title}}
{{date}}
{{time}}
{{date:YYYY-MM-DD}}
```

Recommended configuration:

```text
Template folder location: 70-Schemas/Templates
Date format: YYYY-MM-DD
Time format: HH:mm
```

Core Templates are inserted manually through:

```text
Templates: Insert template
```

The core plugin does not provide folder-template rules or arbitrary logic.

## 7. Templater

Templater supports:

```text
<% tp.file.title %>
<% tp.date.now("YYYY-MM-DD") %>
```

It can also trigger templates automatically when new files are created.

Recommended safe settings:

```text
Template folder location: 70-Schemas/Templates
Trigger Templater on new file creation: enabled
Folder Templates: enabled
File Regex Templates: disabled unless needed
System Commands: disabled
User Scripts: disabled unless reviewed
Startup Templates: empty
```

Recommended ARMOR folder rules:

| Folder | Template |
| --- | --- |
| `01-Facts` | `Fact-Template.md` |
| `02-Rules` | `Rule-Template.md` |
| `03-Insights` | `Insight-Template.md` |
| `04-Research` | `Research-Template.md` |
| `06-Records` | `Record-Template.md` |
| `90-Drafts` | `General-Template.md` |
| `91-Inbox` | `General-Template.md` |
| `93-Proposals` | `Proposal-Template.md` |

Recommended PAMA folder rules:

| Folder | Template |
| --- | --- |
| `01-Reality` | `Reality-Template.md` |
| `03-Decisions` | `Decision-Template.md` |
| `04-Goals` | `Goal-Template.md` |
| `05-Truth` | `Truth-Candidate-Template.md` |
| `07-Reviews` | `Review-Template.md` |
| `08-Working-Memory` | `Working-Memory-Template.md` |

Use explicit folder rules instead of a root `/` catch-all. This prevents templates from being applied to schema, attachment, archive, or plugin-managed files unintentionally.

The deepest matching folder rule wins.

## 8. Security

Templater can execute JavaScript and system commands.

Rules:

- never enable system commands by default
- never run templates from untrusted sources
- keep user script and startup template folders empty by default
- review JavaScript before enabling it
- do not let templates edit authority files automatically
- do not use automatic templates as approval gates

## 9. Agent Behavior

AI agents do not need Obsidian or Templater to create files.

When creating a file, an agent should:

1. Identify the target directory.
2. Read the matching active template.
3. Replace variables with literal values.
4. Validate frontmatter.
5. Apply routing and permission rules.
6. Write the file or create a proposal.

Agents must not write unresolved template expressions into normal memory files.

## 10. Maintenance

Update templates when:

- canonical frontmatter fields change
- directory-to-layer mappings change
- a registered schema changes
- a template creates invalid YAML
- installation paths change

Do not place organization-specific SEO, website, MIC, or internal skill fields in public canonical templates. Register and maintain those fields in the installed Vault.

## 11. Validation

Validate:

- YAML parses after rendering
- no unresolved template expressions remain
- generated `memory_layer` matches the folder
- generated authority is conservative
- high-authority templates create candidates, not silent approval
- Templater system commands remain disabled by default

## 12. Final Rule

Use templates to reduce repetitive work.

Do not use templates to bypass governance.
