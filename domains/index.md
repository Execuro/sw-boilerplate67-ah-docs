---
title: Domains
has_children: true
nav_order: 4
type: index
purpose: Map of business domains and their features on each surface.
scope: All domains under docs/project-wiki/domains/. Feature rows are summaries; detail lives on the feature pages.
last_synced: 2026-09-06
verified_against: Shopware 6.7.13
resync: sw-document-feature updates the feature columns; check rows against each domain index.
tags: [index, domains]
---

# Domains

Feature documentation is grouped by business domain. Pick a domain, then the surface the user acts
on — Administration for the merchant, Storefront for the shopper.

<!-- sw-document-feature adds a row when it creates a domain. Only domains that have a directory appear here. -->

| Domain | Purpose | Administration | Storefront |
|---|---|---|---|
| [Checkout](checkout/index.md) | Cart, shipping and payment selection, order placement | — | Cart upsell widget |
| [Platform](platform/index.md) | Cross-cutting infrastructure, extensions, configuration, observability | — | — |

Each feature carries its own status on the domain page it belongs to.

<details>
<summary>The canonical domain list a new domain must come from</summary>

Domains are created on demand from this list — never invent a slug outside it without an ADR
(`area: process`). A domain only appears in the table above once it has a directory here.

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

To add one: create `domains/<slug>/index.md` from the skill's domain-index template, then add a row
above and in the [wiki home](../index.md) domain table.

</details>

---

*Scope: domain level only — feature detail lives on the feature pages. · Last synced: 2026-09-06 ·
Verified against Shopware 6.7.13 · Re-sync: reconcile with each `domains/<domain>/index.md` feature
table.*
