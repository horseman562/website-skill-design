# Vertical: private clinics (klinik swasta)

Read this **before researching or designing** a clinic prospect. A clinic is not a kedai
with a stethoscope — its website is a regulated advertisement, and the moves that win a
café pitch (testimonials, "yang terbaik", a big smiling doctor hero) are the exact moves
that are prohibited here.

Everything below is sourced from two documents, both dated after 2023. **Re-verify before
relying on it for a live site** — these guidelines get amended:

- **MAB** — *Advertising Guidelines for Healthcare Facilities and Services*, Medicine
  Advertisements Board, amendment MAB 3/2023, in force 5 July 2023.
  https://pharmacy.moh.gov.my/sites/default/files/document-upload/advertising-guidelines-healthcare-facilities-and-services-mab-3.2023.pdf
- **MMC** — *Guideline of the Malaysian Medical Council: The Dissemination of Information by
  Medical Professionals Including on Social Media*, September 2025.
  https://mmc.gov.my/wp-content/uploads/2025/09/The-Dissemination-of-Information-by-Medical-Profesionals-Including-on-Social-Media.pdf

---

## The rule that changes the whole pitch

**A clinic website that describes services relating to the treatment, prevention or
diagnosis of any ailment is an advertisement, and needs prior approval from the Medicine
Advertisements Board (Lembaga Iklan Ubat) before it is published.**

> MAB 1.3 — "advertisements shall only be publicised upon approval by the Medicine
> Advertisements Board."
> MMC 4.17.3 — "The contents must be submitted as outlined above to the Board for prior
> approval."

MAB 9.1 closes the obvious loophole: anything on the internet reachable from Malaysia must
conform, wherever it is hosted.

**What this means for a spec demo.** Publishing a full services-listing demo at
`<slug>.bayuratech.com` and blasting the link publicly is, on a strict reading, publishing
an unapproved healthcare advertisement in the clinic's name. So for clinic prospects only:

1. Put `<meta name="robots" content="noindex, nofollow">` in the demo's `<head>`, and say
   in the page footer that it is a **draft mockup for the clinic's review**, not a live
   advertisement.
2. Send the link **directly to the clinic** (WhatsApp/DM/email). Do not post it publicly,
   and do not put it in a portfolio page while it carries their name.
3. Prefer an **exempt** hero. MAB 3.1 exempts advertisements that don't refer to any skill
   or service relating to treatment, prevention or diagnosis — and names the exact register
   that is safe: *"klinik mesra keluarga anda"*, *"trust and care for years"*, *"you are in
   safe hands"*, plus location and directional information.

**Turn it into the pitch, not an obstacle.** Say in `contacts.md` that the site is built to
MAB/MMC rules and that you'll prepare the Board submission for the live version. Every
other freelancer pitching that clinic is quietly handing them a compliance problem. This is
the strongest differentiator available in this vertical — lead with it.

---

## Permitted on the site

| Allowed | Source |
|---|---|
| Clinic name, location, telephone number | MAB 4.1 i–ii |
| Hours of service (incl. 24-hour notice) | MAB 4.1 iii, MMC 4.8 |
| Types of accommodation and facilities | MAB 4.1 iv |
| **Charges** for services and facilities | MAB 4.1 v |
| **Packages, discounts, price reductions** | MAB 7.1.1 |
| Practitioner **name, qualification, field of specialty** — listed for information | MAB 4.2, MMC 4.9 |
| Practitioner photographs — **must not exceed one-third the size of the format** | MAB 4.1 vi, MAB 6.8 |
| Services list (Surgical, Maternity, A&E, Rehabilitation…) as recognised by statutory bodies | MAB 4.2 |
| Awards/accreditation — **name and date only**, not overemphasised | MAB 3.4.4, MMC 4.11 |
| Any colours, logos, address of location | MMC 4.17.2 |

Prices being allowed is worth exploiting: a clear, factual fee list is permitted, useful to
patients, and something most clinic sites don't do.

## Prohibited — do not put these on a clinic site

