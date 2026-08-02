# UIX-05 — Audit Log

**Mockup:** `audit-log.html` · **Status:** Planned
**Requirements:** [SEC-05](../docs/SEC-05-architecture.md) rule 9 ("All AI work is audited"), [SEC-02](../docs/SEC-02-principles.md) traceability, [SEC-08](../docs/SEC-08-steps.md) item 8

## Purpose

The complete record of every AI output and every human action on it: who reviewed, what was edited, what was accepted or rejected, and how long people spent assessing and refining. This is the raw data behind the CEO/CTO metrics page.

## Primary users

CTO/architect (governance), BA (correction playbook), leadership (spot checks). Read-only for everyone.

## Layout

Filter bar above a dense data table, with an expandable detail drawer per row.

```
┌ sidebar ┬──────────────────────────────────────────────┐
│         │ topbar                                       │
│         │ filters: date ▾ agent ▾ action ▾ reviewer ▾  │
│         │ ┌──────────────────────────────────────────┐ │
│         │ │ time · agent · output · action · reviewer│ │
│         │ │       · review time · edit distance      │ │
│         │ │ ▸ expandable row → full event detail:    │ │
│         │ │   prompt used, sources, before/after     │ │
│         │ │   diff, rejection reason                 │ │
│         │ └──────────────────────────────────────────┘ │
│         │ pagination · export CSV                      │
└─────────┴──────────────────────────────────────────────┘
```

## Event types logged

| Event | Recorded fields |
|---|---|
| AI draft created | Agent, prompt template id, sources cited, workflow item |
| Human reviewed | Reviewer, role, time spent |
| Human edited | Editor, edit distance (chars/sections changed), before/after |
| Approved | Approver, role, timestamp → item becomes source of truth |
| Rejected | Rejecter, required reason (feeds correction playbook) |
| Pushed to system | Target (Jira/Figma/Git), items created, n8n run id |
| AI suggestion on locked item | Suggestion stored separately — original untouched (SEC-05 rule 11) |

## Key components

- Action chips with status colors: created (neutral) / approved (good) / edited (accent) / rejected (critical) / pushed (good)
- Tabular numerals for time and edit-distance columns
- Detail drawer showing prompt, cited sources, and a before/after diff
- Export for the quarterly governance review (SEC-08 item 10)
