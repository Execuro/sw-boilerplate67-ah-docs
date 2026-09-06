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

[Wiki home](../../index.md) › [Domains](../index.md) › Platform

# Platform

Everything a developer needs that is not tied to a single business feature. Unlike business
domains, Platform has no Administration/Storefront split and no feature pages — anything a
merchant or shopper can see belongs to a business domain, not here.

| Page | Answers |
|---|---|
| [Extensions inventory](extensions-inventory.md) | Which custom extensions exist and who owns them |
| [Customization guidelines](customization-guidelines.md) | How we extend Shopware here (plugin vs app, decoration, events, theme) |
| [Configuration](configuration.md) | Environment variables, system config keys, feature flags |
| [Logging](logging.md) | Channels, destinations, levels, correlation |
| [Debugging](debugging.md) | Profiler, Xdebug, common failure lookups |
| [Environments and deployment](environments-and-deployment.md) | Environments, build, deploy, rollback |

## Related

- [Tech stack](../../baseline/tech-stack.md)
- [Decision records](../../adr/index.md)

---

*Scope: infrastructure and conventions only, no business features · Last synced: 2026-09-06 ·
Verified against Shopware 6.7.13 · Re-sync: walk the pages below after upgrades; `sw-document-feature`
only touches the extensions inventory and configuration.*
