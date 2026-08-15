---
name: dashboard-site
description: Build a single-page analytics dashboard — KPI row, interactive charts with hover tooltips, filters and a table view — as a self-contained HTML file. Use when asked for a dashboard, an analytics or statistics page, a KPI/metrics overview, or "a page that shows all our data".
---

# Building a dashboard page

A dashboard is read by a person deciding something. Everything here exists to make the
numbers *correct and comparable*, not decorative.

**Load the `dataviz` skill first if it is available** — it owns the colour method and the
anti-pattern catalog, and this skill assumes its rules. If it is not available, the rules
that matter are restated below.

Reference implementation: **`reference/dashboard-reference.html`** — a complete, working
dashboard (5 charts, 4 KPIs, filters, tooltips, table view, light/dark). Start by reading
it; most jobs are a content swap on that file.

---

## 1. Decide what the dashboard is for

Answer before drawing anything:

- **Who reads it**, and **what decision does it inform?** If no action follows, it should
  be a report, not a dashboard.
- **How many KPIs?** Executive 3–5 · operational 8–12 · analytical unlimited.
- **Max 6–8 charts on a screen.** Prefer fewer, larger charts.

**Every KPI needs a comparison** — vs target, or vs the prior period. A number alone is
meaningless. **Titles state the insight** ("Up 15.6% on the previous 30 days"), not the
column name.

---

## 2. Pick the form before the colour

| The data's job | Form |
|---|---|
| One headline number | Stat tile / hero figure — not a chart |
| Change over time | Line (2px, round caps) |
| Magnitude across categories | Bars, ranked |
| Part-to-whole, at a glance | Donut — **≤ 6 segments**, never for close values |
| Ordered bands (tiers, age) | One-hue ordinal ramp |
| Continuous magnitude on a map/heatmap | One-hue sequential ramp |

---

## 3. Validate the palette — never eyeball it

If `dataviz` is present, run its validator and fix every FAIL before writing chart code:

```bash
node scripts/validate_palette.js "<hex,hex,…>" --pairs all --mode light
node scripts/validate_palette.js "<dark hexes>"  --pairs all --mode dark
```

The reference file ships a **validated trio** (all-pairs, both modes):

| Role | Light | Dark |
|---|---|---|
| series-1 | `#1baf7a` | `#199e70` |
| series-2 | `#2a78d6` | `#3987e5` |
| series-3 | `#eb6834` | `#d95926` |
| neutral (prior period, "Other") | `#b8b6ae` | `#5c5a55` |

Chrome: surface `#fcfcfb`/`#1a1a19` · page `#f9f9f7`/`#0d0d0d` · ink `#0b0b0b`/`#ffffff` ·
secondary `#52514e`/`#c3c2b7` · muted `#898781` · grid `#e1e0d9`/`#2c2c2a`.

**series-1 is 2.74:1 on the light surface — below 3:1.** The *relief rule* applies: every
mark in that colour must carry a visible direct label, and the table view must exist. If
you restyle, re-validate; don't assume.

Hard rules: fixed hue order, never cycled past 8 (fold the tail into "Other"). **Colour
follows the entity, never its rank** — filtering must not repaint the survivors.
Sequential = one hue light→dark. Status colours (good/warning/critical) are reserved and
never double as "series 4".

---

## 4. Layout

F-pattern. Hero KPI top-left; detail bottom-right.

```
filters — ONE row, above everything it scopes
KPI ×4 — hero first, each with a delta
primary chart (wide)        | secondary chart
detail | detail | detail
table view (toggle) · footer: source + last refreshed
```

**Filters go in one row above the charts — never inside a card, never per-chart.** Both of
the reference screenshots this skill was built from had per-card Day/Month/Year toggles;
that is an anti-pattern, because independently filtered charts stop agreeing and the reader
can't tell which slice they're seeing. One row, and everything re-renders against the same
slice. Date range first.

---

## 5. Mark specs

| Mark | Spec |
|---|---|
| Bar / column | **≤ 24px thick**, 4px rounded data-end, **square at the baseline** |
| Line | 2px, round join and cap |
| Marker | ≥ 8px (r ≥ 4), **2px ring in the surface colour** |
| Area fill | series hue at ~10% opacity |
| Gridlines | 1px **solid** hairline, one step off surface — never dashed |
| Between touching fills | **2px gap in the surface colour**, never a border |

**Axis ticks round to clean numbers** — `0 / 5k / 10k / 15k`, never `3.5k` or `37`. Use a
nice-number helper (see the reference file's `niceMax`).

Legend for **≥ 2 series** (a single series needs none — the title names it). Direct-label
**selectively**: the endpoint, the extreme, the one series that matters — never a number on
every point. **Text never wears the series colour**; identity comes from a coloured key
beside it. `tabular-nums` on table columns and axis ticks only — never on a hero figure.

---

## 6. Interaction is part of the deliverable

- **Line/area → crosshair.** A vertical hairline snaps to the nearest X and the tooltip
  lists **every series** at that X. The reader aims at a date, not at a 2px line.
- **Bars, cells, donut segments → the mark is the hit target.** Hovered mark lifts,
  siblings dim.
- **Hit targets are bigger than the marks** — full rows or full bands, ≥24px, never the
  painted pixels.
- **In the tooltip the value leads** (bold, high contrast), the series name follows. Key
  each row with a short stroke of the series colour, not a filled box.
- **Insert labels with `textContent`**, never `innerHTML` — series names come from data.
- **Keyboard focus shows the same readout as hover.** Marks get `tabindex="0"`.
- **Tooltips enhance, never gate** — every value is also reachable from a direct label or
  the table view.

---

## 7. Before calling it done

Render it, screenshot it, and **look at it**. Then check against this list — every entry
below was a real defect caught this way, not theory:

- [ ] Palette validator run, all FAILs fixed
- [ ] No dual-axis chart anywhere (two y-scales invent a correlation)
- [ ] Filtering does not repaint surviving series
- [ ] No value-ramp on nominal categories (it double-encodes bar length)
- [ ] No 2-slice donut or one-bar chart left by a filter state — that's a stat tile
- [ ] Axis ticks are clean numbers
- [ ] Every KPI carries a comparison
- [ ] Table view exists and covers every plotted value
- [ ] Footer shows source + last refreshed
- [ ] Checked at 1440 / 960 / 390px; no horizontal overflow
- [ ] **Dark mode verified by computed colour, not by eye.** Declare tokens on `:root` —
      declaring them only on a wrapper class leaves `body { color: var(--text-1) }`
      unresolvable, and every element without an explicit colour silently inherits black.

---

## Reference files

| File | Use |
|---|---|
| `reference/dashboard-reference.html` | Complete working dashboard — start here |
