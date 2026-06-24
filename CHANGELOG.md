# Changelog

All notable changes to AI Agent Memory Architecture are recorded here.

This project uses project-level semantic versions for repository releases. Architecture branch names such as ARMOR Enterprise V7.2 Stable and PAMA Personal V5.3 Stable may remain unchanged across patch releases when the update adds templates, guides, or maintenance documentation without changing the stable architecture boundary.

## Unreleased

### Added

- Added `AGENT_VAULT_BOOTSTRAP_RULE.md`, a copy-ready startup rule that tells agents where to enter installed ARMOR Vaults before broad search.

### Changed

- Linked the bootstrap rule from the README, installation guide, update guide, Document Map Standard, and enterprise runtime adaptation guide.
- Clarified that Document Maps need a durable agent startup instruction to prevent agents from defaulting to broad Vault-wide keyword search.
- Archived PAMA Personal V5.3 Stable under `archive/personal/PAMA-Personal-v5.3-Stable/`.
- Removed PAMA from the active install and update path so the maintained project line is ARMOR Enterprise focused.

## [v1.5.0] - 2026-06-23

### Added

- Added `TEMPLATE_AUTOMATION_GUIDE.md` as the project-level template configuration standard.
- Added canonical ARMOR and PAMA template sets for:
  - Plain Markdown
  - Obsidian Core Templates
  - optional Templater automation
- Added reusable Templater folder-mapping examples for both architecture branches.

### Changed

- Added template-profile installation, update, validation, and agent runtime guidance.
- Standardized generated template frontmatter on `FRONTMATTER_STANDARD.md`.
- Bumped project version from `v1.4.0` to `v1.5.0`.
- Updated architecture overview diagrams to show AI Agent Memory Architecture `v1.5.0`.
- Kept ARMOR Enterprise at `V7.2 Stable` and PAMA Personal at `V5.3 Stable`; the frozen top-level architecture boundaries are unchanged.

### Governance Notes

- Templates aid file creation but never grant truth authority.
- Plain Markdown remains the portable default; Obsidian Core Templates and Templater are optional profiles.
- One active syntax profile should be used per installed template folder.
- Templater system commands, user scripts, and startup templates remain disabled by default.

## [v1.4.0] - 2026-06-23

### Added

- Added `DOCUMENT_MAP_STANDARD.md` as the project-level Vault navigation standard.
- Added ARMOR and PAMA static Vault Document Map templates.
- Added a reusable Obsidian `Document-Registry.base` with views for:
  - current authority
  - files needing review
  - expiring documents
  - proposals and conflicts
  - documents grouped by memory layer
  - historical files

### Changed

- Added Document Map installation and update mappings for ARMOR and PAMA.
- Added map-first discovery guidance to the runtime adaptation guide.
- Added Document Map guidance to the architecture overview and branch READMEs.
- Bumped project version from `v1.3.0` to `v1.4.0`.
- Updated architecture overview diagrams to show AI Agent Memory Architecture `v1.4.0`.
- Kept ARMOR Enterprise at `V7.2 Stable` and PAMA Personal at `V5.3 Stable`; the frozen top-level architecture boundaries are unchanged.

### Governance Notes

- Static maps and dynamic registries are navigation references, not authority sources.
- Agents must open underlying authority files before answering or writing.
- Static maps change when architecture entry points or routing change, not for every new content file.
- Dynamic registry quality depends on canonical frontmatter from `FRONTMATTER_STANDARD.md`.

## [v1.3.0] - 2026-06-23

### Added

- Added `FRONTMATTER_STANDARD.md` as the project-level source of truth for Markdown frontmatter.
- Added a reusable Frontmatter Registry template under `shared/frontmatter/`.
- Added canonical ARMOR and PAMA directory-to-frontmatter mappings.
- Added legacy field migration rules for `memory_class`, `created_at`, `target_layer`, `review_required`, `default_truth_retrieval`, and numeric authority labels.

### Changed

- Unified ARMOR and PAMA frontmatter vocabulary around `memory_layer`, `permission_class`, `authority`, `confidence`, and `write_policy`.
- Updated enterprise and personal multi-agent governance examples to use canonical fields.
- Updated ARMOR and PAMA execution templates to generate compliant frontmatter.
- Added installation and update mappings for the Frontmatter Standard and Registry.
- Bumped project version from `v1.2.4` to `v1.3.0`.
- Updated architecture overview diagrams to show AI Agent Memory Architecture `v1.3.0`.
- Kept ARMOR Enterprise at `V7.2 Stable` and PAMA Personal at `V5.3 Stable`; the frozen top-level architecture boundaries are unchanged.

