# Project Instructions

## Skills

All reusable skill files live in the [skeels/](skeels/) folder.

| Skill | File | Purpose |
|---|---|---|
| Dashboard Design | [skeels/Dashboard_creation.md](skeels/Dashboard_creation.md) | Layout patterns, KPI cards, charts, data tables |
| Web Search | [skeels/data_web_serach.md](skeels/data_web_serach.md) | Search web for latest docs and articles |
| HTML to PNG | [skeels/html_to_png.md](skeels/html_to_png.md) | Export any HTML file to high-quality PNG via Puppeteer |

---

## Dashboard Design

> Skill: [skeels/Dashboard_creation.md](skeels/Dashboard_creation.md)

Defines the **visual and structural patterns** to follow in every dashboard:

- **Layout** — Standard Admin Dashboard: sticky header + sidebar + main content area
- **KPI Cards** — Top row, 4 columns on large screens (`KPICard` component spec)
- **Chart Cards** — `ChartCard` wrapper with clear titles and consistent time ranges
- **Data Tables** — Searchable + paginated (`DataTable` pattern)
- **Real-time** — WebSocket connection + animated ping live indicator
- **Responsive grid** — 12-column system with sm/md/lg breakpoints
- **Best practices** — 5-second rule, above-the-fold critical data, progressive disclosure

Read this skill before designing any layout, component, or widget.

---

## Dashboard Creation

> Output: a single self-contained `.html` file

Rules for generating the actual HTML dashboard file:

1. **Self-contained** — all CSS and JS inline; only CDN allowed is Chart.js
2. **Dark/light mode** — CSS variables + toggle button
3. **Distinctive aesthetics** — bold unique typography, strong color palette, micro-animations
4. **No generic AI look** — no Inter/Roboto, no purple-on-white gradients, no cookie-cutter layouts
5. **Mock data** — realistic sample data so the dashboard renders immediately
6. **Charts** — use Chart.js (CDN) for all chart rendering

### Creation Workflow

When asked to build a dashboard:

1. Read [skeels/Dashboard_creation.md](skeels/Dashboard_creation.md) for layout and component patterns
2. If real or live data is needed → run the Web Search skill first (see below)
3. Apply frontend-design aesthetics (unique fonts, color direction, animations)
4. Output a single `.html` file
5. Must include: KPI cards row · at least 2 charts · data table · sidebar nav

---

## Web Data Search

> Skill: [skeels/data_web_serach.md](skeels/data_web_serach.md)

Use whenever a task needs live data, external docs, or API information.

```bash
bun skeels/scripts/search.ts <query>
```

**Query tips:**
- Use 2–4 keywords for best results
- Include the library / language / framework name

Use search results to populate dashboard data, verify API shapes, or fetch latest documentation before generating output.
