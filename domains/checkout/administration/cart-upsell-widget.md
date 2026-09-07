---
title: "Cart upsell widget (Administration)"
nav_order: 1
parent: Checkout
grand_parent: Domains
domain: checkout
surface: administration
feature: cart-upsell-widget
status: built
extension: null
spec: null
prd: specs/0001-cart-upsell-widget.md
verified_against: Shopware 6.7.13
last_synced: 2026-09-07
tags: [checkout, administration]
related: [../storefront/cart-upsell-widget.md, ../index.md, ../../platform/configuration.md]
---

# Cart upsell widget — Administration

What a merchant admin maintains for the cart upsell block and its promo label: the goods-value
threshold, the label's target amount, and the product Cross-Selling the block draws from. Why this
exists: [Checkout domain index](../index.md#features).

## Status

`built` — no `sw-verify-feature` report exists; documented on the user's instruction for a demo run
(see Decision Log). AC-1..AC-11 of `specs/0001-cart-upsell-widget.md` are the reference.

## Business user

- **Threshold** — the goods value above which the block appears. It is a Rule Builder condition on
  the goods price (Settings → Rule Builder), so the amount is changed there without a code change.
  Delivered with 20 as its initial value; the change takes effect on the next cart view.
- **Target amount of the promo label** — the amount the label counts toward, maintained as a merchant
  setting and likewise effective on the next cart view.
- **Which products are offered** — the Cross-Selling of each product (Catalogues → Products →
  Cross-Selling). Nothing is maintained per cart: editing a product's Cross-Selling changes what the
  cart offers on the next cart view. There is no curated fallback list — when nothing qualifies, the
  block simply stays hidden.
- **Label wording** — translatable storefront text; stock Snippets (Settings → Snippets) is the
  facility for editing it per language. Whether the wording is merchant-editable is still open
  (PRD Q-6).
- No new admin module, no ACL role and no per-cart data is introduced by this feature.

## Developer

- **Where:** no dedicated extension is recorded for this project yet (`extension: null`). The
  merchant side is entirely stock surfaces — Rule Builder, product Cross-Selling, Snippets — plus the
  setting holding the label's target amount. All shopper-visible behaviour lives on the
  [Storefront page](../storefront/cart-upsell-widget.md).
- **Extension points used:** stock Rule Builder goods-price condition for visibility; stock product
  Cross-Selling as the candidate source; stock Snippets for the label text.
- **Decisions:** the threshold is expressed as a Rule Builder condition rather than a bespoke
  setting, so the merchant edits it with the tooling they already use, and it is compared as a plain
  number in the shopper's active currency (PRD C-1, BR-2). The label's target amount needs a setting
  of its own — stock keeps amounts only inside Rule Builder conditions, promotion cart rules and
  shipping price matrices, none of which exposes an amount back to the storefront.
- **Config:** threshold (Rule Builder condition) and the label's target amount; see
  [../../platform/configuration.md](../../platform/configuration.md).
- **Debug/observe:** [../../platform/logging.md](../../platform/logging.md) ·
  [../../platform/debugging.md](../../platform/debugging.md).
- **Gotchas:**
  - Raising the threshold hides the block for carts between the old and the new value immediately, on
    their next cart view — existing carts are not grandfathered.
  - The threshold is not currency-aware: the same number is compared in whatever currency the shopper
    uses.
  - A Cross-Selling product that is out of stock or not visible in the sales channel is silently
    dropped, which can empty the block for a cart that otherwise qualifies.
  - Open in the PRD (`_TBD_`, PRD §11 Q-1..Q-6): whether the label's target amount is a second
    setting or the threshold itself, and what reaching it promises the shopper.

## Related

- Counterpart surface: [../storefront/cart-upsell-widget.md](../storefront/cart-upsell-widget.md)
- Domain: [../index.md](../index.md)
- PRD: [../../../../../specs/0001-cart-upsell-widget.md](../../../../../specs/0001-cart-upsell-widget.md)
- Platform: [../../platform/configuration.md](../../platform/configuration.md)

## Decision Log

- 2026-09-07 — Domain set to checkout by user (ambiguous between checkout and marketing)
- 2026-09-07 — Documented as `built` on the user's instruction for a demo run; the built-check found no code under `custom/` or `vendor/` and no verification report

---

*Last synced: 2026-09-07 · Verified against Shopware 6.7.13 · Re-sync: re-run `sw-document-feature`.*
