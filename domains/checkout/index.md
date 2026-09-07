---
title: Checkout
has_children: true
nav_order: 1
parent: Domains
type: domain
purpose: The cart and the steps from it to a placed order — cart contents, shipping and payment selection, order placement.
scope: Everything the shopper does between the cart and the order confirmation, plus the merchant settings that steer it. Product data and cross-selling maintenance belong to Catalogues; the placed order and its lifecycle belong to Orders.
last_synced: 2026-09-07
verified_against: Shopware 6.7.13
resync: sw-document-feature updates the feature table.
tags: [checkout, domain, index]
---

# Checkout

What the shopper does from the cart to the placed order, and the merchant settings that steer it.
Maintaining product data and each product's Cross-Selling happens in Catalogues; everything after the
order is placed belongs to Orders.

## Features

| Feature | Why (business goal) | Administration | Storefront | Status |
|---|---|---|---|---|
| Cart upsell widget | The cart is the last place to grow the order value: shoppers already above a merchant-set goods value are offered companion products from the cart items' Cross-Selling, and a promo label tells shoppers below a target amount how much is still missing. | [page](administration/cart-upsell-widget.md) | [page](storefront/cart-upsell-widget.md) | built |

## Domain notes

- The goods value used across this domain is the product sum as displayed to the shopper, before
  shipping costs and unaffected by promotion discounts.
- Amounts configured for this domain are plain numbers applied in the shopper's active currency —
  no conversion happens, so 20 means 20 EUR for a EUR shopper and 20 USD for a USD shopper.
- This domain deliberately does not own product recommendations outside the cart: the product detail
  page uses stock Cross-Selling and belongs to Catalogues.

## Related

- [../index.md](../index.md)

---

*Scope: cart to order placement. · Last synced: 2026-09-07 · Verified against Shopware 6.7.13 ·
Re-sync: reconcile the feature table with `domains/checkout/*/`.*
