# UIX-06 — Leadership Metrics (CEO/CTO Dashboard)

**Mockup:** `metrics.html` · **Status:** Planned
**Requirements:** [SEC-11](../docs/SEC-11-next-documents.md) item 6, [SEC-05](../docs/SEC-05-architecture.md) rule 10, [SEC-02](../docs/SEC-02-principles.md) measure & improve

## Purpose

Gives CEO/CTO the visibility the requirements demand: where AI is helping, where it is failing, how much human review time it costs, and whether quality is improving.

## Primary users

CEO, CTO, architect; delivery leads for the quarterly governance review (SEC-08 item 10).

## Metrics (from SEC-11)

| Metric | Form |
|---|---|
| Time saved (estimated) | Stat tile + trend line |
| Employee review time | Stat tile + per-agent bar chart |
| Edit rate (drafts needing human edits) | Stat tile + trend line |
| Rejection rate | Stat tile + trend line |
| Quality score | Stat tile + per-agent comparison |
| Incident rate | Stat tile; incidents listed |
| AI failure patterns | Table of repeated corrections, grouped by agent + prompt |

## Layout

```
┌ sidebar ┬──────────────────────────────────────────────┐
│         │ topbar · date-range filter (7/30/90 days)    │
│         │ [tile][tile][tile][tile][tile][tile]         │
│         │ [ review time by agent ] [ edit rate trend ] │
│         │ [ acceptance funnel     ] [ failure patterns │
│         │                            table            ]│
└─────────┴──────────────────────────────────────────────┘
```

## Chart rules (binding for this page)

1. Charts follow the shared dataviz method: form first, color last.
2. Categorical palette (per-agent series) must be **validated** with the palette validator before shipping — CVD-safe in light and dark mode.
3. One axis per chart — never dual-axis; two measures = two charts.
4. Legend present for ≥2 series; direct labels where space allows; values never colored by series hue.
5. Every chart offers a table view (accessibility + export).
6. Status colors are reserved for status; agent series use categorical slots.

## Key components

- Six stat tiles with period-over-period deltas (green ▲/▼ where the direction is good)
- Review-time-by-agent horizontal bars; acceptance funnel (accepted / edited / rejected)
- Failure-patterns table: correction theme, agent, occurrences, example, owner
- Date-range presets: 7 / 30 / 90 days, quarter-to-date
