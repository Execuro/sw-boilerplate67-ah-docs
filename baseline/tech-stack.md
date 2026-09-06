---
title: Tech stack
nav_order: 2
type: project
purpose: The fixed technical baseline every feature is built and verified against.
scope: Versions, runtime, tooling, environment shape. Not per-feature configuration (see domains/platform/configuration.md).
last_synced: 2026-09-06
verified_against: Shopware 6.7.13
resync: Update after any Shopware, PHP, or shopware-cli upgrade; bump verified_against on all pages in the same change.
tags: [baseline, versions]
---

# Tech stack

What this project runs on. Every feature page is verified against the versions below, so when one
of them changes, the pages that were verified against the old one become visibly stale.

<!-- Fill from the repo, never from memory: Shopware = composer.lock shopware/core; PHP and Node = the docker-dev image tag in compose.yaml; Database = the database service image; shopware-cli = `shopware-cli --version`. -->

## Versions

| Component | Version | Where it comes from |
|---|---|---|
| Shopware | 6.7.13.0 | `composer.json` / `composer.lock` (`shopware/core`) |
| PHP | 8.5 | `compose.yaml` web image, `.shopware-project.yml` (`docker.php.version`) |
| Database | MariaDB 11.8 | `compose.yaml` (`database` service) |
| Node | 24 | `compose.yaml` web image tag (`php8.5-node24-caddy`) |
| shopware-cli | 0.16.10 | `shopware-cli --version` — builds, fixers, static analysis |

The project is Composer-based, built from the `shopware/production` template.

## Local environment

The local stack is Docker Compose, generated and managed by shopware-cli — `compose.yaml` carries
the header *"This file is managed by shopware-cli. Do not edit manually."*, so local changes belong
in a `compose.override.yaml` instead.

| Service | Address | What it is for |
|---|---|---|
| Storefront / Administration | <http://127.0.0.1:8000> | The shop itself; local Administration credentials are in `.shopware-project.yml` |
| Adminer | <http://127.0.0.1:9080> | Database browsing |
| Mailpit | <http://127.0.0.1:8025> | Catches all outgoing mail (SMTP on 1025) |
| LavinMQ | <http://127.0.0.1:15672> | Message queue behind Symfony Messenger (AMQP on 5672) |
| Vite | ports 5173 / 5773 | Administration and Storefront watchers |

More detail, and what the non-local environments look like:
[Environments and deployment](../domains/platform/environments-and-deployment.md).

## Where things live

- Extensions: `custom/plugins/`, `custom/apps/`, `custom/static-plugins/` — see the
  [extensions inventory](../domains/platform/extensions-inventory.md).
- Specs and PRDs: `specs/`. This wiki: `docs/project-wiki/`.
- Build and watch scripts: `bin/` (`build-storefront.sh`, `watch-administration.sh`, …).

## Related

- [Glossary](glossary.md)
- [Platform](../domains/platform/index.md)

---

*Scope: versions and environment shape only. · Last synced: 2026-09-06 · Verified against Shopware
6.7.13 · Re-sync: compare with `composer.json`, `composer.lock`, `compose.yaml` and
`.shopware-project.yml` after any upgrade.*
