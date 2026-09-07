---
title: "Cart upsell widget (Administration)"
nav_order: 1
parent: Checkout
grand_parent: Domains
domain: checkout
surface: administration
feature: cart-upsell-widget
status: planned
extension: null
spec: null
prd: specs/0001-cart-upsell-widget.md
verified_against: Shopware 6.7.13
last_synced: 2026-09-07
tags: [checkout, administration, planned]
related: [../storefront/cart-upsell-widget.md, ../index.md, ../../platform/configuration.md]
---

# Cart upsell widget — Administration

What a merchant admin maintains for the cart upsell block and its promo label: the goods-value
threshold, the label's target amount, and the product Cross-Selling the block draws from. Why this
exists: [Checkout domain index](../index.md#features).

## Status

> ⚠️ NOT BUILT
>
> **What exists in the repo:** the PRD `specs/0001-cart-upsell-widget.md` (In progress, 70%, nine open questions) and the WIP ADR
> `specs/0001-cart-upsell-widget-adr-extension-topology.md` (proposed). No tech spec.
> **What is missing:** everything — `custom/plugins/`, `custom/apps/` and `custom/static-plugins/` are
> empty, `src/` holds only an empty `src/Controller`, `composer.json` requires nothing beyond
> `shopware/*` plus `symfony/flex` and `symfony/amqp-messenger`, and `bin/console plugin:list` was not
> reachable (docker service `web` not running).
> **Reference:** PRD AC-1..AC-11; verification not run. Checked against the repo on 2026-09-07.
>
> Do not describe this feature as available. Everything below is the *intended* design from the PRD.
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

## Developer (planned)

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
  shipping price matrices, none of which exposes an amount back to the storefront. Which extension holds that setting follows
  from [ADR-0001-extension-topology](../../../../../specs/0001-cart-upsell-widget-adr-extension-topology.md) (WIP, proposed), the project-wide rule that
  features ship inside a domain plugin rather than one of their own; it is still proposed.
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
  - A Rule Builder rule is not owned by a sales channel, so a per-channel threshold needs the stock
    Sales Channel condition added to the rule — whether that is wanted is open (PRD Q-7).
  - Open in the PRD (`_TBD_`, PRD §11 Q-1..Q-9): whether the label's target amount is a second
    setting or the threshold itself, what reaching it promises the shopper, whether both amounts are
    shop-wide or per sales channel, and whether they are maintained net or gross (Q-8).

## Related

- Counterpart surface: [../storefront/cart-upsell-widget.md](../storefront/cart-upsell-widget.md)
- Domain: [../index.md](../index.md)
- PRD: [../../../../../specs/0001-cart-upsell-widget.md](../../../../../specs/0001-cart-upsell-widget.md)
- ADR: [ADR-0001-extension-topology](../../../../../specs/0001-cart-upsell-widget-adr-extension-topology.md) (WIP, proposed)
- Platform: [../../platform/configuration.md](../../platform/configuration.md)

## Decision Log

- 2026-09-07 — Domain set to checkout by user (ambiguous between checkout and marketing)
- 2026-09-07 — Documented as `built` on the user's instruction for a demo run; the built-check found no code under `custom/` or `vendor/` and no verification report
- 2026-09-07 — Status changed built→planned by built-check (no artefact under custom/, src/ or vendor/; plugin:list not reachable)
- 2026-09-07 — User enforced documentation although the built-check found no code

---

*Last synced: 2026-09-07 · Verified against Shopware 6.7.13 · Re-sync: re-run `sw-document-feature`.*
