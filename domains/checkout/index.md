---
title: Checkout
type: domain
purpose: Cart, shipping and payment selection, order placement.
scope: Cart contents and pricing, cart-level upsell/promo surfaces, shipping/payment method selection, checkout confirm/finish. Post-placement order lifecycle belongs to Orders.
last_synced: 2026-09-06
verified_against: Shopware 6.7.13
resync: sw-document-feature updates the feature table.
tags: [checkout, domain, index]
---

# Checkout

**Purpose:** Cart, shipping and payment selection, order placement. **Scope:** Everything up to and including order placement; post-placement lifecycle is Orders.
**Last synced:** 2026-09-06 · **Verified against:** Shopware 6.7.13
**How to re-sync:** Reconcile the table with `domains/checkout/*/`.

Extension: none yet — see [extensions inventory](../platform/extensions-inventory.md).

## Features

| Feature | Why (business goal) | Administration | Storefront | Status | Spec |
|---|---|---|---|---|---|
| Cart upsell widget | Grows order value at the last point of the funnel: shoppers above a merchant-set cart threshold see cross-sell products they can add in one step, and a promo label nudges shoppers below a target amount toward it. | — | [page](storefront/cart-upsell-widget.md) | built | — |

## Domain notes

- The upsell block's visibility threshold reuses the stock Rule Builder "Goods price" condition — no new admin surface was built for it.
- The upsell candidates come from stock product Cross-Selling, pooled across cart items and de-duplicated; no new product data.
- The promo label's target amount is a merchant-set amount (see the feature page); it does not grant any reward by itself.

## Related

- [../index.md](../index.md)
