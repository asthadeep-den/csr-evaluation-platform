# CSR Impact Evaluation Platform
### by Astha Deep · M&E & CSR Advisory

A full-stack, single-file CSR partner evaluation tool. Browse 22 NGOs across Karnataka & Maharashtra, filter and shortlist, add to an evaluation cart, run a weighted scoring framework, and explore impact assessment across geographic reach, SDG alignment, Theory of Change, and outcome indicators.

**Design:** Vintage editorial — yellow parchment · black bold type · Playfair Display headers

---

## Live deploy (GitHub Pages)

```
https://<your-username>.github.io/<repo-name>/
```

---

## What's inside

### Three views, one file

| View | What it does |
|------|-------------|
| **Discover** | Browse all 22 NGOs. Filter by state, theme, size, FCRA status. Live search. Add any to evaluation cart. |
| **Evaluate** | 5-step weighted scoring framework on your cart selection. Adjustable dimension weights. Financial health audit. Allocation recommendation. |
| **Impact Assessment** | Geographic reach map (D3 India choropleth) · SDG alignment matrix · Theory of Change flow · Outcome indicator dashboard. |

### Evaluation framework (5 steps)

| Step | Content |
|------|---------|
| 1 — Mandate Brief | Selected partners, theme/state coverage, evaluation methodology |
| 2 — Partner Profiles | Full org cards: FCRA, budget, beneficiaries, programme, score |
| 3 — Scoring Matrix | Drag sliders to adjust 6 dimension weights; scores and chart update live |
| 4 — Financial Health | Utilization rate, admin overhead, audit status, red flags (High / Medium / Clear) |
| 5 — Recommendation | Ranked output · Selected / Conditional / Not Recommended · Portfolio allocation table |

### Impact Assessment (4 panels)

| Panel | Content |
|-------|---------|
| Geographic Reach | D3 India map · KA + MH highlighted · NGO location dots sized by beneficiary reach · Hover tooltips · Filter by cart / theme |
| SDG Alignment | 10 SDGs × 22 NGOs matrix · Primary ● and Secondary ◐ contributions · Filter by theme or cart |
| Theory of Change | Education and Livelihoods results chains · Inputs → Activities → Outputs → Outcomes → Impact |
| Outcome Indicators | Education / Livelihoods / Cross-cutting KPI cards with benchmarked progress bars |

---

## NGO database (22 organisations)

| # | Organisation | State | Theme | Budget |
|---|-------------|-------|-------|--------|
| 1 | Akshara Foundation | KA | Education | ₹24 Cr |
| 2 | Parikrma Humanity Foundation | KA | Education | ₹8 Cr |
| 3 | Dream a Dream | KA | Education | ₹12 Cr |
| 4 | Samarthanam Trust | KA | Mixed | ₹35 Cr |
| 5 | Swami Vivekananda Youth Movement | KA | Livelihoods | ₹18 Cr |
| 6 | Vikasana | KA | Livelihoods | ₹5 Cr |
| 7 | Concerned for Working Children | KA | Education | ₹6 Cr |
| 8 | Gramin Vikas Trust | KA | Mixed | ₹4.2 Cr |
| 9 | Gram Vikas Samithi | KA | Livelihoods | ₹3 Cr |
| 10 | Pratham Education Foundation | MH | Education | ₹380 Cr |
| 11 | SEWA Bharat | MH | Livelihoods | ₹42 Cr |
| 12 | Magic Bus India Foundation | MH | Education | ₹45 Cr |
| 13 | Apnalaya | MH | Livelihoods | ₹9 Cr |
| 14 | Catalysts for Social Action | MH | Livelihoods | ₹8.5 Cr |
| 15 | iTeach Schools | MH | Education | ₹6 Cr |
| 16 | Masoom | MH | Education | ₹4 Cr |
| 17 | Mann Deshi Foundation | MH | Livelihoods | ₹15 Cr |
| 18 | Hamara Foundation | MH | Livelihoods | ₹3.5 Cr |
| 19 | Ummeed Child Development Center | MH | Education | ₹11 Cr |
| 20 | Teach For India | KA + MH | Education | ₹82 Cr |
| 21 | Nudge Foundation | KA + MH | Livelihoods | ₹55 Cr |
| 22 | Yuwa India | MH | Education | ₹2 Cr |

