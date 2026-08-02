# UIX-08 — Gaia Research Workspace

**Mockup:** `gaia.html` · **Status:** Planned (Phase 2 build)
**Requirements:** [SEC-07](../docs/SEC-07-roadmap.md) Phase 2 (Gaia parallel build), [SEC-05](../docs/SEC-05-architecture.md) step 1 (research starts the flow) and "Research Assistant + Gaia" pairing, [SEC-02](../docs/SEC-02-principles.md) traceability, [SEC-09](../docs/SEC-09-suggestions.md) item 7 (research stays in draft until human approval)

## Purpose

Gaia's dedicated workspace: where sustainability research is requested, drafted, source-checked, and approved. The output — an approved, source-backed research note — is the input that feeds Atlas in Phase 3.

Gaia covers (from SEC-07 Phase 2):

- Sustainability research and topic summaries
- Competitor and regulation summaries
- Customer problem analysis
- Source-backed research notes

## Primary users

**Research Assistant (owner)** — owns research quality, sustainability context, and source validation (SEC-09 roles). Product lead and BA read approved notes; the BA pulls them into Atlas.

## Workflow

> Research request → Gaia drafts a source-backed note → RA validates sources and edits → RA approves → note is locked as source of truth → available to Atlas

Human gate: **nothing leaves draft state without RA approval** — a Gaia note can never flow into Atlas while unapproved.

## Layout

Master–detail: research library on the left, selected note on the right with a dedicated sources panel.

```
┌ sidebar ┬──────────────────────────────────────────────┐
│         │ topbar                                       │
│         │ page head: Gaia · Research library           │
│         │            [＋ New research request]         │
│         │ filters: topic ▾ · type ▾ · status ▾         │
│         │ ┌──────────────┬───────────────────────────┐ │
│         │ │ note library │ note detail               │ │
│         │ │ R-016 draft  │ title · type · status     │ │
│         │ │ R-015 draft  │ ┌───────────────────────┐ │ │
│         │ │ R-014 ✓      │ │ summary / findings    │ │ │
│         │ │ R-013 ✓      │ │ (editable in review)  │ │ │
│         │ │ R-012 ✕      │ └───────────────────────┘ │ │
│         │ │              │ sources panel [1][2][3]…  │ │
│         │ │              │ [Reject] [Edit] [Approve] │ │
│         │ └──────────────┴───────────────────────────┘ │
└─────────┴──────────────────────────────────────────────┘
```

## Key components

- **New research request form:** topic, research type (market / regulation / competitor / customer problem), guiding questions, scope notes — this becomes the recorded input for traceability.
- **Research library list:** note id (R-###), title, type chip, status pill, age, "used by" indicator when a requirement was built from it (e.g. "→ REQ-031").
- **Note detail:** Gaia's structured draft — summary, key findings, risks/opportunities, open questions. Editable while in review.
- **Sources panel:** every claim cites a numbered source; each source row shows title, link, date accessed, and an RA validation checkbox ("verified ✓"). A note **cannot be approved until every source is verified** — the SEC-09 risk control made physical in the UI.
- **Inline citation markers:** findings reference sources as [1], [2] so the RA can spot-check claim-by-claim.
- **Action bar:** Approve (primary) · Edit · Reject (danger, reason required).
- **Handoff card (on approved notes):** "Send to Atlas as requirement input" — visible only after approval, linking Phase 2 output to the Phase 3 pipeline.

## States

| State | Display |
|---|---|
| Requested | Neutral pill "— Queued for Gaia" |
| Gaia draft | Warning pill "⚠ Draft — RA review needed" |
| Sources partially verified | Warning pill "⚠ 3/6 sources verified"; Approve disabled |
| Approved | Good pill "✓ Approved · source of truth" + lock; handoff card appears |
| Rejected | Critical pill "✕ Rejected" + reason (feeds correction playbook) |
| Consumed by Atlas | Accent pill "→ Used in REQ-031" linking to the requirement |

## Design decisions

- Source verification is a blocking checklist, not a suggestion — unverified research physically cannot become requirement input.
- The library keeps rejected notes visible (grayed) because rejection reasons feed the prompt playbook (SEC-08 item 8).
- Research notes are never edited by AI after approval; Gaia updates arrive as a **new linked note version**, keeping the approved original intact (SEC-05 rule 11).

## Section codes (visible in the UI)

Use these codes to request changes to a specific part of `gaia.html` — each is an `id` on the element and shown as a small tag in the UI.

| Code | Section |
|---|---|
| GAIA-01 | Sidebar navigation |
| GAIA-02 | Topbar (breadcrumb + user) |
| GAIA-03 | Page header + new research request action |
| GAIA-04 | Library filters |
| GAIA-05 | Research library (research groups → documents) |
| GAIA-06 | Draft status banner |
| GAIA-07 | Note header (title, type, status, provenance) |
| GAIA-08 | Summary |
| GAIA-09 | Key findings |
| GAIA-10 | Risks & opportunities |
| GAIA-11 | Open questions for the BA |
| GAIA-12 | Sources panel (verification checklist) |
| GAIA-13 | Action bar (approve / edit / reject) |
| GAIA-14 | Gaia Assistant chat (section updates + research tools) |
| GAIA-15 | Related papers (find + keep) |
| GAIA-16 | Knowledge base (kept items, RAG context) |
| GAIA-17 | Document editor toolbar (formatting, insert link, attach, export PDF) |
