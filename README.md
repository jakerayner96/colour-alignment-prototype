# Brand Colours — PDP, Added to Bag, Bag, Checkout and Account

`brand-colours.html` shows the **final signed-off styling** for each brand —
Debenhams, boohoo, boohooMAN, PLT and Karen Millen. Pick a brand and all five
screens render **side by side**: PDP, Added to Bag, Bag, Checkout and Account.
The Before states, the colour picker and the screen switcher were removed
after the KM review (Aug 2026). Open it in a browser; no server or build
step. Deep links work: `brand-colours.html?brand=km`. Fonts come from Google
Fonts and the boohoo PDP pulls two images from mediahub.boohoo.com, so first
load wants a network connection. Everything else is local under
`brand-assets/`, which must travel with the HTML file.

The page is: App Store icon brand switcher → the five screens side by side →
full brand palette → golden truth buttons (the full design-system state
matrix: Default, Touch down, Disabled, Spinner and the Added / Checkout
Securely icon states for every CTA type).

**Click-to-inspect:** click any element on the page and a floating card
reads out its colour, font, size, weight, background (composited through
transparent parents), border and WCAG contrast with an AA pass/fail badge.
Esc or ✕ closes it; the brand tiles keep their normal behaviour.

## Signed-off decisions (KM review, Aug 2026)

- **Karen Millen** keeps Primary orange for the primary CTAs (Add to Bag,
  View Bag, Buy Now) and the account balance card — updated to `#D24508` so
  white button text clears WCAG AA at 4.57:1 (the original `#DB4E11` sat at
  4.11:1). The full shade ramp is re-derived from the new primary with the
  design system mix ratios, giving the darker orange `#892D05` (8.6:1 on
  white) for text links (Change / Delete / Discounts / bold T&C copy) and
  the tick boxes. Secondary CTAs (Continue Shopping, Apply, Change Payment
  Method) keep a **black outline with black copy**, and the Virtual Try On
  hanger and filled tick circles stay **black**.
- **boohoo** drops the pink palette entirely and runs **black and white,
  mirroring boohooMAN**: black primary CTAs, black links and ticks, mono
  banners and a black account balance card.
- **boohooMAN** is unchanged: black with the Aggressive Green `#01FE8A`
  accent on the account balance card.
- **Debenhams and PLT** were already live on the new palette. PLT renders
  with 0 border radius on every component.

## Bag (Bag 2026)

The Bag shows **4 products from 2 sellers** by default: the boohoo cardigan
and TIRTIR cushion delivered by the brand, and the Living and Home fireplace
and Prada perfume delivered by marketplace seller Pachamama. **Every card
variant from the design is built into the markup** and toggled with the
`hidden` attribute — search `data-card=` in the HTML and delete `hidden` to
turn one on:

| `data-card`      | Variant                                                    |
|------------------|------------------------------------------------------------|
| `standard`       | plain product card with the bin / count / plus stepper (on) |
| `beauty`         | beauty product card (on)                                    |
| `oos`            | out of stock: red border + alert banner, bin only           |
| `qty-unavail`    | quantity unavailable: alert + stepper with disabled plus    |
| `egift`          | e-Gift Card with the View Details info link                 |
| `unlimited`      | Debenhams Unlimited subscription card                       |
| `protect-add`    | protection plan offer with Add                              |
| `protect-active` | protection plan active with Remove                          |
| `subscribe`      | Subscribe & Save module with Save 5% chip                   |
| `assembly`       | Assembly Available, powered by Taskrabbit                   |
| `sold`           | black "Sold X times" banner                                 |
| `freegift`       | attached Free Gift (Lancôme bundle)                         |
| `comp-sample`    | Complimentary Sample card                                   |
| `custom`         | customised product with Bag Label rows                      |
| `preorder`       | Pre-Order chip + estimated dispatch banner                  |
| `gifts`          | Your Gifts section (Benefit bundle)                         |
| `topup`          | Need A Top-Up? section                                      |
| `samples`        | Choose 2 free samples carousel                              |

