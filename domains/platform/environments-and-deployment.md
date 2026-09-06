---
title: Environments and deployment
type: platform
purpose: Which environments exist, how a build reaches them, and how to roll back.
scope: Process and topology. No hostnames or credentials.
last_synced: 2026-09-06
verified_against: Shopware 6.7.13
resync: Update when the CI pipeline or environment list changes.
tags: [platform, deployment, environments]
---

# Environments and deployment

**Purpose:** Know the path from commit to production. **Scope:** Process only. **Last synced:** 2026-09-06 · **Verified against:** Shopware 6.7.13
**How to re-sync:** Compare with the CI configuration (e.g. `.github/workflows/`, `.gitlab-ci.yml`) and `.shopware-project.yml`.

## Environments

<!-- One row per environment. Data = demo / anonymised copy / real. Feature flags = which are on. No URLs. -->

| Environment | Purpose | Data | Feature flags |
|---|---|---|---|
| local | Development | _TBD_ | all on |
| _TBD_ | | | |
| production | Live Sales Channels | Real | released only |

## Deployment flow

<!-- Numbered steps from CI to running: build (shopware-cli project ci / build), artifact, target routine (migrations, plugin:refresh/update, theme:compile, cache warmup), rollback strategy. -->

1. _TBD_

## Rules

- No manual changes on non-local containers.
- Feature flags (see [configuration.md](configuration.md)) gate anything with `status: partially-built`.

## Related

- [../../project/baseline.md](../../project/baseline.md), [logging.md](logging.md)
