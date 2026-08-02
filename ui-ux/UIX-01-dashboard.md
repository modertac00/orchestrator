# UIX-01 — Delivery Dashboard

**Mockup:** `index.html` · **Status:** ✅ Built
**Requirements:** [SEC-02](../docs/SEC-02-principles.md) (human-in-the-loop), [SEC-05](../docs/SEC-05-architecture.md) (pipeline, agents), [SEC-07](../docs/SEC-07-roadmap.md) (phase states)

## Purpose

The landing view for everyone on the team. Answers three questions in one glance:

1. What is waiting on **me** (human approvals)?
2. Where is work in the **delivery pipeline**?
3. What are the **agents** doing right now?

## Primary users

All roles — BA, Research Assistant, UI/UX, engineers, QA, architect, leadership. The approval queue adapts to the signed-in role (mockup shows a BA view).

## Layout

```
┌ sidebar ┬──────────────────────────────────────────┐
│ brand   │ topbar: breadcrumb · new item · user     │
│ overview│ page head: initiative name · CTA buttons │
│ agents  │ [stat][stat][stat][stat]                 │
│ delivery│ [ pipeline stepper — 6 stages ]          │
│ footer  │ [ awaiting review ]  [ agent cards ]     │
└─────────┴──────────────────────────────────────────┘
```

## Key components

- **Stat tiles (4):** pending human approvals, active workflow items, AI drafts this week (accepted / edited / rejected split — the SEC-02 measurement principle), average human review time.
- **Pipeline stepper:** Research (Gaia+RA) → Requirements (Atlas+BA) → UI/UX (Mira+Design) → Development (Uncle Bob+Devs) → QA (Ada+QA) → Security (Leonidas+Arch). Each stage names the **agent + human pair** — never an agent alone. A highlighted stage marks where attention is needed.
- **Awaiting your review queue:** each row shows agent badge, output title, provenance (which research note / requirement it came from — SEC-02 traceability), age, status pill, Review button. Overdue items (>24h) escalate to critical.
- **Agent status cards (6):** role description, status pill (Active / Pilot / Planned per roadmap phase), queue depth, runs today.

## States

| State | Display |
|---|---|
| Agent active | Good pill "✓ Active" + green sidebar dot |
| Agent in pilot | Warning pill "⚠ Pilot" |
| Agent planned (Phase 4) | Neutral pill "— Planned", muted sidebar dot |
| Review pending | Warning pill "⚠ Needs review" |
| Review overdue >24h | Critical pill "✕ Overdue 24h+" |

## Design decisions

- The sidebar footer states the operating principle ("AI proposes — people approve") so the human-in-the-loop rule is visible on every page.
- Approval count badges in the nav keep pending human work impossible to miss.
- No AI output is ever shown as "done" — only as draft/needs-review until a human acts.
