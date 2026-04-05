# FinLens — Financial Intelligence Dashboard

A stunning, fully functional finance dashboard UI built as a frontend internship assignment. Inspired by the design aesthetics of [davidlangarica.dev](https://www.davidlangarica.dev/) and [Shopify Editions Winter '26](https://www.shopify.com/editions/winter2026).

---

## 🚀 Live Preview

Open `index.html` directly in **Google Chrome** (full screen recommended). No build step required — it's a single self-contained HTML file.

---

## ✨ Features

### Design & Animations
- **Cinematic loader** — animated counter 0→100% with phase messages, exactly like David Langarica's "Heading to my universe..." screen
- **Live particle canvas** — 55 floating particles with connecting lines, 5 ambient orbs that react to mouse position in real time (violet, pink, cyan, lime, amber)
- **Custom magnetic cursor** — dual-ring cursor with `mix-blend-mode:difference`, expands on hover
- **3D card tilt** — every card responds to mouse position with `perspective(900px) rotateX/Y` transforms
- **Magnetic buttons** — Add Transaction button follows mouse with elastic spring-back via GSAP
- **Word-clip hero animation** — "YOUR MONEY, REDEFINED." slides up character-by-character with `skewY` ease
- **Rotating subtitle** — "Financial [Intelligence / Analytics / Dashboard] Platform" cycles with CSS keyframes
- **Marquee ticker** — scrolling data strip with live values
- **Double-text scrolling** — giant outlined text (TRANSACTIONS / INSIGHTS / ANALYTICS) scrolls horizontally per section
- **Shimmer sweep** — diagonal light sweep on card hover
- **GSAP ScrollTrigger** — cards stagger in as sections scroll into view
- **Parallax section numbers** — 01/02/03/04 drift on scroll
- **Section number animations** — large ghost numbers parallax independently

### Dashboard Pages

#### 1. Overview
- 4 KPI stat cards (Balance, Income, Expenses, Savings Rate) with animated count-up
- Balance Trend line chart (12-month)
- Spending Mix donut chart with legend
- Recent Activity table (last 5 transactions)

#### 2. Transactions
- Full sortable, filterable, searchable transaction ledger
- Filter by type (Income/Expense) and category
- Sort by date or amount
- Pagination (9 per page)
- **CSV Export** (fixed with BOM for Excel compatibility)
- Add/Delete transactions (Admin only)

#### 3. Insights
- Top spending category with animated fill bar
- Savings rate with motivational context
- Average transaction value
- Biggest single expense
- Monthly comparison bar chart (6 months)
- Category breakdown with animated horizontal bars

#### 4. Analytics
- Net cash flow area chart (12-month)
- Expense distribution radar chart
- Income sources donut chart
- Spending heatmap (daily intensity grid for March)

### Role-Based UI
- **Admin**: Full access — can Add and Delete transactions, sees all actions
- **Viewer**: Read-only — Add/Delete buttons hidden, no action column
- Toggle via the role dropdown in the top navigation

### State Management
- All transaction data persisted to `localStorage` (key: `FLX`)
- Survives page refresh
- Synced across all pages instantly

---

## 🛠 Technical Stack

| Technology | Usage |
|---|---|
| Vanilla JS (ES6+) | All logic, state, data |
| GSAP 3.12 + ScrollTrigger | Loader exit, card reveals, parallax |
| Chart.js 4.4 | All 6 charts (line, bar, doughnut, radar) |
| HTML5 Canvas | Particle + orb ambient background |
| CSS Custom Properties | Design tokens, theming |
| Bebas Neue | Display / heading font |
| Bricolage Grotesque | Body / UI font |
| DM Mono | Data / monospace font |
| localStorage | Data persistence |

---

## 📂 File Structure

```
finlens/
├── index.html      ← Complete self-contained app (CSS + JS + HTML)
└── README.md       ← This file
```

---

## 🐛 Bugs Fixed in This Version

1. **Charts blank on Insights/Analytics pages** — Charts now build lazily when sections are scrolled to OR navigated to via nav pills, solving the issue where hidden canvases had zero dimensions
2. **Insights showing ₹0** — `bInsights()` was only called from nav button clicks, not from scroll events; now called via `ensureInsights()` on both triggers
3. **CSV export broken** — Rewrote using `Blob` + `URL.createObjectURL()` + `document.body.appendChild(a)` — fully compatible with all browsers; added UTF-8 BOM for Excel
4. **Alignment issues** — Fixed `tamt.xp` color (was same as background), corrected `.kv.gold` → `.kv.vio` for savings rate card, fixed stats strip with proper `opacity` transition
5. **Heatmap blank** — Same lazy-build fix as charts
6. **Nav active state wrong** — Section indices were off-by-one; `uNav()` now correctly maps scroll position to nav pill highlights
7. **Category bars not animating** — Fixed timing with double `requestAnimationFrame` to ensure DOM is painted before width transition fires
8. **Delete button color** — Expense amounts now correctly show in red (`#f87171`) not white

---

## 💡 Design Decisions

- **Single file** — No build toolchain required for evaluation. Paste-and-run.
- **Scroll snapping** — `scroll-snap-type:y mandatory` gives each section a cinematic full-viewport feel
- **Dark palette** — `#05050c` near-black base with warm grain noise overlay, matching premium fintech aesthetics
- **Lime accent** — `#c8ff00` chosen for maximum contrast on dark backgrounds while reading as "positive/growth"
- **No external images** — All visuals are CSS/Canvas/SVG

---

## 📋 Assignment Requirements Checklist

| Requirement | Status |
|---|---|
| Dashboard Overview (Balance, Income, Expenses) | ✅ |
| Time-based visualization (Balance Trend chart) | ✅ |
| Categorical visualization (Spending Mix donut) | ✅ |
| Transactions list with Date, Amount, Category, Type | ✅ |
| Filtering (by type, category) | ✅ |
| Sorting (by date, amount) | ✅ |
| Search | ✅ |
| Role-based UI (Admin vs Viewer) | ✅ |
| Insights section (top category, monthly comparison, etc.) | ✅ |
| State management (localStorage persistence) | ✅ |
| Responsive design | ✅ |
| Clean, readable UI | ✅ |
| Empty/no-data handling | ✅ |
| Dark mode | ✅ (default) |
| CSV Export | ✅ |
| Animations & transitions | ✅ (extensive) |

---

## 🎨 Optional Enhancements Implemented

- ✅ Dark mode (default theme)
- ✅ Data persistence (localStorage)
- ✅ Export functionality (CSV with BOM)
- ✅ Advanced filtering & sorting
- ✅ Animations & transitions (GSAP, CSS)
- ✅ Custom cursor
- ✅ 3D card tilt effects
- ✅ Magnetic button physics
- ✅ Particle background system
- ✅ Scroll-snapped full-viewport sections

---

*FinLens © 2026 — Built with passion for the frontend internship assignment.*
