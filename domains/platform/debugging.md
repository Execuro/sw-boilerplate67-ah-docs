---
title: Debugging
type: platform
purpose: How to observe and debug this project locally, and where to look first for common failures.
scope: Local development. Production incident handling lives in environments-and-deployment.md.
last_synced: 2026-09-06
verified_against: Shopware 6.7.13
resync: Update when the local setup or tooling changes (see baseline/tech-stack.md).
tags: [platform, debugging, profiler, xdebug]
---

# Debugging

**Purpose:** Shorten the "where do I look" step. **Scope:** Local dev. **Last synced:** 2026-09-06 · **Verified against:** Shopware 6.7.13
**How to re-sync:** Re-run each tip on a fresh checkout after upgrades.

## Tools

<!-- Keep the generic Shopware tools; add the project's container/service names and IDE settings. -->

- **Symfony profiler** at `/_profiler` when `APP_ENV=dev`; Store API and Admin API requests appear there too.
- **Xdebug**: _TBD_ (container, `XDEBUG_MODE`, IDE server name).
- **shopware-cli**: `shopware-cli project ci` for the full lint/static-analysis run, `shopware-cli extension validate --full` per extension.
- Logs: see [logging.md](logging.md).

## Common failure lookups

<!-- Add a row whenever a feature page's Gotchas reveal a recurring symptom; link the feature page. -->

| Symptom | Look first |
|---|---|
| Administration module missing after change | `bin/console bundle:dump` + rebuild; check the extension's `main.js` entry and ACL privileges |
| Storefront template change not visible | `bin/console cache:clear`, `theme:compile`; confirm the block lives in the domain extension, not the theme |
| Custom entity not found / 500 on Admin API | migration ran? `bin/console database:migrate --all`; entity definition registered in `services.yaml` |
| Flow not firing | `business_events` log; is the event registered as a business event? |

## Surface tips

- Administration: Vue devtools work on the dev build; the Admin API request log is in the profiler.
- Storefront: `?_profiler` on any page; Twig template names visible via the profiler's Twig panel.

## Related

- [configuration.md](configuration.md), [customization-guidelines.md](customization-guidelines.md)
