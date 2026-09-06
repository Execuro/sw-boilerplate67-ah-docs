---
title: Logging
type: platform
purpose: Which log channels exist, where they go, and how to correlate entries.
scope: Application logs from custom extensions and Shopware. Not infrastructure/container logs.
last_synced: 2026-09-06
verified_against: Shopware 6.7.13
resync: Update when an extension registers a new Monolog channel (config/packages/monolog.yaml).
tags: [platform, logging, observability]
---

[Wiki home](../../index.md) › [Domains](../index.md) › [Platform](index.md) › Logging

# Logging

Which log channel carries what, and where it ends up — so you look in the right file first.

## Channels

<!-- Shopware's own channels first (app, business_events), then one row per project channel. Destination = file path or stream, no hostnames. -->

| Channel | Emitted by | Level (prod) | Destination |
|---|---|---|---|
| `app` | Shopware core | `error` | `var/log/prod.log`, stderr in containers |
| `business_events` | Flow Builder, mail | `info` | `var/log/business_events.log` |

*No project-specific log channel is recorded yet.*

Local (`APP_ENV=dev`): everything at `debug`, also in the Symfony profiler. Log files live under
`var/log/` (currently empty on a fresh checkout).

## Conventions

<!-- Context fields every entry carries (sales_channel_id, order_number…), what must never be logged (customer PII), correlation id handling, which channel a feature must use. -->

*No project-specific logging conventions recorded yet.*

## Related

- [Debugging](debugging.md), [Environments and deployment](environments-and-deployment.md)

---

*Scope: application logs from custom extensions and Shopware, not infrastructure/container logs ·
Last synced: 2026-09-06 · Verified against Shopware 6.7.13 · Re-sync: compare with
`config/packages/monolog.yaml` when an extension registers a new channel.*
