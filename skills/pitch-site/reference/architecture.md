# House architecture

The shape every Bayuratech pitch site shares. Same skeleton, never the same skin —
the visual identity must change every time (see `differentiation.md`).

## File shape

One self-contained `index.html`. No build step, no framework, no external CSS or JS.
Google Fonts is the only external request, plus Pexels photo URLs.

```
:root design tokens
reset + grain overlay
/* ── NAV ── */
/* ── HERO ── */
/* ── STATS STRIP ── */
/* ── TICKER ── */
/* ── SHARED SECTION ── */
/* ── <content sections> ── */
/* ── WA CTA ── */
/* ── FOOTER ── */
/* ── RESPONSIVE 960px ── */
/* ── RESPONSIVE 640px ── */
```

The `<body>` mirrors it with `<!-- NAV -->`, `<!-- HERO -->` … comments.

## Token set

```css
:root {
  --dark / --navy / --card    /* or light equivalents: --ivory --sand --light */
  --accent                    /* primary brand accent */
  --accent-2                  /* secondary / gold */
  --text  --muted
  --nav-h: 76px;
  --r: 14px;                  /* card radius */
}
```

## Section order

Nav → Hero → Stats/Credential strip → Ticker → Services or Menu → one **feature section**
(usually inverted: dark on a light site, light on a dark site) → Why Us (4 cards) →
Locations/Branches → WA CTA → Footer.

The feature section is where a site earns its personality — a pantang highlight, a sauce
lineup, a heat scale, a process flow.

## Signature moves

**Grain overlay** — SVG `feTurbulence` on `body::before`, opacity `0.02`–`0.03`,
`z-index: 9999`, `pointer-events: none`.

**Nav** — fixed, `backdrop-filter: blur(14px)`, translucent background, logo with a
`<small>` sub-label, links, and one pill CTA button.

**Hero eyebrow** — a small uppercase label with a `::before` rule-line (`width: 26px;
height: 1px`), often with a pulsing accent dot.

**Hero title** — `clamp()` sized, with **one word in the accent colour**.

**Stats strip** — 4 cells directly under the hero, big accent numbers over uppercase
letter-spaced labels. Real numbers only: follower counts, years, outlet counts, ratings.

**Infinite ticker** — items **duplicated in the markup** so the loop is seamless:

```css
.ticker-track { display: flex; width: max-content; animation: ticker 38s linear infinite; }
@keyframes ticker { from { transform: translateX(0); } to { transform: translateX(-50%); } }
```

**Cards** — `translateY(-4px)` lift plus an accent border and soft shadow on hover.
Optionally an animated bottom-border reveal (`width: 0 → 100%`).

**Ghost word** — one giant thematic Malay word behind the final CTA, in the display font:

```css
-webkit-text-stroke: 2px rgba(<accent>, 0.09);
color: transparent;
```

Past ghosts: `SEJUK` (aircond), `Cantik` (spa), `BK` (florist), `HOT` (hot chicken).

**WhatsApp button** — always `#25D366` with a green glow shadow, linking
`wa.me/60...?text=<url-encoded Malay message>`.

**Footer** — logo + tagline left, socials centre, copyright right.

## Content rules

- Copy in **Bahasa Melayu**, `<html lang="ms">`, warm and direct
- Prices as `RM`
- Icon-free and emoji-free in the UI itself (emoji belong in the pitch *messages*, not the site)
- Real, verified facts only — anything unconfirmed goes in `notes.md`, not on the page
- If a price source is a delivery platform, say so in a disclaimer line under the menu

## Responsive

Breakpoints exactly **960px** and **640px**.

- 960: multi-column grids drop to 2; 2-col feature sections stack
- 640: `.nav-links { display: none }`, grids drop to 1, `section` padding shrinks,
  footer becomes `flex-direction: column; text-align: center`

The page body must never scroll horizontally at any width.