Below the cards: the Deliver+ module from SEEL Enhancements 2026 `2903:2410`
(branded header on the brand's Deliver+ colour with the SEEL USP list on
white and the Trustpilot / Seel footer), a Promo Code section, then the
Order Summary — Subtotal, Delivery, expandable Discounts, the brand's
Deliver+ optional add-on, Order Total (matching the checkout summary),
Checkout with / without Deliver+, the wallet buttons (PayPal, Pay Later,
Apple Pay, Klarna) and the available payment options row. The design's
Rewards banner was dropped from the order summary on request. The payment
row carries 8 of the design's 9 chips — Clearpay's logo only exists in Figma
as loose vector fragments, so it is omitted rather than redrawn.
boohoo's Deliver+ module keeps its SEEL branding on Light 3 pink `#FFE0EB`
even though the boohoo CTAs are mono.

## Added to Bag (Bag 2026)

Bottom sheet over the PDP: bordered product panel (68×102 thumb, 12px type),
a "You have qualified for 99p delivery" tick line (tick circle fills with the
brand's Dark 3), then Continue Shopping (secondary) above View Bag (primary).

## Account (Account 2026)

Centred balance card per brand (Debenhams aqua gradient, boohoo and
boohooMAN black — MAN with the green button — PLT garnet, KM Primary orange)
with a white View Balance button, then 56px menu rows with black status
tags/counters and a centred grey Sign Out. Row sets follow the designs:
Debenhams and KM get the fuller sets (Unlimited / Premier, Beauty Club,
Debenhams Mastercard); boohoo, boohooMAN and PLT the shorter ones.

## Sources

- Palettes (full, per brand): Debenhams Design System `aIHmkCaTy9c5EWOxAGw0So`,
  🎨 COLOURS page. Debenhams `11241:47116`, boohoo `11241:47015`,
  PLT `11904:2395`, Karen Millen `11763:2228`, BOOHOOMAN `12482:2057`.
- Buttons (golden truth): node `12681:158518` in the same file, with the KM
  black-outline and boohoo mono decisions applied on top.
- PDPs: VTO - Virtual Wardrobe `LxHqA4rFpRYNWJu8vzn18X` per brand — Debenhams
  `15203:68314`, boohoo `15067:47748`, PLT `15203:70973`, boohooMAN
  `15235:24424`. Karen Millen mirrors the Debenhams PDP in Jost.
- Bag: Bag 2026 `CYyGeUDy4w02enV7uFxZ6W` — bag + cards `1337:250006`,
  Added to Bag modal `1337:253191`, quantity selector `1234:76756`.
  Product imagery and icons exported from the file into `brand-assets/bag/`.
- Account: Account 2026 `2KLlzqIWlDcri8YIHwEd63` — PLT `1288:10469`,
  Debenhams `1296:69796`, boohoo `1304:17722`, Karen Millen `1304:29816`.
  boohooMAN mirrors boohoo. The boohoo pink card and the KM black card in
  those designs are overridden by the signed-off colours above.
- Deliver+ (brand-specific across all screens): SEEL Enhancements 2026
  `CQIe2e2c0iagD1T9WjdYsx` — styling and logos from Figma; tick copy from the
  live sites. Logos live in `brand-assets/deliver/`.
- Checkouts: Checkout 2026 `WChEtDPH0LcErdYFS9SESn`, "Brands Checkout"
  section, Signed In - Card Pre-selected per brand, restructured per node
  `3990:36587`: "Promo Code or Gift Card" and "Paying with…" are separate
  sections (the old Redeem Gift Card row folded into the promo section).
- App icons: public App Store listings (iTunes Search API), in
  `brand-assets/app-icons/`.

Colours are driven entirely by CSS custom properties scoped to
`.phone[data-brand]` (weights via `--w-btn/--w-body/--w-bold`, Deliver+ via
`--dplus-bg/--dplus-ink/--dplus-link`, plus `--vto` for the VTO hanger,
`--tickc` for the filled tick circles and `--tert` for tertiary CTA fills),
so each swatch change is one token edit. The navy Pay button and the extended
palette (reds, greens, yellow) are fixed across the framework.

---

Internal design prototype. Not production code, and not a Debenhams product.
