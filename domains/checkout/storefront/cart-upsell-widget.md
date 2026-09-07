---
title: "Cart upsell widget (Storefront)"
nav_order: 1
parent: Checkout
grand_parent: Domains
domain: checkout
surface: storefront
feature: cart-upsell-widget
status: built
extension: null
spec: null
prd: specs/0001-cart-upsell-widget.md
verified_against: Shopware 6.7.13
last_synced: 2026-09-07
tags: [checkout, storefront]
related: [../administration/cart-upsell-widget.md, ../index.md, ../../platform/configuration.md]
---

# Cart upsell widget — Storefront

A block in the cart offering companion products the shopper can add in one step, plus a promo label
stating how much is still missing to reach a target amount. Why this exists:
[Checkout domain index](../index.md#features).

## Status

`built` — no `sw-verify-feature` report exists; documented on the user's instruction for a demo run
(see Decision Log). AC-1..AC-11 of `specs/0001-cart-upsell-widget.md` are the reference.

## Business user

**The upsell block**

- Appears in both the full cart page and the offcanvas cart, and only while the cart's goods value is
  *greater than* the merchant's threshold — at exactly the threshold or below, nothing is shown.
- Offers the Cross-Selling products of all products in the cart, pooled and de-duplicated, never a
  product already in the cart, and only products purchasable in the current sales channel.
- Shows at most four products, each as a compact card with name, image, price and an add button.
- Adding a product puts it in the cart at its normal price — no discount, no free gift; the block
  then drops that product and may pick up its Cross-Selling products instead.
- Shows nothing at all — not even an empty placeholder — when no candidate survives those filters.
- Re-evaluates on every cart change: adding, removing, changing a quantity, applying a promotion.
- Guests and registered customers see the same block, in every storefront sales channel and every
  customer group.

**The promo label**

- States the amount still missing to reach the merchant's target amount, in the shopper's active
  currency. Amounts are plain numbers, never converted between currencies.
- Counts the same goods value as the block: the product sum before shipping, unaffected by promotion
  discounts. Selecting a shipping method or entering a promotion code therefore does not move it.

**When something goes wrong:** if an upsell product cannot be added (sold out in the meantime), the
shopper sees the standard cart error message and the cart is left unchanged.

## Developer

- **Where:** no dedicated extension is recorded for this project yet (`extension: null`); the surface
  is the storefront cart and offcanvas cart. See [../administration/cart-upsell-widget.md](../administration/cart-upsell-widget.md)
  for the merchant-side settings that drive both.
- **Extension points used:** the storefront cart and offcanvas cart templates carry the block; the
  candidate list is derived from stock product Cross-Selling and the cart line items, and visibility
  from a Rule Builder goods-price condition. Adding a product uses the stock add-to-cart path — only
  the entry point is new.
- **Decisions:** the upsell source is stock product Cross-Selling of the cart items, not a curated
  set, so no new product data is introduced (PRD C-2). The threshold is merchant-maintained from the
  first release rather than fixed in code, initial value 20 (PRD C-1). The block deliberately stays
  hidden instead of falling back to a curated product set. Discounts and free gifts are out of scope
  — stock Promotions cover pricing if that is wanted later.
- **Config:** the threshold and the label's target amount are merchant settings, described on the
  [Administration page](../administration/cart-upsell-widget.md); see also
  [../../platform/configuration.md](../../platform/configuration.md).
- **Debug/observe:** [../../platform/logging.md](../../platform/logging.md) ·
  [../../platform/debugging.md](../../platform/debugging.md).
- **Gotchas:**
  - The comparison is strictly *greater than* the threshold — a cart at exactly 20 with a threshold
    of 20 shows no block. This is the boundary most often reported as a bug.
  - Thresholds are not currency-converted: the same number applies in every currency.
  - The same product being Cross-Selling of several cart items must still be offered once.
  - Which four of more than four candidates are shown is not a business concern and is not specified.
  - Open in the PRD (`_TBD_`, PRD §11 Q-1..Q-6): whether the label's target is the same value as the
    block threshold, what reaching the target promises the shopper, when the label shows, what it
    shows once the target is reached, which cart figure it counts, and whether its wording is
    merchant-editable per language.

## Related

- Counterpart surface: [../administration/cart-upsell-widget.md](../administration/cart-upsell-widget.md)
- Domain: [../index.md](../index.md)
- PRD: [../../../../../specs/0001-cart-upsell-widget.md](../../../../../specs/0001-cart-upsell-widget.md)
- Platform: [../../platform/configuration.md](../../platform/configuration.md)

## Decision Log

- 2026-09-07 — Domain set to checkout by user (ambiguous between checkout and marketing)
- 2026-09-07 — Documented as `built` on the user's instruction for a demo run; the built-check found no code under `custom/` or `vendor/` and no verification report

---

*Last synced: 2026-09-07 · Verified against Shopware 6.7.13 · Re-sync: re-run `sw-document-feature`.*
