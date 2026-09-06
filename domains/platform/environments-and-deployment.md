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

[Wiki home](../../index.md) › [Domains](../index.md) › [Platform](index.md) › Environments and deployment

# Environments and deployment

Only one environment is recorded for this project so far: `local`, defined in
`.shopware-project.yml` (type docker, PHP 8.5). No staging or production environment is recorded
in the repo yet.

## Local stack

The local stack is Docker Compose, generated and managed by shopware-cli — `compose.yaml` carries
the header *"This file is managed by shopware-cli. Do not edit manually."*, so local changes belong
in a `compose.override.yaml` instead.

| Service | Address | Purpose |
|---|---|---|
| Storefront / Administration | <http://127.0.0.1:8000> | The shop itself |
| Adminer | <http://127.0.0.1:9080> | Database browsing |
| Mailpit | <http://127.0.0.1:8025> | Catches all outgoing mail (SMTP on 1025) |
| LavinMQ | <http://127.0.0.1:15672> | Message queue behind Symfony Messenger (AMQP on 5672) |
| Vite | ports 5173 / 5773 | Administration and Storefront watchers |

Component versions (PHP, Node, Database, Shopware) live on
[Tech stack](../../baseline/tech-stack.md) — not repeated here.

## Deployment flow

No deployment pipeline is recorded in this repo yet.

## Rules

- No manual changes on non-local containers.
- Feature flags (see [Configuration](configuration.md)) gate anything with `status: partially-built`.

## Related

- [Tech stack](../../baseline/tech-stack.md), [Logging](logging.md)

---

*Scope: process and topology, no hostnames or credentials · Last synced: 2026-09-06 · Verified
against Shopware 6.7.13 · Re-sync: update when a CI pipeline or a new environment is added to
`.shopware-project.yml`.*
