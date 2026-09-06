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

# Cart upsell widget — Storefront

## Summary

The cart and offcanvas cart show an upsell block once the cart's goods value passes a merchant-set threshold, offering up to 4 cross-sell products the shopper can add in one step. A promo text label separately states how much is still missing to reach a merchant-set target amount. For the why, see [Domain index](../index.md#features).

## Status

`built` — documented for this demo run without a code-evidence check (user instruction: skip validation, assume built). No PRD `[adr]` markers and no tech spec exist yet; only the PRD (`specs/0001-cart-upsell-widget.md`) backs this page.

## Business user

- Guests and registered customers, all customer groups, on all storefront sales channels.
- Above the threshold: the block appears on the full cart page and in the offcanvas cart, showing up to 4 product cards (name, image, price, add button), pooled from the Cross-Selling of the products already in the cart, excluding anything already in the cart or not purchasable in the sales channel.
- Adding a card's product places it in the cart at its normal price with one action; the block re-evaluates immediately (the added product drops out, its own Cross-Selling may join the pool).
- At or below the threshold, or when no eligible product remains, no block and no empty placeholder are shown.
- The promo label states the amount still missing to a merchant-set target amount, in the shopper's active currency; both the threshold and the target are plain numbers with no currency conversion.
- Out of scope: product-detail-page recommendations, discounts/free gifts on upsell products, a curated fallback set, and the checkout confirm page.

## Developer

- **Where:** PRD only — `specs/0001-cart-upsell-widget.md`. No tech spec or code paths recorded yet.
- **Extension points used:** _TBD_ — expected to be a cart processor/cart widget plus Twig blocks in the cart and offcanvas cart templates; not confirmed against code.
- **Decisions:** Threshold and promo-label target are merchant-set amounts, not fixed in code (PRD C-1); source of upsell products is Cross-Selling, not a curated set (PRD C-2); compared amount is the goods value before shipping, not the cart total (PRD C-4); one-step add at normal price (PRD C-8).
- **Config:** Threshold amount and promo-label target amount — see [../../platform/configuration.md](../../platform/configuration.md) (no config keys recorded yet, PRD only).
- **Debug/observe:** See [../../platform/logging.md](../../platform/logging.md), [../../platform/debugging.md](../../platform/debugging.md) — nothing feature-specific recorded yet.
- **Gotchas:** PRD leaves open whether the promo label's target equals the block's visibility threshold or is a separate amount (Q-1), what happens once the target is reached (Q-4), and which cart figure the label counts toward (Q-5) — treat these as undecided until the tech spec resolves them.

No code listings.

## Related

- Domain: [../index.md](../index.md)
- PRD: `specs/0001-cart-upsell-widget.md`

## Decision Log

- 2026-09-06 — User enforced documentation as a demo run; built-check gate was skipped and status was set to `built` without code evidence.
