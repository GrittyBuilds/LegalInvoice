# Tenth — Brand Package v1.0

**Tenth** — billing and trust accounting for law firms.
Named for the tenth of an hour: six minutes, the unit a law firm bills in.

Tagline: **Bill to the tenth. Reconcile to the cent.**
Descriptor: **Billing & Trust for Law Firms**

Every file here is self-contained. No fonts, scripts or images are fetched from
the internet — open any HTML file straight from disk and it renders complete.

---

## 01 — Identity

| File | What it is |
|---|---|
| `tenth-brand-guide.pdf` / `.html` | 9-page guide: the name, tagline and voice, the mark and its construction, lockups, misuse, colour, typography, files and licence |
| `tenth-logo-directions.png` | The three directions presented before the choice; keep for the record |
| `logo/` | 15 SVGs and 30 PNG exports, plus `favicon.ico` |

Logo files: `mark` (primary / reversed / mono black / mono white), `lockup-horizontal`
(+ reversed, mono black, mono white), `lockup-stacked` (+ reversed), `wordmark`
(+ reversed), `appicon-dark`, `appicon-light`, `favicon`.

The wordmark is supplied as **outlines** — no font needed to place it, and it can't
drift if someone re-types it. PNG exports are transparent, sized in the filename.

**Geometry:** ring of 10 segments at 36°, 1.6° gaps, stroke `t` = 11 units on a
100-unit grid. The tenth sits at twelve o'clock on radius 35 at stroke 17.
Clear space 2t. Minimum size 16 px / 5 mm.

## 02 — Design system

| File | What it is |
|---|---|
| `tokens.css` | 70 light tokens with a full dark override. `[data-theme="dark"]` on the root or any container flips the theme |
| `tokens.json` | The same values for any non-CSS consumer |
| `tenth-ui-kit.html` / `.png` | Every control in both themes, driven only by the tokens |

Two rules carry through the whole system:

1. **Figures are Geist Mono, tabular.** Money and hours align on the decimal down a
   40-line invoice.
2. **Trust money is teal and nothing else is.** Client (IOLTA) funds never appear in
   the colour of operating money — the misread the product exists to prevent.

All 16 foreground/background pairs measure **≥ 4.5:1** (WCAG AA) in both themes.

## 03 — Product

`index.html` — your application, re-skinned and shipping the brand.

What changed:

- Palette replaced with Tenth tokens; legacy variable names kept as aliases so no
  existing rule broke.
- **Geist Sans + Geist Mono embedded as base64** (SIL OFL 1.1). The app now carries
  its own typography offline — previously it asked for Poppins and silently fell
  back to a system font.
- Sidebar shows the **product** (Tenth) with the active billing company beneath it,
  rather than the firm name alone.
- Title, theme colour and an embedded SVG favicon.
- Money figures switched to monospaced tabular; trust balances rendered in teal.
- **Printed documents were made brand-neutral on purpose.** Invoices, statements and
  retainer requests are the *firm's* documents — Tenth's cobalt appears nowhere on
  them. Section headings are now ruled labels rather than filled emerald bars, which
  reads better and uses a fraction of the toner.
- Focus rings, buttons and the finalise action moved to cobalt with AA contrast.

Everything else — the data model, the localStorage key `legalBilling.v1`, every
calculation — is untouched. An existing backup imports without change.

## 04 — Go to market

| File | What it is |
|---|---|
| `tenth-landing.html` | Full landing page with product screenshots embedded |
| `tenth-one-pager.pdf` / `.html` | Single-page A4 sell sheet |
| `tenth-email-signature.html` | Table-based signature; logo embedded, four fields to fill |
| `tenth-social-card.png` | 1200 × 630 for link previews |
| `screenshots/` | Source captures at 2× |

The screenshots use a **fictional firm** — Whitlock & Reyes, PLLC and invented
clients — so nothing from your practice appears in marketing material.

---

## Typefaces

Geist Sans and Geist Mono, © Vercel, under the **SIL Open Font License 1.1** — free
to embed and redistribute inside licensed software provided the licence text travels
with them. Chosen deliberately over a commercial face so a licensed copy of Tenth
carries no font liability.

## Before this ships to anyone else

- USPTO knockout search, Classes 9, 36 and 42
- Domain acquisition
- Pantone / CMYK matching if anything goes to a commercial printer
- A decision on whether Tenth licenses through the firm or its own entity

*Billing software, not legal advice. Each firm remains responsible for its own
compliance with the Michigan Rules of Professional Conduct.*
