---
title: Project baseline
type: project
purpose: The fixed technical baseline every feature is built and verified against.
scope: Versions, runtime, tooling, environment shape. Not per-feature configuration (see domains/platform/configuration.md).
last_synced: 2026-09-06
verified_against: Shopware 6.7.13
resync: Update after any Shopware, PHP, or shopware-cli upgrade; bump verified_against on all pages in the same change.
tags: [baseline, versions]
---

# Project baseline

**Purpose:** Single source for "what are we running" in sw-boilerplate67-ah.
**Scope:** Versions and environment shape only. **Last synced:** 2026-09-06 · **Verified against:** Shopware 6.7.13
**How to re-sync:** Compare with `composer.json`, `composer.lock`, `Dockerfile`/`compose.yaml`, and `.shopware-project.yml`.

<!-- Fill from the repo, never from memory: Shopware = composer.lock shopware/core; PHP = composer.json "require.php" or the Dockerfile image; shopware-cli = `shopware-cli --version`; Node = .nvmrc / package.json engines. Replace _TBD_ cells; do not invent versions. -->

## Versions

| Component | Version | Notes |
|---|---|---|
| Shopware | 6.7.13 | Composer-based project (`shopware/production` template) |
| PHP | _TBD_ | |
| Database | _TBD_ | MySQL / MariaDB, version |
| shopware-cli | _TBD_ | build, static analysis, fixers |
| Node | _TBD_ | Administration and Storefront builds |

## Environment shape

<!-- One bullet per fact: local runtime (docker compose services, ddev, dockware…), where extensions live, where specs and docs live. -->

- Local: _TBD_. See [../domains/platform/environments-and-deployment.md](../domains/platform/environments-and-deployment.md).
- Extensions live in `custom/plugins/`, `custom/apps/`, `custom/static-plugins/`. Inventory: [../domains/platform/extensions-inventory.md](../domains/platform/extensions-inventory.md).
- Specs live in `specs/`; docs in `docs/project-wiki/`.

## Related

- [glossary.md](glossary.md)
- [../domains/platform/index.md](../domains/platform/index.md)
