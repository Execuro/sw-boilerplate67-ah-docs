---
title: Platform
type: domain
purpose: Cross-cutting application infrastructure shared by every business domain.
scope: Extensions inventory, customization rules, configuration, logging, debugging, environments. No business features.
last_synced: 2026-09-06
verified_against: Shopware 6.7.13
resync: Review after each Shopware upgrade or infrastructure change; each sub-page has its own resync rule.
tags: [platform, infrastructure, index]
---

# Platform

**Purpose:** Everything a developer needs that is not tied to a single business feature.
**Scope:** Infrastructure and conventions only. **Last synced:** 2026-09-06 · **Verified against:** Shopware 6.7.13
**How to re-sync:** Walk the pages below after upgrades; `sw-document-feature` only touches the extensions inventory and configuration.

Unlike business domains, Platform has no Administration/Storefront split and no feature pages. Anything a merchant or shopper can see belongs to a business domain, not here.

| Page | Answers |
|---|---|
| [extensions-inventory.md](extensions-inventory.md) | Which custom extensions exist and who owns them |
| [customization-guidelines.md](customization-guidelines.md) | How we extend Shopware here (plugin vs app, decoration, events, theme) |
| [configuration.md](configuration.md) | Environment variables, system config keys, feature flags |
| [logging.md](logging.md) | Channels, destinations, levels, correlation |
| [debugging.md](debugging.md) | Profiler, Xdebug, common failure lookups |
| [environments-and-deployment.md](environments-and-deployment.md) | Environments, build, deploy, rollback |

## Related

- [../../baseline/tech-stack.md](../../baseline/tech-stack.md)
- [../../adr/index.md](../../adr/index.md)
