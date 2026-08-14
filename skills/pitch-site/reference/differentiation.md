# Design Differentiation Table

**Read this before writing any CSS. Append the new row (in bold) after the build.**

Every site must bring a font pair, colour theme, and hero layout that appear nowhere below.
Also copy this table into the new project's `notes.md`.

> Sites are labelled by trade, not client name — this repo is public. The rule only needs
> the theme / hero / fonts columns to work, so the labels are deliberately anonymous.
> Keep it that way when you append.

| Site | Theme | Hero Layout | Fonts |
|------|-------|-------------|-------|
| Burger #1 | Dark + Ember Orange | Full dark floating | Bebas Neue, Oswald |
| Burger #2 | Red + Yellow | Split 55/45 dark | Bebas Neue, Barlow |
| Burger #3 | Dark + Neon Green | Full dark collage | Anton, Space Grotesk |
| Clinic #1 | Teal + Gold | Full dark 100vh | DM Serif, Plus Jakarta |
| Clinic #2 | Navy + Gold | Split diagonal dark | Playfair, Outfit |
| Clinic #3 | Dark + Amber | Full dark bottom-anchor | Big Shoulders, Nunito |
| Tuition #1 | Navy + Yellow | Full dark bottom-anchor | Montserrat, Poppins |
| Training #1 | Forest + Cream | Light split right panel | Raleway, Lato |
| Florist #1 | Deep Plum + Rose | Dark + photo, stats strip | Cormorant Garamond, DM Sans |
| Restaurant #1 | Deep Brown + Terracotta | Dark + photo, stats strip | Fraunces, Work Sans |
| Homestay #1 | Dark Botanical + Tan | Centered + CTA + stats strip | Lora, Karla |
| Agency #1 | Deep Navy + Violet | CSS glow blobs (no photo) | Syne, DM Sans |
| Automotive #1 | Charcoal + Ice Cyan | Left-gradient fade (dark left) | Exo 2, Inter |
| Spa #1 | Warm Ivory + Rose + Gold | 2-col light (no dark overlay) | Bodoni Moda, Jost |
| Chicken #1 | Cobalt Blue + Cayenne Red + Butter Cream | Cobalt poster block + arch photo + tilted stickers | Archivo Black, Manrope |
| Cafe #1 | Ink Black + Bone + Sage | Full-bleed photo + inset hairline frame (magazine cover), centred light serif | Newsreader, Figtree |
| Cafe #2 *(reusable template)* | Espresso + Oat + Brass | Bottom-anchored asymmetric split over full-bleed photo | EB Garamond, Hanken Grotesk |
| **Clinic #4 *(reusable template)*** | **Chalk + Clay + Deep Olive** | **Light editorial, left type stack + circular photo mask with hairline rings** | **Spectral, Epilogue** |

---

## Fonts already spent

Anton · Archivo Black · Barlow · Bebas Neue · Big Shoulders · Bodoni Moda ·
Cormorant Garamond · DM Sans · DM Serif · EB Garamond · Exo 2 · Figtree · Fraunces ·
Hanken Grotesk · Inter · Jost · Karla · Lato · Lora · Manrope · Montserrat · Newsreader ·
Nunito · Oswald · Outfit · Playfair · Plus Jakarta · Poppins · Raleway · Space Grotesk ·
Spectral · Syne · Work Sans · Epilogue

## Hero layouts already spent

Full dark floating · Split 55/45 dark · Full dark collage · Full dark 100vh ·
Split diagonal · Full dark bottom-anchor · Light split right panel · Dark + photo stats
strip · Centered + CTA + stats strip · CSS glow blobs (no photo) · Left-gradient fade ·
2-col light split · Cobalt poster block + arch photo + stickers ·
Magazine-cover inset hairline frame · Bottom-anchored asymmetric split ·
Light editorial + circular photo mask

## Ideas not yet used

- Full-bleed photo with a bottom-anchored frosted card
- Asymmetric two-photo collage with a vertical headline
- Split with a diagonal clip-path seam
- Marquee headline that scrolls behind the CTA

---

## Reusable templates vs client sites

Some builds are **generic templates** pitched to many prospects in one trade (the aircond site,
Cafe #2). They still get a differentiation row, because the template itself must not clone an
existing client site — if a prospect ever sees both, the pitch dies.

Rules for templates:

- Give it a neutral invented brand name, never a real one
- **No fabricated social proof** — no review counts, star ratings, follower numbers or "since
  20XX". Use only structural facts (hours, menu size, number of spaces). Add the prospect's real
  numbers after you know them
- Avoid photos containing any legible business name or signage
- Put a **swap list** at the top of `index.html` as a comment, and repeat it in `notes.md`
- A straight content swap of a template does **not** earn a new differentiation row — only a
  genuine restyle does

---

## The "premium / not AI slop" mode

Some briefs ask for an editorial, high-end feel (studied from `cartelcoffeeshop.com` and
`thetepen.my`). The default house devices are exactly what makes those briefs fail. When
this mode is requested, **drop** the ticker, the ghost word, glows, pill radii and drop
shadows — and instead:

- Display serif at **weight 300–400, never bold**, large, with slight negative tracking
- Tiny uppercase labels: ~11–12px, weight 600, `letter-spacing: 0.2em–0.26em`
- One accent colour, used sparingly — hairlines, eyebrows, hover, nothing more
- 1px hairlines (`rgba(text, 0.13)`) as the main structural device; square corners
- Outlined buttons that invert on hover
- Menus as editorial lists with dotted leaders, not cards
- Generous section padding (8rem desktop) and real photography doing the work

The signal is **restraint**. If an element exists to be impressive, cut it.
