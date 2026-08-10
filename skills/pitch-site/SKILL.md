---
name: pitch-site
description: Build a Bayuratech spec-demo pitch site for a Malaysian SME prospect — research the business from its Instagram/Facebook/TikTok/Foodpanda presence, build a single-file HTML demo with a fresh design, and write the research + outreach docs. Use when given a prospect's social media or business URL and asked to build them a site, demo, or pitch.
---

# Building a Bayuratech pitch site

Naqiuddin (Bayuratech) cold-pitches Malaysian SMEs by building them a complete demo
site **on spec**, then messaging them with the link. This skill is the whole pipeline.

Each prospect gets one folder under `D:/2025_project_portfolio/<slug>/` holding exactly
three files. Demos deploy to `<slug>.bayuratech.com`.

**Work in this order.** Research grounds the design; skipping ahead produces a generic
site that reads as a template and kills the pitch.

---

## 1. Research the prospect

Use **Playwright MCP**, not just WebFetch — most of what matters is behind JS.

| Source | What to pull | How |
|---|---|---|
| Instagram | Followers, post count, bio, outlet list, Linktree URL | `browser_navigate` then read `meta[name="description"]` — it carries follower/post counts **without login** |
| Linktree | Real brand colours, locations, order links | `browser_take_screenshot` then **Read the image** — this is the single best source of their actual palette |
| Foodpanda / GrabFood | Full menu with real prices, rating, review count | `browser_evaluate` over `[data-testid="menu-product"]`; falls back to `document.body.innerText` |
| Facebook | Address, hours, follower count, review sentiment | Often needs login for deep scraping — take what the public page gives |
| TikTok | Follower count | WebSearch is usually enough |
| WebSearch | SSM/Sdn Bhd registration, incorporation date, outlet count | Search the exact business name |

Deep IG/FB scraping needs a login. Don't fight it — the profile `<meta>` tag plus the
Linktree usually covers everything you need.

**Record confidence for every fact.** Mark each as confirmed ✅ or needs-verification ⚠️.
Anything unverified stays **off the website** — put it in `notes.md` as a to-confirm item
instead. Never invent hours, prices, addresses, or phone numbers.

### Hero photo
Search Pexels for the trade, then **confirm the photo by actually viewing it** — navigate
to the image URL, screenshot, and Read it. Record the Pexels ID, description, and URL in
`notes.md`. A wrong-looking hero photo is the fastest way to lose a pitch.

---

## 2. Choose a design that has never been used

**This is the hard rule.** Read `reference/differentiation.md` before writing any CSS.
Every site must bring a font pair, colour theme, and hero layout that appear nowhere in
that table.

Why: these prospects are all in the same small area, pitched by the same person. If two
of them compare demos, identical-looking sites destroy the pitch's credibility.

Then **append the new row in bold** to that table — both in `reference/differentiation.md`
here and in the new project's `notes.md`.

Match the theme to the trade: ice cyan for aircond (cold), plum + rose for a florist,
ivory + gold for a spa, ember for a burger joint.

> **Best move when available:** if the prospect already has brand colours — screenshot
> their Linktree or profile and build the palette from *their* real identity. It reads as
> genuine effort rather than a swapped template, and it's a strong line in the pitch message.

---

## 3. Build `index.html`

One self-contained file. No build step, no framework, no external CSS/JS. Google Fonts is
the only external request, plus Pexels photo URLs.

Start from `reference/page-skeleton.html` — it carries the full house style as a
token-driven boilerplate. The architecture and its signature moves are documented in
`reference/architecture.md`.

Non-negotiables:
- `:root` design tokens, then reset, then `/* ── SECTION ── */` blocks; body mirrors with `<!-- SECTION -->`
- Copy in **Bahasa Melayu**, `<html lang="ms">`, prices as `RM`
- Icon-free and emoji-free in the UI itself
- Breakpoints exactly **960px** and **640px**; `.nav-links { display: none }` at 640
- WhatsApp CTA is `#25D366` with a green glow, linking `wa.me/60...?text=<url-encoded Malay>`

---

## 4. Verify it in a browser — always

`file:` URLs are blocked in Playwright. Serve it first:

```powershell
# run_in_background: true — a foreground server blocks, and Start-Job dies with the call
Set-Location 'D:\2025_project_portfolio\<slug>'; python -m http.server 8899 --bind 127.0.0.1
```

Then `browser_navigate` to `http://127.0.0.1:8899/index.html` and check at **1440**, **960**
and **390** px:

```js
// horizontal overflow check — the page body must never scroll sideways
document.documentElement.scrollWidth > window.innerWidth + 1
```

Screenshot each width and **Read the images** — look at the result, don't assume it works.
Stop the server with `TaskStop` when done.

Gotcha: a `fullPage` screenshot fires before `loading="lazy"` images resolve, so
below-fold photos look broken. Scroll the section into view and wait before judging —
check `img.naturalWidth` to tell a real failure from a lazy-load artifact.

---

## 5. Write `notes.md` and `contacts.md`

Copy `reference/notes-template.md` and `reference/contacts-template.md`. Both are required
— the outreach kit is half the deliverable.

`contacts.md` carries four ready-to-send Malay messages: Instagram/Facebook DM, WhatsApp,
a follow-up for 3–4 days later, and a formal email with a subject line. All signed as
Naqiuddin from Bayuratech, always linking the demo URL and `https://www.bayuratech.com/`.

**Adapt the pitch angle to the prospect's size.** The default angle is *"you have no
website"*, which works for a small kedai. For an established multi-outlet Sdn Bhd it reads
as a cold template and gets ignored — find the specific, verifiable gap instead (a
multi-outlet chain whose customers can't find their nearest branch's address or hours
anywhere online is a far stronger opening than "you need a website"). Say so in the
Strategy Notes, and price the job accordingly.

If the prospect has **no public WhatsApp or phone number**, don't invent one and don't
leave a dead button: swap the CTA to their real channels (Foodpanda / Instagram DM) and
flag it at the top of `contacts.md` as the reason.

---

## Reference files

| File | Use |
|---|---|
| `reference/differentiation.md` | The running table of every site's theme/hero/fonts. **Read before designing, append after.** |
| `reference/architecture.md` | The house style — section order, signature CSS moves, tokens |
| `reference/page-skeleton.html` | Token-driven boilerplate to start from |
| `reference/notes-template.md` | Structure for the research doc |
| `reference/contacts-template.md` | Structure for the outreach kit |
