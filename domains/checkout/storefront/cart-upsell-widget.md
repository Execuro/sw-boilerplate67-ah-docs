---
title: "Cart upsell widget (Storefront)"
domain: checkout
surface: storefront
feature: cart-upsell-widget
status: built
extension: null
spec: null
prd: specs/0001-cart-upsell-widget.md
verified_against: Shopware 6.7.13
last_synced: 2026-09-06
tags: [checkout, storefront]
related: [../index.md, ../../platform/configuration.md]
---

[Wiki home](../../../index.md) › [Domains](../../index.md) › [Checkout](../index.md) › Cart upsell widget

# Cart upsell widget — Storefront

Once a cart's goods value passes a merchant-set threshold, the cart and offcanvas cart show an
upsell block offering up to four cross-sell products the shopper can add in one step. A separate
promo label states how much is still missing to reach a merchant-set target amount. The business
reasoning lives in the [domain index](../index.md#features).

## Status

`built` — documented for a demo run without a code-evidence check, at the user's instruction. Only
the PRD (`specs/0001-cart-upsell-widget.md`) backs this page; there is no tech spec and no ADR yet.

## Business user

Guests and registered customers see it, in every storefront sales channel and customer group.

- **Above the threshold:** the block appears on both the full cart page and the offcanvas cart, as
  up to four product cards (name, image, price, add button). Candidates are the Cross-Selling
  products of the items already in the cart, pooled and de-duplicated, minus anything already in the
  cart or not purchasable in that sales channel.
- **Adding a product** puts it in the cart at its normal price in one action; the block then
  re-evaluates — the added product drops out and its own Cross-Selling may join the pool.
- **At or below the threshold**, or when no eligible product remains, neither the block nor an empty
  placeholder is shown.
- **The promo label** states the amount still missing to the target, in the shopper's active
  currency. Threshold and target are plain numbers compared without currency conversion.

Deliberately out of scope: product-detail-page recommendations, discounts or free gifts on the
upsell products, a curated fallback product set, and the checkout confirm page.

## Developer

- **Where:** PRD only (`specs/0001-cart-upsell-widget.md`); no implementation paths recorded.
- **Extension points used:** not confirmed against code — expected to be a cart-level collector or
  page-loaded subscriber plus Twig block overrides in the cart and offcanvas cart templates.
- **Decisions:** threshold and promo target are merchant-set, not fixed in code; the product source
  is stock Cross-Selling rather than a curated set; the compared figure is the goods value before
  shipping, not the cart total; adding is one step at the normal price.
- **Config:** threshold amount and promo-label target amount — see
  [configuration](../../platform/configuration.md); no config keys recorded yet.
- **Debug/observe:** nothing feature-specific yet — general tools in
  [debugging](../../platform/debugging.md) and [logging](../../platform/logging.md).
- **Gotchas:** the PRD still leaves open whether the promo label's target is the same amount as the
  block's visibility threshold, what the label shows once the target is reached, and which cart
  figure counts toward it. Treat those as undecided until a tech spec settles them.

## Related

- [Checkout domain](../index.md)
- PRD: `specs/0001-cart-upsell-widget.md`

## Decision Log

- 2026-09-06 — User enforced documentation as a demo run; built-check gate was skipped and status
  was set to `built` without code evidence.

---

*Last synced: 2026-09-06 · Verified against Shopware 6.7.13 · Re-sync: re-run `sw-document-feature`
once the feature has a tech spec and a verification report.*
