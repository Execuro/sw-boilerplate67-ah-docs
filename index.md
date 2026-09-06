---
title: Project documentation
type: index
purpose: Entry point and wiki index for the sw-boilerplate67-ah documentation.
scope: Everything under docs/project-wiki/. Does not cover Shopware core docs (use the ShopwareDevKnowledgeBase MCP for those).
last_synced: 2026-09-06
verified_against: Shopware 6.7.13
resync: Regenerate the domain map from domains/index.md whenever a domain or feature page is added.
tags: [index, wiki]
---

# Project documentation

**Purpose:** Durable, atomic knowledge about *this* Shopware project — what we built, why, where it lives, and how to operate it.
**Scope:** Project-specific features, decision records (ADRs), and platform infrastructure. Shopware core behaviour is *not* documented here; link to Shopware docs instead.
**Last synced:** 2026-09-06 · **Verified against:** Shopware 6.7.13
**How to re-sync:** Run `sw-document-feature` after each `sw-verify-feature` report; update `last_synced` on touched pages only.

## How to navigate

- New to the project? Start with [baseline/tech-stack.md](baseline/tech-stack.md) and [baseline/glossary.md](baseline/glossary.md).
- Looking for a feature? Go to the [domain index](domains/index.md), pick the domain, then the surface (Administration or Storefront).
- Looking for "why did we do it this way"? See [ADRs](adr/index.md) — technical, process, and significant business decisions in one place.
- Writing or generating a page? Read [CONVENTIONS.md](CONVENTIONS.md) first; page templates live in `.claude/skills/sw-document-feature/reference/templates/`.

## Domain map

<!-- sw-document-feature adds one row per domain when the domain is created. Keep in sync with domains/index.md. -->

| Domain | Purpose |
|---|---|
| [Checkout](domains/checkout/index.md) | Cart, shipping and payment selection, order placement |
| [Platform](domains/platform/index.md) | Cross-cutting infrastructure: extensions inventory, configuration, logging, debugging, environments |

## Sections

- [Overview](README.md) — what this wiki is and how to publish it (GitHub Pages / Jekyll)
- [Conventions](CONVENTIONS.md) — page types, frontmatter schema, surface-isolation rule, status vocabulary
- [Tech stack](baseline/tech-stack.md) — the fixed technical baseline (versions, runtime, tooling)
- [Glossary](baseline/glossary.md) — project terms mapped to Shopware terminology
- [Decision records (ADRs)](adr/index.md) — technical, process, and significant business decisions
- [Domains](domains/index.md) — feature documentation per domain and surface

Templates used by `sw-document-feature` live outside the site in `.claude/skills/sw-document-feature/reference/templates/` (see [Conventions](CONVENTIONS.md)).

## Pipeline context

PRD `specs/NNNN-slug.md` → spec `specs/NNNN-slug-spec.md` → implementation in `custom/plugins/<PluginName>` → `sw-verify-feature` → `sw-document-feature` → pages here.
