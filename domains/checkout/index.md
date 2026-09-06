---
title: Checkout
has_children: true
nav_order: 1
parent: Domains
type: domain
purpose: Cart, shipping and payment selection, order placement.
scope: Cart contents and pricing, cart-level upsell/promo surfaces, shipping/payment method selection, checkout confirm/finish. Post-placement order lifecycle belongs to Orders.
last_synced: 2026-09-06
verified_against: Shopware 6.7.13
resync: sw-document-feature updates the feature table.
tags: [checkout, domain, index]
---

# Checkout

Everything from the cart up to and including order placement. What happens to an order after it is
placed belongs to the Orders domain.

## Features

| Feature | Why (business goal) | Administration | Storefront | Status | Spec |
|---|---|---|---|---|---|
| Cart upsell widget | Grows order value at the last point of the funnel: shoppers above a merchant-set cart threshold see cross-sell products they can add in one step, and a promo label nudges shoppers below a target amount toward it. | — | [page](storefront/cart-upsell-widget.md) | built | — |

## Domain notes

- The upsell block's visibility threshold reuses the stock Rule Builder "Goods price" condition —
  no new Administration surface was built for it.
- Upsell candidates come from stock product Cross-Selling, pooled across the cart items and
  de-duplicated; no new product data is introduced.
- The promo label's target amount is a merchant-set amount and grants no reward by itself; any
  reward (free shipping, discount) would be a separate stock Promotion.

No extension of its own yet — see the [extensions inventory](../platform/extensions-inventory.md).

---

*Scope: cart, shipping and payment selection, order placement — the post-placement lifecycle is
Orders. · Last synced: 2026-09-06 · Verified against Shopware 6.7.13 · Re-sync: reconcile the
feature table with `domains/checkout/*/`.*
