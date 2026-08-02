# UIX-04 — Jira Breakdown

**Mockup:** `jira-breakdown.html` · **Status:** Planned
**Requirements:** [SEC-05](../docs/SEC-05-architecture.md) (Atlas + Jira), [SEC-08](../docs/SEC-08-steps.md) item 5, [SEC-07](../docs/SEC-07-roadmap.md) Phase 1

## Purpose

Shows how an approved requirement becomes delivery structure: epic → stories → subtasks → QA tasks, with acceptance criteria and estimates — before n8n pushes anything to Jira. This is the last checkpoint between AI-drafted structure and real Jira tickets.

## Primary users

BA (owner of Jira readiness — SEC-09 roles), developers (estimates, feasibility flags), QA lead (QA task coverage).

## Layout

```
┌ sidebar ┬──────────────────────────────────────────────┐
│         │ topbar                                       │
│         │ requirement header: REQ-029 · ✓ approved     │
│         │ sync banner: "Not yet in Jira" [Push to Jira]│
│         │ ┌──────────────────────────────────────────┐ │
│         │ │ ▸ EPIC ECO-01 Supplier emissions intake  │ │
│         │ │   ▸ Story ECO-110 (5 pts?) [AC: 4]       │ │
│         │ │     · subtask FE form                    │ │
│         │ │     · subtask API endpoint               │ │
│         │ │     · QA task (Ada: 14 test cases)       │ │
│         │ │   ▸ Story ECO-111 …                      │ │
│         │ └──────────────────────────────────────────┘ │
└─────────┴──────────────────────────────────────────────┘
```

## Key components

- **Requirement header:** source requirement with its approval state and link back to the Atlas workflow run that produced this breakdown
- **Tree view:** collapsible epic → story → subtask hierarchy; each node shows type chip, title, estimate field (developer-owned — AI never fills final estimates), acceptance-criteria count, linked Ada test cases
- **Feasibility flags:** developers can mark a story "⚠ technical risk" or "✕ not feasible" with a note — the SEC-05 step 4 review
- **Sync state banner:** Draft (not in Jira) → Pushed (with Jira keys linked) → Drift detected (Jira changed after push)
- **Push to Jira action:** primary button, disabled until BA approval; explains what n8n will create

## States

| State | Display |
|---|---|
| Breakdown draft | Warning pill "⚠ Draft — BA review needed" |
| BA approved, not pushed | Accent pill "Ready for Jira" + enabled push button |
| Pushed to Jira | Good pill "✓ In Jira" + ticket keys as links |
| Developer risk flag | Serious pill "⚠ Technical risk" on the node |
