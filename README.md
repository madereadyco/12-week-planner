# Made Ready Co — 12-Week Planner Website

The public-facing marketing site for **Made Ready 12-Week Planner (MR12W)** — the only Google Sheets 12 Week Year tracker on Etsy with built-in automated execution scoring. Sold by [Made Ready Co](https://madeready.co) on Etsy.

Live at: **[madereadyco.github.io/mr12w-site](https://madereadyco.github.io/mr12w-site/)**

---

## Brand

| | |
|---|---|
| Brand | Made Ready Co |
| Domain | madeready.co |
| Email | madeready.co@gmail.com |
| Product | Made Ready 12-Week Planner (MR12W) |
| Internal code | MR12W |
| Etsy shop | Made Ready Co |

---

## The product

**Made Ready 12-Week Planner (MR12W)** is a Google Sheets implementation of the 12 Week Year methodology (Moran & Lennington) that:

- Sets a vision and enforces a hard maximum of 3 goals per 12-week cycle
- Plans weekly tactics across all 12 weeks plus a 13th buffer week
- Automatically scores execution via a live scorecard — Tasks Set and Tasks Done pull from the Weekly Plan via COUNTIFS, no manual counting
- Tracks daily habits with a checkbox grid and weekly compliance percentage
- Runs entirely inside the buyer's own Google account — no subscription, one-time purchase
- Works for personal goals (fitness, habits, side projects), work goals (OKRs, sales targets), or both

**MR12W Pro** adds Claude AI running invisibly inside the sheet — an AI Weekly Coach reviewing your scorecard every Friday, an AI Cycle Insight written analysis at cycle end, and Off-Track Alerts flagging struggling goals before the cycle ends — with no API key required from the buyer.

### Pricing

| Version | Price | Key addition |
|---|---|---|
| MR12W Standard | £12.99 | Full automated execution scoring system |
| MR12W Pro | £24.99 | Claude AI coaching, cycle insight, off-track alerts |
| MR12W Pro Upgrade | £10.00 | For existing Standard customers |

### The unique differentiator

Zero other 12 Week Year templates on Etsy have automated execution scoring. Every competitor is a static, manual-entry template. The scorecard reads from the Weekly Plan automatically — buyers tick tactics off, the score calculates itself.

**Supporting research (Etsy audit 2026):**
- 225 monthly searches for "12 Week Year" on Etsy
- Only 26 competing sellers — one of the most lopsided demand-to-competition ratios on the platform
- 95% click-through rate on the search term
- 0 competing templates found with automated execution scoring

---

## Repository contents

```
mr12w-site/
├── index.html      ← Single-page marketing site (all HTML, CSS, JS in one file)
└── README.md       ← This file
```

The entire site is a self-contained HTML file. No build step, no dependencies, no npm, no framework.

---

## Site sections

| Section | ID | Description |
|---|---|---|
| Hero | — | Headline, goal type pills, trust signals, formula bar eyebrow |
| Sheet preview | — | Interactive 5-tab spreadsheet mockup (clickable tabs) |
| Method banner | — | 4 research-backed stats making the competitive case (225 / 26 / 0 / 85%) |
| How it works | `#how-it-works` | 5-step setup walkthrough + MR12W Pro AI flow diagram |
| Features | `#features` | 9 feature cards (Standard + Pro) |
| What is the 12 Week Year? | `#method` | Plain English methodology explainer + execution score visual |
| Standard vs Pro | `#comparison` | Full feature comparison table |
| Pricing | `#pricing` | Two pricing cards + upgrade path |
| Reviews | `#reviews` | Three testimonials + 3 research-backed stats |
| FAQ | `#faq` | 8 questions including "Do I need to have read the book?" |
| CTA | `#get-it` | Etsy buy button |
| Footer | — | Links, contact, SEO tags |

---

## Interactive sheet preview tabs

The mockup shows all 5 real tabs with realistic data:

| Tab | Formula bar shows | What it demonstrates |
|---|---|---|
| 🎯 Vision & Goals | `=B4+83` | Cycle end date auto-calculates from start date |
| 🗓️ Weekly Plan | `='🎯 Vision & Goals'!$B$4+0` | Week dates pull from Vision tab |
| 📊 Scorecard | `=IFERROR(AVERAGE(D3:D14),0)` | 12-week average calculates automatically |
| 🔁 Habit Tracker | `=IFERROR(COUNTIF(B3:H3,TRUE)/7,0)` | Week % from daily checkboxes |
| 🪞 Review | `=IFERROR('📊 Scorecard'!D17,"—")` | Average score pulled into review |

---

## Tech

- Pure HTML, CSS, and vanilla JS — no framework, no build tool
- Google Fonts: DM Sans, Inter, JetBrains Mono
- Dark mode default, light mode toggle (preference saved to `localStorage` as `mr12w-theme`)
- Responsive at 760px breakpoint (hamburger menu with SVG open/close icons)
- Interactive sheet mockup — 5 clickable tabs with formula bar and caption updates
- Deployed via GitHub Pages

---

## Design system

Shared with the MRBT marketing site — same CSS variable structure, same component patterns, same breakpoints. The two sites should remain visually consistent as both evolve.

**Theme variables (dark/light via `[data-theme]` attribute on `<html>`):**

```css
--bg, --bg-mid, --bg-soft
--text-primary, --text-body, --text-muted, --text-faint
--border, --border-light
--card-bg, --card-hover
--green: #1E7E34  (primary — consistent across all Made Ready Co products)
```

**Fonts:**
- Display headings: DM Sans (600/700 weight)
- Body: Inter (300/400/500)
- Code/monospace: JetBrains Mono

---

## How to update

**Quick edit (no local setup needed):**

1. Open `index.html` in this repo on GitHub
2. Click the pencil ✏️ icon
3. Make your changes
4. Click **Commit changes** → **Commit directly to main**
5. GitHub Pages rebuilds automatically — live within ~60 seconds

**Local edit:**

```bash
git clone https://github.com/madereadyco/mr12w-site.git
cd mr12w-site
# edit index.html in VS Code or any editor
git add .
git commit -m "describe your change"
git push
```

**Things you'll need to update when the Etsy listing goes live:**
- Hero and CTA `href` values — currently `#pricing`, should point to the real Etsy listing URL
- Reviews section — replace placeholder testimonials with real ones as they come in
- Stats banner — update numbers if search volume or competitor count changes materially

---

## Full product roadmap

### ✅ Phase 0 — Foundation (Complete)

- [x] Product named: **Made Ready 12-Week Planner (MR12W)**
- [x] Market research confirmed: 225 searches / 26 sellers / 95% CTR
- [x] Two-tier pricing confirmed: Standard £12.99 / Pro £24.99
- [x] Upgrade path confirmed: £10 for existing Standard customers
- [x] Marketing site built: `mr12w-site/index.html`

---

### ✅ Phase 1 — Build MR12W Standard (Complete)

- [x] `MR12W_Builder.gs` self-installing Apps Script written
- [x] Tab 1: 🎯 Vision & Goals — cycle dates, vision box, 3-goal limit, category dropdown
- [x] Tab 2: 📋 Action Plan — tasks linked to goals, due week dropdown, done checkboxes
- [x] Tab 3: 🗓️ Weekly Plan — 12 weeks + buffer week, dates auto-calculated, tactic rows
- [x] Tab 4: 📊 Scorecard — COUNTIFS auto-scoring, 85% target, colour-coded status, 12-week average
- [x] Tab 5: 🔁 Habit Tracker — daily checkboxes, week % formula, duplicate function
- [x] Tab 6: 🪞 Review — weekly + end-of-cycle reflection, average score pulled from Scorecard
- [x] Menu: `🤖 Made Ready 12-Week` with Score This Week, Duplicate Habit Tracker, Pro upgrade prompts
- [x] Friday reminder trigger installed on build
- [x] Bug fixed: `setFrozenColumns(1)` moved to end of `buildHabitTrackerTab()` to avoid merge conflict

---

### 🏪 Phase 2 — Etsy Launch

Get MR12W Standard live and generating its first sales.

- [ ] Master Google Sheet built from `MR12W_Builder.gs` in `madeready.co@gmail.com`
- [ ] Sheet set to **Anyone with the link can view**
- [ ] Make-a-copy link generated (`/copy` URL)
- [ ] Etsy listing: MR12W Standard £12.99
  - [ ] Title generated via Made Ready Listing Generator (MRLG)
  - [ ] All 13 tags filled
  - [ ] 7–10 listing images (hero, tab previews, scorecard detail, lifestyle)
  - [ ] Demo video uploaded
  - [ ] First 160 characters of description keyword-optimised
- [ ] ReadMe PDF — 4-step visual setup guide (Canva)
- [ ] Loom setup video — 90 seconds showing Vision → Weekly Plan → Friday scoring ritual
- [ ] Delivery PDF wrapping Make-a-copy link
- [ ] Test purchase confirms download flow end to end
- [ ] Etsy Ads: £1–2/day for first 30 days

**Launch trigger:** Delivery assets complete + listing images shot + test purchase confirmed.

---

### 🤖 Phase 3 — MR12W Pro (AI layer)

Build the £24.99 product. Start after Standard has 10+ sales.

- [ ] Add Pro routes to `madeready-ai-api`:
  - [ ] `/api/weekly-coach` — reads scorecard data, returns one specific adjustment suggestion
  - [ ] `/api/cycle-insight` — reads full 12-week scorecard, returns written performance analysis
  - [ ] `/api/off-track` — flags goals with execution % consistently below 60%
- [ ] Wire Pro menu items to real endpoints (remove upgrade prompt alerts)
- [ ] Test full flow: Friday score → AI Coach response written to Scorecard tab
- [ ] Etsy listing: MR12W Pro £24.99
- [ ] Etsy listing: MR12W Pro Upgrade £10.00

**Launch trigger:** 10+ Standard sales + `madeready-ai-api` Pro routes tested and stable.

---

### 📈 Phase 4 — Product improvements (v2)

Build after Pro is live and revenue is consistent.

- [ ] Goal progress visualisation — mini progress bars on Scorecard per goal
- [ ] Cycle comparison tab — compare execution % across multiple 12-week cycles
- [ ] Shared/couples mode — two users tracking goals in one sheet
- [ ] Export to PDF — end-of-cycle summary (Apps Script → HTML → PDF via `HtmlService`)
- [ ] Update site to reflect new features
- [ ] Consider price increase to Standard £14.99 / Pro £29.99 at v2

---

### 🌐 Phase 5 — Move to Vercel + own domain

- [ ] Connect `madeready.co` to Vercel
- [ ] `mr12w-site` repo connected to Vercel for auto-deploy on push
- [ ] Consider a unified `madeready.co` site with product pages for MRBT, MR12W, and MRLG

---

## Related repos

| Repo | Description | Status |
|---|---|---|
| `madeready-site` | MRBT marketing website | ✅ Live |
| `mr12w-site` | This repo — MR12W marketing website | ✅ Built |
| `madeready-ai-api` | Shared AI backend (Vercel + Neon Postgres) | ✅ Live |
| `madeready-sheets-templates` | Private — all `.gs` builder scripts | ✅ Private |

---

*© 2026 Made Ready Co · madeready.co · madeready.co@gmail.com*
