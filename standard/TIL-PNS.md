# TIL Portable Note Standard (TIL-PNS) v0.1

A small, portable Markdown convention for capturing learning in Obsidian and publishing it elsewhere later.

## Goals

1. Obsidian can be the authoring workspace.
2. Markdown remains readable without tooling.
3. Frontmatter is stable and publisher-agnostic.
4. Agents may suggest, enrich, validate, and export; publication remains explicit.
5. Private/internal context is separated from publishable content.
6. One note can target multiple destinations without rewriting the lesson.
7. The format remains Git-friendly and easy to lint.

## Required frontmatter

```yaml
---
til_version: "0.1"
id: "2026-09-16-git-worktrees-agent-lanes"
title: "Git worktrees make better agent lanes"
date: 2026-09-16
status: draft
visibility: public
audience:
  - professional
tags:
  - git
  - worktrees
  - agentic-development
summary: "Worktrees let parallel agents operate in isolated branch-backed directories without cloning repositories or colliding in one checkout."
---
```

## Recommended metadata

```yaml
source_type: experiment
confidence: high
ai:
  assisted: true
  disclosure: "AI assisted with research, organization, and editing."
origin:
  kind: conversation
  refs: []
canonical: null
publish:
  lancer1977: true
  devto: false
  hashnode: false
created: 2026-09-16T10:00:00-04:00
updated: 2026-09-16T10:00:00-04:00
```

## Status values

- `inbox` — captured but not shaped
- `draft` — actively developed
- `ready` — approved for export/publication
- `published` — published to at least one destination
- `private` — retained for personal/internal learning only
- `archived` — no longer active

## Canonical body structure

Only `Lesson` is expected for a publishable note. The rest are optional.

```markdown
# Title

## Lesson

The durable idea in plain language.

## Why it matters

Why this is useful or surprising.

## Example

Commands, code, measurements, diagrams, or workflow.

## What changed my mind

Optional prior assumption and what evidence changed it.

## Caveats

Tradeoffs, uncertainty, and environment-specific details.

## Sources

Human-readable references.

## Next experiments

Follow-up questions or measurements.

## Private notes

Anything that must never leave the source workspace. Exporters MUST strip this section.
```

## Automation safety rules

Exporters MUST:

- refuse to publish `inbox`, `draft`, or `private` notes;
- refuse `visibility: private`;
- remove `## Private notes` and its contents;
- preserve the original source note;
- write generated output separately;
- report missing required metadata;
- never silently promote status;
- require explicit publish-target opt-in;
- mark generated files as generated.

## Identity

`id` is permanent and should not change after creation. Recommended form:

```text
YYYY-MM-DD-short-kebab-title
```

The filename may change. The `id` is the durable cross-publisher key.

## Publisher-specific metadata

Publisher-specific fields belong beneath a namespace such as:

```yaml
publish_meta:
  devto:
    series: null
  hashnode:
    publication_id: null
```

Do not add publisher-specific fields at the top level.

## Internal/work learning

For lessons derived from employer or internal work:

1. Capture freely in a private source note.
2. Generalize customer, project, vendor, proprietary, and security-sensitive details.
3. Create a separate public-facing derivative note.
4. Preserve provenance without copying confidential material.
5. Require human review before `status: ready`.

The public note should be a derivative artifact, not a sanitized overwrite of the internal source.
