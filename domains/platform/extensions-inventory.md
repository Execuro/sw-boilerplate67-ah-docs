---
title: Extensions inventory
type: platform
purpose: The authoritative list of custom Extensions (plugins, apps, themes) in this project and which domain owns each.
scope: custom/plugins, custom/apps, custom/static-plugins, and vendor-installed store extensions that deliver project features. Not Shopware core.
last_synced: 2026-09-06
verified_against: Shopware 6.7.13
resync: sw-document-feature adds a row when a spec introduces a new extension; verify with `bin/console plugin:list` and `app:list`.
tags: [platform, extensions, inventory]
---

# Extensions inventory

**Purpose:** Know what is installed and who owns it. **Scope:** Project extensions only. **Last synced:** 2026-09-06 · **Verified against:** Shopware 6.7.13
**How to re-sync:** `bin/console plugin:list`, `bin/console app:list`, `ls custom/plugins custom/apps custom/static-plugins` vs this table.

<!-- One row per extension. Type = plugin | app | theme | package (vendor-installed). Path = custom/... or vendor/... Owning domain links the domain index. Delete the _TBD_ row when the first real row exists. -->

| Extension | Type | Path | Owning domain | Depends on | Purpose | Notes |
|---|---|---|---|---|---|---|
| _TBD_ | | | | | | |

## Rules

<!-- Record the project's own naming and ownership rules here, e.g. one plugin per domain group, a shared core plugin for cross-cutting code, technical-name prefix for config keys and log channels. Keep them as rules, not history — history goes to adr/. -->

- Every extension that ships project functionality requires a row here, including vendor-installed ones.
- An extension serving more than one domain records the sharing in the Notes column.
- Cross-cutting code (logging, feature flags, shared traits) goes into the platform-level extension named here, never into a business-domain extension. See [customization-guidelines.md](customization-guidelines.md).
