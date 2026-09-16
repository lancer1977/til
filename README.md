# Today I Learned

A portable, flat-file learning journal for durable engineering lessons.

This repository is the canonical source for professional/public TIL content. Notes are plain Markdown with a small stable frontmatter contract so they can be rendered by a website, indexed in Obsidian, syndicated to other platforms, or processed by automation without changing the source format.

## Principles

- Markdown is the source of truth.
- Content is publisher-agnostic.
- Notes remain readable without tooling.
- Publication is an explicit human-approved state change.
- AI may capture, enrich, validate, sanitize, and export notes, but should not silently publish them.
- Private/internal context must never leak through an exporter.
- Generated site output does not belong in this repository.

## Layout

```text
content/
  2026/
    09/
      2026-09-16-git-worktrees-agent-lanes.md
standard/
  TIL-PNS.md
site.yaml
```

## Lifecycle

```text
inbox -> draft -> ready -> published
                 \\-> private
```

A note's `status` field is authoritative for automation.

## Publishing model

```text
This repository
      |
      v
portable Markdown
      |
      +--> static site renderer
      +--> GitHub Pages
      +--> DEV / Hashnode adapters
      +--> RSS / JSON feeds
      +--> future destinations
```

The content repo should stay boring. Rendering, search, themes, and deployment belong in a reusable TIL engine.
