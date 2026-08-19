# Vertical: law firms (peguam / firma guaman)

Read this **before researching or designing** a law firm prospect. A law firm website is
regulated publicity. Almost every move that wins a café or burger pitch — prices,
testimonials, star ratings, "yang terbaik", a confident claim about outcomes — is
prohibited here, and the person you are pitching reads legislation for a living.

**Primary source.** Legal Profession (Publicity) Rules 2025, **P.U. (A) 462/2025** —
gazetted 26 Dec 2025, **in force 1 January 2026**, made under s.77(1) Legal Profession Act
1976 by the Bar Council with the Attorney General's approval. Bar Council Circular
No 471/2025 carries the gazette as an attachment and is publicly downloadable:

- https://www.malaysianbar.org.my/cms/upload_files/document/Circular%20No%20471-2025.pdf
  (the rules text begins at page 2; extract with `pdftotext -layout`)
- The Bar's own rules page is **members-only** — do not rely on being able to open it.

⚠ **Rule 10 revoked the 2001 Rules.** Any guide, blog post, competitor site or older
template written against the Legal Profession (Publicity) Rules 2001 is out of date.
Re-verify before every build: Circular 471/2025 says the Bar Council's Legal Profession
Committee is **still reviewing its Rulings** in light of the new Rules, and further Rulings
may issue.

---

## The rule that changes the whole pitch

> **Rule 7(a)** — "Any person shall not in any publicity ... **specify the fees charged** by
> the person for his or its services"

**No prices. Anywhere.** No table, no "bermula dari RM…", no hourly rate, no package. This is
the single biggest departure from every other vertical in this portfolio, where a real price
list is normally the strongest content on the page.

Replace the pricing section with an **enquiry route** plus an FAQ entry that explains *why*
no fee is shown. Handled well, that FAQ answer is itself a credibility signal — it shows the
firm the developer knows their rules.

---

## Prohibited — do not put these on a law firm site

| Rule | What it forbids |
|---|---|
| **7(a)** | Any statement of the fees charged |
| **7(b)** | Comparison or criticism of another firm's fees or service quality |
| **7(c)** | Direct *or indirect* reference to a case the firm acted in, where that breaches confidentiality — no case studies, no "we recovered RM X" |
| **5(2)(a)** | Material misrepresentation — e.g. listing a practice area the firm does not actually handle |
| **5(2)(b)** | Omitting a material fact |
| **5(2)(c)** | **Information that cannot be verified** — this kills invented statistics. In a *template* there is no safe placeholder stat: no "20 tahun pengalaman", no "500+ transaksi", no client counts, no ratings |
| **5(2)(d)** | Anything **likely to create an unjustified expectation about the results** — no "pasti lulus", no guarantees, no timelines phrased as promises |
| **6(1)** | Claiming to be an **"expert"** / **"pakar"**. *Specialisation* may be claimed, but only if justifiable under 6(3): qualifications, experience, proportion of time in the field, level of success |
| **4** | Anything adversely affecting the **dignity and standing** of the profession |

### The testimonial trap
Testimonials are a trap, but **not for the reason most people assume**. The words
"testimonial" and "endorsement" appear **nowhere** in the 2025 Rules — there is no express
ban. They fail instead under **5(2)(c)** (unverifiable) and **5(2)(d)** (creates expectations
about results). State that basis. Claiming a non-existent express prohibition to a lawyer
destroys your credibility on everything else you have said.

### The stock-photo trap
**Images are NOT restricted.** The gazette never mentions images, photographs or logos —
photography is a design decision here, not a compliance one. Never tell a firm otherwise.

What to avoid is the cliché: gavels (not even used in Malaysian courts), scales of justice,
Greek columns, suited handshakes. Under **rule 4** that imagery works against the dignity
requirement, and it is what every other Malaysian law firm site already looks like.

What works instead: leather-bound law volumes, architectural detail, a restrained office
interior — dark, low-key, no people, no signage. The reference build uses Pexels **159720**
(law volumes, gold spine lettering) full-bleed behind the masthead with a two-stop scrim.
A photo-free typographic hero also works but tends to read as bland; the reference build
started photo-free and had the photo added afterwards.

### Hero type and the ticker
Set the hero headline in the **sans**, not the display serif. A large serif headline reads as
generic and over-precious on a law firm site; bold sans is more direct. Keep the serif for
section headings and the wordmark so the document character survives below the fold. Do not
italicise the accent word unless the italic is actually loaded — a faux-slanted sans looks
broken; colour alone is enough.

