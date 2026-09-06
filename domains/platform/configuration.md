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

[Wiki home](../../index.md) › [Domains](../index.md) › [Platform](index.md) › Configuration

# Configuration

One lookup for where a given setting lives, so nobody has to grep the codebase for it.

## Layers

<!-- Adjust the "Where" column to this project; keep the three layers. -->

| Layer | Used for | Where |
|---|---|---|
| Environment variables | Infrastructure (DB, mailer, search, URLs) | `.env`, `.env.local`, `env.example` |
| System config (`bin/console system:config:*`) | Merchant-editable settings, per Sales Channel | Administration → Settings → Extensions |
| Feature flags | Toggling unfinished features per environment | `config/packages/` |

## System config keys

<!-- One row per key an extension exposes: `<Extension>.config.<key>`. Link the feature page that uses it. Never put real values or secrets here. -->

| Key | Domain | Default | Notes |
|---|---|---|---|

*No project-specific config keys recorded yet — `config/packages/` only holds `http_discovery.yaml` and `lock.yaml`.*

## Feature flags

<!-- One row per flag; Owner links the domain index. Flags gate everything with status partially-built. -->

| Flag | Default | Owner |
|---|---|---|

*No feature flags recorded yet.*

## Related

- [Environments and deployment](environments-and-deployment.md), [Debugging](debugging.md)

---

*Scope: project-level config only, values are examples, never real secrets · Last synced: 2026-09-06 ·
Verified against Shopware 6.7.13 · Re-sync: diff with `.env`/`.env.local`/`env.example`,
`config/packages/*.yaml`, and each extension's `config.xml` once extensions exist.*
