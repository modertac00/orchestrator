# UIX-00 — Design System

Single source of truth: `styles.css` in the repository root. Every mockup page links this one stylesheet; no page defines its own colors or components.

## Brand direction

Moderta builds sustainability products, so the accent is a **deep green** (`#0e6f4f` light / `#1e9a6e` dark). The overall tone is a calm, professional internal tool: warm off-white surfaces, hairline borders, low shadow, generous whitespace.

## Color tokens

| Role | Light | Dark | Notes |
|---|---|---|---|
| Page background | `#f9f9f7` | `#0d0d0d` | |
| Surface (cards, sidebar) | `#fcfcfb` | `#1a1a19` | |
| Raised surface | `#ffffff` | `#222221` | Buttons, nested cards |
| Primary ink | `#0b0b0b` | `#ffffff` | Headings, values |
| Secondary ink | `#52514e` | `#c3c2b7` | Body, labels |
| Muted ink | `#898781` | `#898781` | Meta text, hints |
| Hairline | `#e1e0d9` | `#2c2c2a` | Borders, dividers |
| Accent (brand green) | `#0e6f4f` | `#1e9a6e` | Primary actions, active nav |
| Accent tint | `#e6f2ed` | `#12291f` | Active nav bg, agent glyphs |

## Status colors (reserved)

Status colors are **never** reused for anything decorative, and never carry meaning by color alone — every status pill pairs a colored dot with an icon character and a text label (SEC-09 accessibility discipline).

| Status | Color | Usage |
|---|---|---|
| Good | `#0ca30c` | Active agent, approved item |
| Warning | `#fab219` | Needs review, pilot state |
| Serious | `#ec835a` | Escalation, at-risk item |
| Critical | `#d03b3b` | Overdue, rejected, blocked |

## Typography

- Font: `system-ui, -apple-system, "Segoe UI", sans-serif` — no display faces
- Page title 20px/650, card title 15px/650, body 14px, meta 12px, uppercase nav labels 11px
- Tabular numerals (`font-variant-numeric: tabular-nums`) only for table columns that align vertically

## Dark mode

Automatic via `prefers-color-scheme` — every token has a dark value; components reference tokens only, never raw hex.

## Core components (in `styles.css`)

| Component | Class | Used for |
|---|---|---|
| App shell | `.shell`, `.sidebar`, `.main`, `.topbar`, `.content` | Every page |
| Card | `.card`, `.card-head`, `.card-body` | Content grouping |
| Stat tile | `.stat-tile` | KPI numbers (dashboard, metrics) |
| Status pill | `.pill` + `good/warning/serious/critical/neutral/accent` | All state display |
| Agent badge | `.agent-badge` | Identifying which agent produced output |
| Pipeline stepper | `.pipeline`, `.stage` | Delivery flow stages |
| List row | `.list`, `.list-row` | Queues (approvals, audit entries) |
| Data table | `table.data` | Structured records |
| Buttons | `.btn`, `.primary`, `.danger`, `.small` | Actions; danger reserved for reject/delete |

## Rules

1. New pages must not introduce new colors — extend tokens in `styles.css` if genuinely needed.
2. Primary (green) button = the single main action per view; everything else is a plain button.
3. `.btn.danger` is reserved for reject/delete actions at approval gates.
4. Icons are lightweight unicode glyphs for mockups; swap for an icon set in the real build.
5. Charts (metrics page) must follow a validated accessible palette — validate before shipping.
