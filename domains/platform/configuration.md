---
title: Configuration
type: platform
purpose: Where each kind of setting lives and how features expose their configuration.
scope: Environment variables, system config keys, feature flags. Values are examples, never real secrets.
last_synced: 2026-09-06
verified_against: Shopware 6.7.13
resync: sw-document-feature adds rows for new config keys found in a spec; check against each extension's config.xml.
tags: [platform, configuration, feature-flags]
---

# Configuration

**Purpose:** One lookup for "where is that setting". **Scope:** Project-level config only. **Last synced:** 2026-09-06 · **Verified against:** Shopware 6.7.13
**How to re-sync:** Diff with `.env.dist`, `config/packages/*.yaml`, and each `custom/plugins/*/src/Resources/config/config.xml`.

## Layers

<!-- Adjust the "Where" column to this project; keep the three layers. -->

| Layer | Used for | Where |
|---|---|---|
| Environment variables | Infrastructure (DB, mailer, search, URLs) | `.env.local`, container env |
| System config (`bin/console system:config:*`) | Merchant-editable settings, per Sales Channel | Administration → Settings → Extensions |
| Feature flags | Toggling unfinished features per environment | _TBD_ (e.g. `config/packages/<prefix>.yaml`) |

## System config keys

<!-- One row per key an extension exposes: `<Extension>.config.<key>`. Link the feature page that uses it. Never put real values or secrets here. -->

| Key | Domain | Default | Notes |
|---|---|---|---|
| _TBD_ | | | |

## Feature flags

<!-- One row per flag; Owner links the domain index. Flags gate everything with status partially-built. -->

| Flag | Default | Owner |
|---|---|---|
| _TBD_ | | |

## Related

- [environments-and-deployment.md](environments-and-deployment.md), [debugging.md](debugging.md)
