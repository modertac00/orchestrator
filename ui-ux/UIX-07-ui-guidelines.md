# UIX-07 — Shared UX Guidelines

Cross-cutting rules every Moderta Orchestrate screen must follow. These translate the system requirements into UI behavior.

## 1. Human-in-the-loop is visible, always

*From [SEC-02](../docs/SEC-02-principles.md) principle 1 and [SEC-08](../docs/SEC-08-steps.md) item 4.*

- Every AI output renders with a **draft state** until a human acts — never presented as finished work.
- Approve / Edit / Reject actions are present wherever AI output is displayed.
- The pending-approvals count is visible in the sidebar on every page.
- Agents are always shown **paired with their human role** (Atlas + BA, Ada + QA…), never as autonomous actors.

## 2. Source-of-truth lock

*From [SEC-05](../docs/SEC-05-architecture.md) rule 11.*

- Once approved, an item shows a lock and the pill "✓ Approved · source of truth".
- Locked content is visually read-only; AI suggestions on locked items appear in a clearly separated "AI suggestion" panel, never inline edits.

## 3. Traceability on every output

*From [SEC-02](../docs/SEC-02-principles.md) principle 4.*

Every AI output view shows: which agent, which prompt template, which sources/inputs, and which workflow item it belongs to. No orphan outputs.

## 4. Status display discipline

- Status is never conveyed by color alone — always **dot + icon + label** (works for color-blind users, print, forced-colors mode).
- Status colors (good/warning/serious/critical) are reserved; UI accents use the brand green.
- Meaning is consistent everywhere: warning = waiting on a human, critical = overdue/rejected/blocked, good = approved/active, neutral = planned/idle.

## 5. Action hierarchy

- One primary (green) action per view — the "move work forward" action.
- Destructive/negative actions (Reject, Delete) use the danger style and require a reason or confirmation.
- Buttons state what happens: "Push to Jira", "Approve as source of truth" — not just "OK".

## 6. Accessibility baseline

- Text contrast ≥ 4.5:1 on its surface in both light and dark mode.
- All interactive elements reachable by keyboard; focus states visible.
- Tables for any data also shown as charts; `tabular-nums` for aligned numeric columns.
- Semantic HTML in mockups (`aside`, `main`, `nav`, `table`) so structure survives into the real build.

## 7. Language

- Plain language, no ML jargon (the requirements are written for the whole team — so is the UI).
- Agents are named (Gaia, Atlas, Ada, Mira, Uncle Bob, Leonidas) with their role always shown alongside.
- Timestamps as relative age ("2h ago") in queues, absolute dates in the audit log.

## 8. Mockup conventions (this repo)

- One HTML file per screen, all linking `styles.css`; no JavaScript unless a mockup interaction demands it.
- Every page carries the footer note "Static HTML/CSS mockup · no live data".
- Realistic sample data (EcoTrace carbon-reporting initiative) so reviews test real content shapes, not lorem ipsum.
