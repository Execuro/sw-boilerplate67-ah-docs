---
title: Glossary
type: project
purpose: Map project-specific words to Shopware's official terminology.
scope: Terms used in PRDs, specs, and docs. Not a Shopware glossary.
last_synced: 2026-09-06
verified_against: Shopware 6.7.13
resync: Add a row whenever a PRD introduces a new project term.
tags: [glossary, terminology]
---

[Wiki home](../index.md) › Glossary

# Glossary

One vocabulary across PRDs, specs, code and these pages. When the business has its own word for
something Shopware already names, the Shopware name wins in docs and code — this page records the
mapping so nobody has to guess.

## Shopware terms we use

| Term | Meaning |
|---|---|
| Administration | The merchant back office (Vue application, Admin API) |
| Storefront | The shopper-facing site (Twig/JS, Store API) |
| Sales Channel | A storefront/API channel with its own domain, language, currency |
| Extension | A plugin, app, or theme — say *plugin* only when it is one |
| Store API / Admin API | The two HTTP APIs; Storefront uses the Store API, Administration the Admin API |
| Shopping Experiences | The CMS (layouts, blocks, elements) |
| Flow Builder | Event-driven automation configured in the Administration |
| Rule Builder | Conditions used by prices, promotions, shipping, payment |
| Catalogues | Products, categories, properties, manufacturers |
| Customer group | Customer segmentation used by prices and rules |
| Dynamic product group | Rule-based product set (product streams) |

## Project terms

<!-- One row per project word that differs from Shopware's. Note which domain owns a custom entity. -->

| Project term (from PRDs) | What it maps to | Notes |
|---|---|---|
| Upsell block | Cart-level cross-sell surface built on stock product Cross-Selling | Checkout domain; pools Cross-Selling across cart items — not a new product concept |
| Promo label | Cart text stating the amount missing to a merchant-set target amount | Checkout domain; carries no reward by itself |

## Terms we do not use

Don't say **admin panel** or **backend** — say *Administration*. Don't say **frontend** or **shop
front** — say *Storefront*. Don't say **shop** for a channel — say *Sales Channel*. Don't say
**plugin** when the thing may be an app or theme — say *Extension*. Don't say **module** or
**addon** — say *Extension*. Don't say **CMS page** — say *Shopping Experiences layout*.

---

*Scope: project terms and the Shopware terms they map to — not a Shopware glossary. · Last synced:
2026-09-06 · Verified against Shopware 6.7.13 · Re-sync: add a row whenever a PRD introduces a new
project term.*
