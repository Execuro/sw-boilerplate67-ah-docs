---
title: Customization guidelines
nav_order: 2
grand_parent: Domains
parent: Platform
type: platform
purpose: How we extend Shopware in this project, so every feature uses the same mechanisms.
scope: Choice of extension type and extension mechanism. Not a Shopware tutorial — links to Shopware docs for mechanics.
last_synced: 2026-09-06
verified_against: Shopware 6.7.13
resync: Review when Shopware deprecates an extension mechanism or an ADR changes a rule here.
tags: [platform, guidelines, extensions]
---

# Customization guidelines

This is the standard Shopware guidance the project follows by default; no project-specific
exceptions are recorded yet (see [Decision records](../../adr/index.md)).

## Extension type

- Prefer an app where it suffices (no server-side code, distributable via the Store).
- Otherwise a plugin (owned, deployed code).
- Reach for a theme only for pure look-and-feel — never for business logic.

## Preferred mechanisms, in order

1. Events and subscribers, over overriding core.
2. Service decoration (abstract class, thin decorator), over overriding core.
3. Entity extensions, over core schema changes.
4. Twig block overrides in the extension, over copying core templates.

## Related

- [Extensions inventory](extensions-inventory.md), [Debugging](debugging.md)
- Shopware docs: plugin fundamentals, decorating services, entity extensions (via ShopwareDevKnowledgeBase MCP).

---

*Scope: choice of extension type and mechanism, not a Shopware tutorial · Last synced: 2026-09-06 ·
Verified against Shopware 6.7.13 · Re-sync: review when Shopware deprecates a mechanism or an ADR
changes a rule here.*
