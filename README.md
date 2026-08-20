# Brand Colours — PDP, Bag, Checkout and Account

`brand-colours.html` shows the new group colour palettes in use across the PDP,
Added to Bag, Checkout and Account screens for Debenhams, boohoo, boohooMAN,
PLT and Karen Millen, with **Before, After and Pick-a-colour side by side** per
brand. The third phone has a colour picker: pick any primary and the full shade
ramp (Neutral, Neutral Pressed, Light 4-1, Dark 1-3, Primary Dark, CTA) is
derived live using the design system's mix ratios (lights/neutrals mix towards
white, darks towards black — verified exact against the KM ramp; the CTA keeps
the hue at a contrast-safe darkness), and every colour-token component on the
screen recolours — including the Deliver+ box (mapped to a palette slot per
brand: deb Neutral, boohoo Light 3, PLT Light 2, MAN and KM Primary Dark) and
boohoo's Light 3 USP banner and sale badge. Text ink flips white or black
automatically by WCAG contrast, and the picker header reports **WCAG AA**
(4.5:1) for the two pairs that matter: button text on the picked primary and
the derived CTA colour on white. Mono banners and the extended palette
intentionally stay put. Open it in a browser; no server or build step.
Deep links work too: `brand-colours.html?brand=bh&screen=checkout&pick=ff6600`.
Fonts come from Google Fonts and
the boohoo PDP pulls two images from mediahub.boohoo.com, so first load wants a
network connection. Everything else is local under `brand-assets/`, which must
travel with the HTML file.

The page is: App Store icon brand switcher → full brand palette → golden truth
buttons (Before / After) → the two phones.

## Sources

- Palettes (full, per brand): Debenhams Design System `aIHmkCaTy9c5EWOxAGw0So`,
  🎨 COLOURS page. Debenhams `11241:47116`, boohoo `11241:47015`,
  PLT `11904:2395`, Karen Millen `11763:2228`, BOOHOOMAN `12482:2057`.
- Buttons (golden truth, bound to the palettes): node `12681:158518` in the same
  file. Rendered at component size (358×50, Tertiary 40, XS 31). Secondary
  borders bind to Dark 2, Tertiary fills to Neutral, Text Only to the CTA colour.
- PDPs: VTO - Virtual Wardrobe `LxHqA4rFpRYNWJu8vzn18X` per brand — Debenhams
  `15203:68314`, boohoo `15067:47748`, PLT `15203:70973`, boohooMAN
  `15235:24424`. Karen Millen mirrors the Debenhams PDP in Jost with the KM
  palette. PDPs stop after the payment CTAs, followed only by the Deliver+
  banner.
- Deliver+ (brand-specific across all screens): SEEL Enhancements 2026
  `CQIe2e2c0iagD1T9WjdYsx` — Debenhams `164:22195`, boohooMAN `164:22591`,
  boohoo `164:23057`, PLT `164:23851`, KM `164:23448`. Styling and logos from
  Figma; tick copy from the live sites. Logos live in `brand-assets/deliver/`.
- Checkouts: Checkout 2026 `WChEtDPH0LcErdYFS9SESn`, "Brands Checkout" section,
  Signed In - Card Pre-selected per brand.
- App icons: public App Store listings (iTunes Search API), in
  `brand-assets/app-icons/`.

## Before / After per brand

- **Debenhams and PLT** are already live on the new palette, so Before equals
  After for both. PLT renders with **0 border radius** on all components.
- **boohoo** Before follows the live site: `#444444` primary CTAs with
  `#444444` outlined secondaries and black banners. After applies Pink
  `#F8B5CC` with CTA Pink `#BB305F` and Dark 2 `#EA92B0` secondary borders.
- **boohooMAN** stays mono in both states (black CTAs and links); After
  introduces the Aggressive Green `#01FE8A` accent (account balance card).
- **Karen Millen** Before is the live site: black primary CTAs and links with
  grey outlined secondaries. After applies Primary `#DB4E11` with CTA
  `#8E330B` on the Debenhams PDP layout, set in Jost.
- Buttons are one component per brand, used identically on every screen (PDP
  Add to Bag, bag sheet, checkout, promo Apply). The account View Balance and
  Sign Out are XS CTA instances (31px, 12px, regular) — View Balance with the
  card's colour overrides per the designs. **After** follows the design
  system for every brand: SemiBold 600 in the brand font, Primary uppercase,
  Secondary sentence case with a Dark 2 border, Text Only in the CTA colour.
  **Before** follows each live site: Debenhams aqua with all-caps grey-border
  secondaries; boohoo #444444 Montserrat 700 all caps; boohooMAN black
  Montserrat 700 all caps with grey-border secondaries; PLT garnet Roboto 500
  all caps with grey-border secondaries; KM black Jost 400 sentence case.
  Text Only CTAs (checkout Change / Delete links) are black, underlined and
  regular/light on every live site (`--link-ink/--link-w/--link-deco`); the
  design system moves them to the CTA colour in SemiBold, no underline.
- Body weights per live site: Geologica 300, Montserrat 400, Roboto 400,
  Jost 400.
- The navy Pay button and the extended palette (reds, greens, yellow) are fixed
  across the framework and do not change with brand or state.

Colours are driven entirely by CSS custom properties scoped to
`.phone[data-brand][data-state]` (weights via `--w-btn/--w-body/--w-bold`,
Deliver+ via `--dplus-bg/--dplus-ink/--dplus-link`), so each swatch change is
one token edit. The two phones are runtime clones of a single hidden template,
so screen markup only exists once.

---

Internal design prototype. Not production code, and not a Debenhams product.
