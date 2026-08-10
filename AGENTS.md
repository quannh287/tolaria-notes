---
type: Note
_organized: true
_archived: true
---
# AGENTS.md — Tolaria Vault

This is a [Tolaria](https://github.com/refactoringhq/tolaria) vault: a folder of Markdown files with YAML frontmatter forming a personal knowledge graph.

Keep edits compatible with Tolaria's current conventions. Prefer small, human-readable changes over heavy restructuring.

## Core conventions

- One Markdown note per file.
- The first H1 in the body is the preferred display title.
- Legacy `title:` frontmatter is still read as a fallback when a note has no H1. Do not add it to new notes unless you are maintaining an older file.
- Store note type in the `type:` frontmatter field.
- Most notes live at the vault root as flat `.md` files. Type definitions are also flat `.md` files at the vault root (e.g. `project.md`, `person.md`). Saved views live in `views/`.
- Any frontmatter field containing [[wikilinks]] is treated as a relationship. Common names include `Belongs to:`, `Related to:`, `Workspace:`, and custom relationship names.
- Frontmatter properties that start with `_` are usually Tolaria-managed state. Leave them alone unless the user explicitly asks for them to change.

## Notes

```yaml
---
type: Project
status: Active
icon: target
Workspace: "[[tolaria]]"
Belongs to:
  - "[[25q2]]"
Related to:
  - "[[person-luca-rossi]]"
aliases:
  - Tolaria work
url: https://example.com
---

# Ship Tolaria

Body content in Markdown.
```

## Types

Type definitions are regular notes stored flat at the vault root (e.g. `project.md`, `person.md`). Use `type: Type` for new ones:

```yaml
---
type: Type
icon: shapes
color: blue
sidebar label: Projects
template: |
  ## Outcome

  ## Next actions
---

# Project
```

Useful type metadata includes `icon`, `color`, `order`, `sidebar label`, `template`, `sort`, `view`, and `visible`.

## Wikilinks

- [[filename]] or [[Note Title]] — link by filename or title
- [[filename|display text]] — with custom display text
- Works in frontmatter values and Markdown body

## Views

Saved views live in `views/*.yml` and are written as YAML:

```yaml
name: Active Projects
icon: kanban
color: blue
sort: modified:desc
filters:
  all:
    - field: type
      op: equals
      value: Project
    - field: status
      op: equals
      value: Active
```

## Filenames

Use kebab-case: `my-note-title.md`. One note per file.

## Work Management System

Vault sử dụng Sprint workflow hàng tuần với 3 loại note chính:

### Task
```yaml
---
type: Task
status: Todo          # Todo | In Progress | Blocked | Clarify | Done
priority: High        # High | Medium | Low
project: kai-go       # kai-go | gal-gcc | digital-library
sprint: "[[sprint-2026-w27]]"
estimate: "4h"
Belongs to:
  - "[[kai-go]]"
---
# Tên task
```

### Sprint
```yaml
---
type: Sprint
status: Active
week: "2026-W27"
start date: 2026-06-30
end date: 2026-07-04
color: "#f59e0b"
Belongs to:
  - "[[2026-q3]]"
---
# Sprint 2026-W27
```
- Sprint notes dùng `_display: sheet` để hiện dạng spreadsheet planning board.
- Filename convention: `sprint-YYYY-www.md` (e.g. `sprint-2026-w28.md`).

### Daily Log
```yaml
---
type: Daily Log
Belongs to:
  - "[[sprint-2026-w27]]"
---
# 2026-06-30 Daily
```
- Filename convention: `YYYY-MM-DD-daily.md`.
- Template: `## Done today`, `## Blocked / Clarify`, `## Tomorrow`.

### Projects (Work context)
```yaml
---
type: Project
status: In progress
context: Work
capacity: 50%         # % thời gian dành cho project này
color: "#3b82f6"
Belongs to:
  - "[[2026-q3]]"
---
```
Projects hiện tại: `kai-go` (50%), `gal-gcc` (40%), `digital-library` (10%).

## What agents should do

- Create and edit notes using the frontmatter and H1 conventions above.
- Create type definition notes at the vault root (e.g. `my-type.md`) with `type: Type` frontmatter.
- Add or modify relationships without breaking existing wikilinks.
- Create and edit saved views in `views/`.
- Update `AGENTS.md` only when the user asks for vault-level guidance changes.

## What agents should avoid

- Do not create a `type/` subdirectory — type definitions live flat at the vault root alongside regular notes.
- Do not silently overwrite an existing custom `AGENTS.md`.
- Do not overwrite user-authored config or installation-specific app files unless the user explicitly asks.