### Governance Notes

- Frontmatter describes memory but does not grant authority.
- Organization-specific SEO, product-platform, website, and skill fields belong in the installed Vault Registry, not the public core standard.
- New files use canonical fields immediately; existing files migrate lazily when meaningfully updated.
- Logs, records, decisions, and archives should not be mass-rewritten merely to remove legacy field names.

## [v1.2.4] - 2026-06-13

### Added

- Added PAMA Personal Execution Workflow as an optional low-authority execution convention for complex personal tasks, goals, and reviews.
- Added PAMA personal execution templates:
  - `task_plan.md`
  - `findings.md`
  - `progress.md`
  - `closeout.md`
- Added Agent Personal Execution Prompt with copy-ready snippets for Codex, Hermes, Claude Code, and other trusted runtimes.
- Added install and update instructions for copying PAMA execution templates into `08-Working-Memory/Templates/Personal-Execution/`.
- Added README and PAMA README entries for the new personal execution workflow and agent prompt guide.

### Changed

- Bumped project version from `v1.2.3` to `v1.2.4`.
- Updated architecture overview diagrams to show AI Agent Memory Architecture `v1.2.4`.
- Kept ARMOR Enterprise at `V7.2 Stable` and PAMA Personal at `V5.3 Stable`; this release does not change the stable architecture boundary.

### Governance Notes

- PAMA execution files are explicitly low-authority working materials.
- Findings, progress, plans, and closeouts do not become Reality, Decisions, Goals source of truth, Truth, or Core policy by themselves.
- Candidate long-term personal memory must still go through the PAMA Memory Write Router, Root-Cause Fix Protocol, or review gate.
- This release intentionally does not add hooks, automatic plan injection, stop gates, attestation, runtime-specific recovery automation, or new top-level Vault folders.

## [v1.2.3] - 2026-06-13

### Added

- Added ARMOR Project Execution Workflow as an optional low-authority execution convention for complex project tasks.
- Added project execution templates:
  - `task_plan.md`
  - `findings.md`
  - `progress.md`
  - `closeout.md`
- Added Agent Project Execution Prompt with copy-ready snippets for Codex, Hermes, Claude Code, and other trusted runtimes.
- Added install and update instructions for copying project execution templates into `70-Schemas/Project-Execution/`.
- Added README and enterprise README entries for the new workflow and agent prompt guide.

### Changed

- Bumped project version from `v1.2.2` to `v1.2.3`.
- Updated architecture overview diagrams to show AI Agent Memory Architecture `v1.2.3`.
- Kept ARMOR Enterprise at `V7.2 Stable` and PAMA Personal at `V5.3 Stable`; this release does not change the stable architecture boundary.

### Governance Notes

- Project execution files are explicitly low-authority working materials.
- Findings, progress, plans, and closeouts do not become Facts, Rules, or Core policy by themselves.
- Candidate long-term memory must still go through the Memory Write Router, Root-Cause Fix Protocol, or proposal workflow.
- This release intentionally does not add hooks, automatic plan injection, stop gates, attestation, runtime-specific recovery automation, or new top-level Vault folders.

## [v1.2.2] - 2026-06-12

### Changed

- Bumped project version to `v1.2.2`.
- Added the architecture overview for agents.
- Kept ARMOR Enterprise V7.2 Stable and PAMA Personal V5.3 Stable as the active architecture branches.

## [v1.2.1] - 2026-06-12

### Added

- Added the agent update guide for aligning existing Vaults with the latest architecture while preserving user content and history.
- Split architecture overview diagrams into separate assets.

### Changed

- Bumped project version to `v1.2.1`.

## [v1.2.0] - 2026-06-12

### Added

- Added PAMA multi-agent shared vault governance.
- Added multi-agent shared vault governance for trusted runtimes sharing one governed Vault.

### Changed

- Tightened runtime adaptation guidance for shared Vault deployments.
- Bumped project version to `v1.2.0`.

## [v1.1.0] - 2026-06-12

### Added

- Released PAMA V5.2 Stable.
- Added Codex ARMOR runtime integration guidance.

### Changed

- Bumped project version to `v1.1.0`.

## [v1.0.0] - 2026-06-11

### Added

- Added architecture visuals to READMEs.
- Added architecture overview diagram.
- Added agent installation guide.
- Established the initial public project release for AI Agent Memory Architecture.

### Changed

- Simplified default enterprise installation.
- Generalized enterprise runtime support.
- Removed legacy Claudian runtime support from the active architecture.
