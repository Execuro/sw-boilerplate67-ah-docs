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

# Logging

**Purpose:** Find the right log fast. **Scope:** Application-level. **Last synced:** 2026-09-06 · **Verified against:** Shopware 6.7.13
**How to re-sync:** Compare with `config/packages/monolog.yaml`.

## Channels

<!-- Shopware's own channels first (app, business_events), then one row per project channel. Destination = file path or stream, no hostnames. -->

| Channel | Emitted by | Level (prod) | Destination |
|---|---|---|---|
| `app` | Shopware core | `error` | `var/log/prod.log`, stderr in containers |
| `business_events` | Flow Builder, mail | `info` | `var/log/business_events.log` |
| _TBD_ | | | |

Local (`APP_ENV=dev`): everything at `debug`, also in the Symfony profiler.

## Conventions

<!-- Context fields every entry carries (sales_channel_id, order_number…), what must never be logged (customer PII), correlation id handling, which channel a feature must use. -->

- _TBD_

## Related

- [debugging.md](debugging.md), [environments-and-deployment.md](environments-and-deployment.md)
