---
title: Customization guidelines
type: platform
purpose: How we extend Shopware in this project, so every feature uses the same mechanisms.
scope: Choice of extension type and extension mechanism. Not a Shopware tutorial — links to Shopware docs for mechanics.
last_synced: 2026-09-06
verified_against: Shopware 6.7.13
resync: Review when Shopware deprecates an extension mechanism or an ADR changes a rule here.
tags: [platform, guidelines, extensions]
---

# Customization guidelines

**Purpose:** Consistent extension mechanisms across domains. **Scope:** Rules and rationale only. **Last synced:** 2026-09-06 · **Verified against:** Shopware 6.7.13
**How to re-sync:** Cross-check with [../../adr/index.md](../../adr/index.md).

## Plugin vs app vs theme

<!-- State the project's choice and link the ADR that made it (e.g. plugins for owned code, apps for third-party integrations, one theme for look and feel). -->

_TBD_ — record the decision as an ADR with `area: platform` and link it here.

## Preferred mechanisms, in order

<!-- Keep this an ordered list of "reach for X before Y" with one line of rationale each. Typical order: configuration (system config, Rule Builder, Flow Builder) → events/subscribers → service decoration (abstract class, thin decorator) → entity extensions / custom entities → cart processors/collectors → template inheritance in the domain extension (never in the theme) → Administration component override/extend. -->

1. _TBD_

## Never

<!-- Hard prohibitions, e.g. modifying vendor code, copying full core templates, adding columns to core tables by migration, reading $_ENV in services. -->

- _TBD_

## Related

- [extensions-inventory.md](extensions-inventory.md), [debugging.md](debugging.md)
- Shopware docs: plugin fundamentals, decorating services, entity extensions (via ShopwareDevKnowledgeBase MCP).
