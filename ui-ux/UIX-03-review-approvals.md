# UIX-03 — Review & Approvals

**Mockup:** `review.html` · **Status:** Planned
**Requirements:** [SEC-02](../docs/SEC-02-principles.md) principle 1, [SEC-08](../docs/SEC-08-steps.md) item 4 (approval gates), [SEC-05](../docs/SEC-05-architecture.md) rules 9 & 11

## Purpose

The single human approval gate for **all** agent output. Whatever an agent produces — requirement, mockup, test cases, code suggestion, design comment, security finding — lands here as a draft and cannot move forward until a human acts.

## Primary users

Every role reviews their own domain: BA reviews Atlas output, QA reviews Ada, engineers review Uncle Bob, UI/UX reviews Mira, architect reviews Leonidas, RA reviews Gaia.

## Layout

Master–detail: filterable queue on the left, selected item detail on the right.

```
┌ sidebar ┬──────────────────────────────────────────────┐
│         │ topbar                                       │
│         │ filters: agent ▾ · type ▾ · age ▾ · mine     │
│         │ ┌───────────────┬──────────────────────────┐ │
│         │ │ queue list    │ detail: output preview   │ │
│         │ │ (rows w/      │ diff vs previous version │ │
│         │ │ agent badge,  │ sources + prompt used    │ │
│         │ │ status, age)  │ comments thread          │ │
│         │ │               │ [Reject][Edit][Approve]  │ │
│         │ └───────────────┴──────────────────────────┘ │
└─────────┴──────────────────────────────────────────────┘
```

## Key components

- **Queue row:** agent badge, output type chip, title, provenance line, age, status pill
- **Detail header:** what this is, which workflow item it belongs to, who is the required approver role
- **Preview area:** rendered output (document, mockup iframe, test case table, code block)
- **Edit mode:** inline editing; edits are tracked and displayed as "human edit distance" later (SEC-02 measure principle)
- **Comment thread:** cross-role discussion (SEC-09 item 1 — BA, UI/UX, engineering, QA, architecture refine together)
- **Action bar:** Approve (primary green) · Edit · Comment · Reject (danger, requires reason)
- **Review timer:** time spent reviewing is recorded for the audit log and metrics (SEC-05 rule 9)

## Rules surfaced in the UI

1. Approve marks the item as **source of truth** — a lock appears; AI can no longer modify it, only suggest separately.
2. Reject requires a reason — reasons feed the prompt/correction playbook (SEC-08 item 8).
3. Items show their required approver role; approval by the wrong role is disabled with an explanatory tooltip.
