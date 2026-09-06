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

[Wiki home](../../index.md) › [Domains](../index.md) › [Platform](index.md) › Debugging

# Debugging

Where to look first when something breaks locally, and which tool answers which question.

## Tools

- **Symfony profiler** at `/_profiler` when `APP_ENV=dev`; Store API and Admin API requests appear there too.
- **Adminer** at <http://127.0.0.1:9080> to inspect the database directly.
- **Mailpit** at <http://127.0.0.1:8025> to see mail the application sent.
- **LavinMQ management UI** at <http://127.0.0.1:15672> to inspect the message queue.
- **Logs**: `var/log/` — see [Logging](logging.md).
- **`bin/console`** for any CLI diagnostics (`bundle:dump`, `cache:clear`, `database:migrate`, …).
- **shopware-cli**: `shopware-cli project ci` for the full lint/static-analysis run, `shopware-cli extension validate --full` per extension.
- Xdebug config is not recorded in this project yet; the `docker-dev` web image ships it, but no
  project-specific `XDEBUG_MODE` or IDE server name has been set up.

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

- [Configuration](configuration.md), [Customization guidelines](customization-guidelines.md)

---

*Scope: local development, production incidents live in environments-and-deployment.md ·
Last synced: 2026-09-06 · Verified against Shopware 6.7.13 · Re-sync: re-run each tip on a fresh
checkout after upgrades.*