A scrolling practice-area ticker works here and is not undignified if it is built quietly:
~60s (not the 38s used on F&B sites), small letterspaced caps, hairline borders, **practice
areas only — never a claim or superlative**, and `prefers-reduced-motion` honoured.

Build separators as **CSS-drawn shapes** (a 4px rotated square), not glyph escapes. A
`C6` escape is font-dependent, and in generation it can be re-read as an octal escape and
land in the file as a control character.

### There is NO pre-approval regime
Unlike private clinics under the MAB (see `clinic.md`), **nothing requires Bar Council
sign-off before publishing.** The 2025 Rules are principle-based and enforced after the fact
under rule 9(4), which lets the Bar Council order publicity altered, withdrawn or removed.
Do not tell a firm they need approval — they will know you are wrong.

---

## Rule 9 — the one that lands on YOU

> **9(1)** — the person is responsible for publicity "whether such publicity is done by the
> person, **any employee of the person or any party acting on behalf of the person**"

The web developer is a party acting on the firm's behalf. If you publish a page in a firm's
name that breaches the Rules, the professional exposure lands on the **lawyer**.

Practical consequences:

1. Put `<meta name="robots" content="noindex, nofollow">` on any demo carrying a real firm's
   name, and send the link directly rather than posting it.
2. Get the firm's **written approval of the exact wording** before anything goes public.
3. Say in writing that all copy goes to them for approval. It is the professional posture,
   and it is also reassuring to the client.
4. Never *guarantee* compliance. Say the site is **built to** the 2025 Rules and the firm
   should satisfy itself before publication — guaranteeing it is exactly the kind of
   unverifiable claim the Rules exist to stop.

---

## Permitted, and what to build instead

Firm name, address, contact details, office hours, languages spoken, practice areas the firm
genuinely handles, and neutral factual information are all fine.

The strongest compliant content for a Malaysian conveyancing-led firm:

- **Proses** — the step-by-step conveyancing sequence (booking form → official & bankruptcy
  searches → SPA → loan documents → stamp duty & state consent → registration of transfer →
  completion). First-time buyers genuinely do not know this. Pure factual process
  information, fully compliant, and the most useful thing such a firm can publish.
- **Dokumen yang diperlukan** — the document checklist. Every firm answers this by phone
  all day.
- **Soalan lazim** — including one entry explaining why no fee is displayed.

These occupy the slots that would normally hold prices and social proof.

Always include a footer disclaimer: general information only, not legal advice, no
solicitor–client relationship created by reliance on it.

---

## Research sources for a law firm

- Malaysian Bar firm directory (name, address, practising status)
- Google Maps listing — hours, phone, whether a website field exists at all
- Their existing site, if any — **and check it against the 2025 Rules**; pre-2026 sites
  frequently carry fee indications or testimonials that the current Rules do not permit
- Do **not** rely on review sites or aggregator "top 10 lawyers" listings for anything you
  put on the page

---

## The pitch angle

Two that work, in order:

1. **The rules changed on 1 January 2026.** Most Malaysian law firm sites were built against
   the 2001 Rules and never revisited. Offering a free read-through of their existing site
   against the current Rules is a door-opener no generic web freelancer offers. Frame it as
   observations for their consideration, never as legal advice.
2. **It answers the same phone call fifty times a week** — the process and document sections
   are staff time back, an operational saving rather than marketing.

**Do not lead with** more clients, Google ranking, or "grow your practice". That reads as
touting and sits badly against rule 4.

**Tone:** plain, precise, unhurried. Email rather than Instagram DM. Minimal emoji. Price
higher than café or F&B prospects.

---

## Compliance self-audit

Run before shipping any law firm build, excluding any documentation comment block:

```
grep -onE 'RM[[:space:]]*[0-9]|bermula dari [0-9]|fi sebanyak' body.html
grep -onE '[0-9]+\+|[0-9]+ tahun pengalaman|sejak [0-9]{4}|[0-9]+ klien' body.html
grep -oniE 'pakar|expert|terbaik|jamin|menang|guarantee|testimoni|bintang' body.html
```

All three must return nothing.

---

## Still applies

Everything in `SKILL.md` — the differentiation rule, the single-file build, the 960/640
breakpoints, the three-file folder convention. The reference build for this vertical is
`D:/2025_project_portfolio/peguam-template/`, which also stores the extracted rules text as
`publicity-rules-2025.txt`.
