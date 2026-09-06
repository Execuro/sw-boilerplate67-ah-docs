---
title: Domain index
type: index
purpose: Map of business domains, their features on each surface, and their status.
scope: All domains under docs/project-wiki/domains/. Feature rows are summaries; detail lives on the feature pages.
last_synced: 2026-09-06
verified_against: Shopware 6.7.13
resync: sw-document-feature updates the feature count/status columns; check rows against each domain index.
tags: [index, domains]
---

# Domain index

**Purpose:** Find the right domain and surface quickly. **Scope:** Domain-level only. **Last synced:** 2026-09-06 · **Verified against:** Shopware 6.7.13
**How to re-sync:** Reconcile with each `domains/<domain>/index.md` feature table.

<!-- sw-document-feature adds a row when it creates a domain. Only domains that have a directory appear here. -->

| Domain | Purpose | Administration features | Storefront features | Status |
|---|---|---|---|---|
| [Checkout](checkout/index.md) | Cart, shipping and payment selection, order placement | — | Cart upsell widget | active |
| [Platform](platform/index.md) | Cross-cutting infrastructure, extensions, configuration, observability | — | — | active |

Domain status values (distinct from feature status, see [CONVENTIONS.md](../CONVENTIONS.md)): `active` (at least one built feature), `planned` (only planned features), `empty` (no features yet).

## Canonical domains

Domains are created on demand from this list — never invent a slug outside it without an ADR (`area: process`). Guidance: `.claude/skills/sw-document-feature/reference/domain-guidelines.md`.

| Slug | Domain | Covers |
|---|---|---|
| `catalogues` | Catalogues | Products, variants, categories, properties, manufacturers, Dynamic product groups, availability |
| `checkout` | Checkout | Cart, shipping and payment selection, order placement |
| `orders` | Orders | Post-checkout order lifecycle, documents, returns, states |
| `customers` | Customers | Accounts, registration, Customer groups, addresses, B2B roles |
| `content` | Content | Shopping Experiences layouts, media, SEO, snippets/translations |
| `marketing` | Marketing | Promotions, newsletters, product reviews, cross-selling |
| `sales-channels` | Sales Channels | Sales Channel setup, domains, languages, currencies, countries, taxes |
| `automation` | Automation | Flow Builder flows, Rule Builder rules, scheduled tasks, mail templates |
| `settings` | Settings | System settings and merchant configuration that no other domain owns |
| `integrations` | Integrations | ERP/PIM/payment/shipping connectors, imports/exports, webhooks |
| `platform` | Platform | Cross-cutting infrastructure (no features, no surfaces) |

## Adding a domain

Create `domains/<slug>/index.md` from `.claude/skills/sw-document-feature/reference/templates/domain-index.md`, add a row here and in [../index.md](../index.md).