---

## Deploy to GitHub Pages

**1. Create a new repository**
```
github.com/new → name it e.g. csr-evaluation-platform
```

**2. Upload both files**
```bash
git init
git add index.html README.md
git commit -m "Launch CSR evaluation platform"
git remote add origin https://github.com/<username>/<repo>.git
git push -u origin main
```

**3. Enable Pages**
```
Settings → Pages → Source: Deploy from branch → main / root → Save
```

Live in ~60 seconds at `https://<username>.github.io/<repo>/`

---

## Add or edit NGOs

All data lives in the `ALL_NGOS` array inside the `<script>` block:

```js
{
  id: 22,                    // unique integer, increment from last
  name: 'Full Name',
  short: 'ShortName',        // ≤10 chars — used in chart/table headers
  hq: 'City',
  state: 'KA',               // 'KA' | 'MH' | 'both'
  est: 2005,
  theme: 'edu',              // 'edu' | 'live' | 'mix'
  themeLabel: 'Education',
  fcra: 'Active',            // 'Active' | 'Under renewal'
  budgetNum: 12,             // number in Cr (powers size filter)
  budget: '₹12 Cr',
  bene: '45,000/yr',
  beneNum: 45000,            // number (powers map dot sizing)
  prog: 'Programme description',
  scores: [8.5, 8.0, 7.5, 7.0, 9.0, 8.0],
  // Dimensions order:
  // [Governance, Programme Quality, Financial Health, M&E, Mission Alignment, Partnership]
  util: 89,                  // fund utilization %
  admin: 13,                 // admin overhead %
  audit: 'Clean (FY24)',
  csr1: 'Filed',
  flags: [
    { sev: 'H', text: 'High severity flag description' },
    { sev: 'M', text: 'Medium severity flag description' }
  ],                         // empty array [] = no flags
  lat: 12.97,                // latitude (for map dot)
  lon: 77.59,                // longitude (for map dot)
  sdgs: [
    { g: 4, t: 'p' },       // t: 'p' = primary, 's' = secondary
    { g: 10, t: 's' }
  ]
}
```

**SDG numbers used:** 1 (No Poverty), 2 (Zero Hunger), 3 (Good Health), 4 (Quality Education), 5 (Gender Equality), 8 (Decent Work), 10 (Reduced Inequalities), 11 (Sustainable Cities), 15 (Life on Land), 17 (Partnerships)

---

## Evaluation dimensions & default weights

| # | Dimension | Default weight |
|---|-----------|---------------|
| 1 | Governance & Compliance | 20% |
| 2 | Programme Quality | 25% |
| 3 | Financial Health | 20% |
| 4 | M&E Capacity | 20% |
| 5 | Mission Alignment | 10% |
| 6 | Partnership Readiness | 5% |

Weights are fully adjustable in-tool (Step 3 slider panel). Must sum to 100.

**Scoring thresholds:**
- ≥ 8.0 → **Selected** (green)
- 7.0 – 7.9 → **Conditional** (amber) — subject to MOU conditions
- < 7.0 or any High flag → **Not recommended** (red)

---

## Tech stack

| Component | Library |
|-----------|---------|
| Map | D3 v7 + TopoJSON v3 (India state boundaries from datamaps CDN) |
| Charts | Chart.js 4.4 |
| Icons | Tabler Icons webfont |
| Fonts | DM Sans · DM Mono · Playfair Display (Google Fonts) |
| Framework | Vanilla HTML/CSS/JS — zero build step, zero npm |

Dark mode: not applicable (fixed vintage yellow palette by design).

---

*Built by Astha Deep · M&E & CSR Advisory · FY 2025–26*