| Prohibited | Source |
|---|---|
| **Laudatory remarks.** Copy must be "informative and simple" | MAB 6.8, MMC 4.17.1 |
| Promotion of an individual practitioner's skills, knowledge or experience | MAB 4.2, MMC 4.9 |
| Claims of being **best / only / first / a breakthrough** | MMC 2.6 |
| Comparison, direct or implied, between healthcare facilities | MAB 5.1 |
| Price comparisons between practitioners or grades of staff | MAB 7.1.2 |
| **Free offers** of healthcare services or treatments | MAB 7.1.3 |
| **Gifts** of any form | MAB 7.2 |
| Patient testimonials about treatment, diagnosis, or a practitioner's skill | MAB 4.5 ii |
| Celebrity/**influencer** endorsement of treatment or practitioner skill | MAB 4.6 |
| Photographs of practitioners performing procedures on patients | MAB 3.4.3, MMC 4.1 |
| Photographs of patients with diseases, tissue specimens, biopsy parts | MAB 5.5, MMC 4.10 |
| **Red Cross / Red Crescent symbol** — a Geneva Convention breach and *illegal* | MMC 4.3.5 |

### The testimonial trap

MAB 4.5 is more permissive than most people assume: testimonials about **the premises** —
cleanliness, friendly staff, a comfortable environment — *are* allowed. Testimonials about
treatment received or a doctor's skill are not.

**Default to no testimonials section at all.** The clinic is run by a registered
practitioner who is separately bound by the MMC Code's rules against advertising and
canvassing (MMC 3.2), and a premises testimonial drifts into treatment territory the moment
a real patient writes it. If the client insists, keep it strictly about the premises and
never reproduce Google reviews — those are almost always about the doctor.

This replaces the testimonials block the general house style would use. Fill the space with
**panel/insurance coverage, the fee list, or operating hours** instead — all permitted, and
all things patients actually search for.

### The red cross trap

Do not reach for a red cross or red crescent as a clinic icon, favicon, or accent motif. It
is not a taste question — it is illegal on private medical premises. The house style is
icon-free anyway (see `../architecture.md`); keep it that way here.

---

## Research sources for a clinic

The general research table in `SKILL.md` is built around F&B — Foodpanda and Linktree are
useless here. Substitute:

| Source | What to pull |
|---|---|
| **Google Maps / Business Profile** | Address, hours, phone, exterior photo, whether it's 24-hour. The single best source for a clinic. |
| Facebook page | Hours, panel list, announcements, doctor names |
| Panel/TPA listings (PMCare, MediExpress, insurer panel directories) | Which panels they accept — a top patient question and rarely on their own site |
| MOH facility listings | Licence status under Act 586, registered name |
| WebSearch on the doctor's name | MMC registration, registrable qualifications, specialty |

**Never republish Google reviews on the site** (see the testimonial trap). Use them for
research only — they tell you what patients complain about, which sharpens the pitch.

**Qualifications must be accurate and registrable.** Copy them exactly as published; do not
tidy "MBBS (UM)" into something grander. An invented or inflated qualification is a
professional-conduct problem for the doctor, caused by you.

---

## Section plan for a clinic demo

Replaces the default section order in `../architecture.md`:

1. **Hero** — clinic name, exempt-register tagline (MAB 3.1), hours + phone, WhatsApp CTA
2. **Services** — factual list, no adjectives, no outcome claims
3. **Doctors** — name, registrable qualification, specialty; photo ≤ ⅓ of the format
4. **Hours** — including public holidays and any 24-hour service
5. **Panels & insurance** — logos or plain list of accepted panels
6. **Fees** *(optional but differentiating)* — permitted under MAB 4.1 v
7. **Location** — map, Waze link, landmark directions, parking
8. **Contact** — WhatsApp, phone, footer noting the draft/mockup status

Copy stays in Bahasa Melayu, `<html lang="ms">`, prices as `RM`, per the house rules.

**Tone check before you ship:** read every heading and ask "is this informative, or is it
selling?" *"Klinik keluarga di Taman X, buka 8 pagi–10 malam"* is informative. *"Penjagaan
terbaik untuk keluarga anda"* is laudatory and breaches MAB 6.8. This is the single most
common thing to get wrong, because it is what every other SME site in the portfolio does.

---

## Still applies

The differentiation rule is unchanged — read `../differentiation.md` before designing,
append the new row after. Clinic palettes drift to the same clinical blue-and-white every
time, so this matters more here, not less. Warm neutrals, deep green, or muted teal all
read as medical without being the default blue.
