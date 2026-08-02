# UIX-02 — Atlas Workflow (Phase 1 MVP)

**Mockup:** `atlas.html` · **Status:** ⏳ Next to build
**Requirements:** [SEC-07](../docs/SEC-07-roadmap.md) Phase 1, [SEC-08](../docs/SEC-08-steps.md) item 5 (first MVP workflow), [SEC-05](../docs/SEC-05-architecture.md) (BA + Atlas)

## Purpose

The heart of Phase 1. Walks a BA through the MVP flow:

> research input → Atlas draft requirements → HTML/CSS mockup → acceptance criteria → BA refinement → Jira task breakdown

## Primary users

Business Analyst (owner). Research Assistant provides input; developers review output feasibility.

## Layout

A **stepper page**: horizontal step indicator at top, one active step panel below, context rail on the right.

```
┌ sidebar ┬──────────────────────────────────────────────┐
│         │ topbar                                       │
│         │ ① Input → ② Draft req → ③ Mockup →           │
│         │ ④ Acceptance criteria → ⑤ Jira breakdown     │
│         │ ┌──────────────────────────┬───────────────┐ │
│         │ │ active step workspace    │ context rail: │ │
│         │ │ (editor / preview)       │ sources,      │ │
│         │ │                          │ audit trail,  │ │
│         │ │ [Reject] [Edit] [Approve]│ prompt used   │ │
│         │ └──────────────────────────┴───────────────┘ │
└─────────┴──────────────────────────────────────────────┘
```

## Steps

| Step | Content | Human gate before next step |
|---|---|---|
| 1. Research input | Paste/upload research notes, or pick an approved Gaia note (Phase 3) | BA confirms input scope |
| 2. Draft requirements | Atlas output: problem, user stories, flows, assumptions, open questions — editable | BA edits + approves |
| 3. HTML/CSS mockup | Atlas-generated mockup in an iframe preview with viewport toggle | BA approves direction |
| 4. Acceptance criteria | Given/When/Then list per story, editable, Ada test-case hints | BA approves |
| 5. Jira breakdown | Epic → stories → subtasks tree with estimates placeholder | BA approves → n8n creates Jira items |

## Key components

- Step indicator with per-step state: done ✓ / active / locked
- Draft banner on every AI output: "Draft — Atlas · not approved" (warning tint)
- Approve / Edit / Reject action bar (SEC-09: review, approve, reject, edit, comment actions)
- Context rail: source citations (SEC-02 traceability), the prompt template used, and a mini audit trail (who did what, when)
- Source-of-truth lock: after BA approval a step becomes read-only for AI, marked with a lock + "Human approved — source of truth" pill (SEC-05 rule 11)

## States

| State | Display |
|---|---|
| AI draft | Warning pill "⚠ Draft — needs review" |
| Human edited | Accent pill "✎ Edited by BA" |
| Approved / locked | Good pill "✓ Approved · source of truth" + lock icon |
| Rejected | Critical pill "✕ Rejected" + reason field |
