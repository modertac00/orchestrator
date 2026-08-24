# UIX-08 — Moderta AI Research Workspace (Gaia)

**Mockup:** `gaia.html` · **Status:** Planned (Phase 2 build) · extended for the Research Workspace BRD, 24 Aug 2026
**Requirements:** [SEC-07](../docs/SEC-07-roadmap.md) Phase 2 (Gaia parallel build), [SEC-05](../docs/SEC-05-architecture.md) step 1 (research starts the flow) and "Research Assistant + Gaia" pairing, [SEC-02](../docs/SEC-02-principles.md) traceability, [SEC-09](../docs/SEC-09-suggestions.md) item 7 (research stays in draft until human approval), Research Workspace BRD BR-001 … BR-076

## Purpose

Gaia's dedicated workspace: where research is requested, drafted, source-checked, and approved. The output — an approved, source-backed research note — is the input that feeds Atlas in Phase 3.

The workspace covers four research types, chosen as the first step of a request (BR-001). Research type drives the workflow, note template, assistant tools, evidence rules and output format; everything else — layout, filters, cards, status pills, assistant rail, approval gate — is shared:

- **🎓 Academic** — journal papers, thesis chapters, conference papers, literature and systematic reviews
- **🏢 Business** — company, strategy, product, customer and competitor research
- **📈 Market** — market sizing, trends, segmentation, forecasting, competitive scans
- **🌱 Sustainability** — regulation, ESG, climate and LCA research (the original Gaia scope, preserved)

Every type produces the same artefact: a source-backed research note that cannot leave draft state without human approval.

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

- **New research request form:** research type first, then shared intake (title, research question, workspace, output format, scope notes) plus the fields that type requires — field of study and citation style for Academic, company and industry for Business, geography and currency for Market, framework and jurisdiction for Sustainability. This becomes the recorded input for traceability.
- **Research library list:** research groups (RS-##) carrying a **research type tag**, documents (D-##) carrying a **document type badge** (literature review, systematic review, research paper, case study, market sizing, survey, patent, financial report, competitor analysis, regulation…), status pill, age, and a "used by" indicator (e.g. "→ Used in Thesis §2.3").
- **Note detail:** Gaia's structured draft, with the **section list supplied by the research type's template** — Academic (research question → references), Business (business context → sources), Market (market definition → forecast), Sustainability (the original summary / findings / risks / open questions). Sections take embedded **data table** and **chart** blocks; charts keep their source references.
- **Sources panel:** every claim cites a numbered source. Each row carries bibliographic metadata (authors, year, journal, DOI, publication type, methodology, sample), peer-review status and citation count for academic sources, a reliability tier (primary data / analyst estimate / press coverage) for business and market sources, an auto-generated highlight summary, an **Ask this source** action, an **evidence classification** (supporting / contradicting / mentioning) and — separately — the RA verification checkbox. A note **cannot be approved until every source is verified**.
- **Systematic review mode (Academic):** include / exclude / uncertain screening decisions with reasons, duplicate detection by DOI, title, author, year and similarity, and PRISMA-style counts.
- **Research intelligence:** evidence matrix with custom columns and accept / edit / reject on AI extractions · synthesis with a consensus indicator and contradiction detection · gap finder · idea lab · market sizing with multi-source triangulation · competitive research.
- **Review before release:** claim-to-citation verification, citation audit, manuscript readiness, integrity check.
- **Action bar:** Approve (primary) · Edit · Reject (danger, reason required) · Export.
- **Export:** PDF / DOCX, spreadsheet for tables and evidence, citation styles (APA, MLA, Chicago, Harvard, IEEE, Vancouver, AMA), reference-manager formats (RIS, BibTeX, CSV), and a full research package (output + evidence + sources + screening decisions + audit).
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
| GAIA-16 | Knowledge base (kept items, RAG context) — tagged by research type, workspace and metadata |
| GAIA-17 | Document editor toolbar (formatting, link, attach, insert table, insert chart, AI draft, style & grammar, export) |
| GAIA-18 | New research request — research type selection + type-specific intake |
| GAIA-19 | Note template / structure switcher (sections follow research type) |
| GAIA-20 | Embedded data table block |
| GAIA-21 | Embedded chart block (keeps source references) |
| GAIA-22 | Systematic review mode — screening decisions, duplicates, PRISMA record |
| GAIA-23 | Evidence matrix (cross-source extraction, custom columns, accept / edit / reject) |
| GAIA-24 | Research synthesis — consensus indicator, contradiction detection, cross-source synthesis |
| GAIA-25 | Research gap finder |
| GAIA-26 | Research idea lab (six evaluation criteria) |
| GAIA-27 | Market & competitive intelligence (market sizing, triangulation, competitor matrix) |
| GAIA-28 | Citation & evidence review (claim-to-citation verification, citation audit) |
| GAIA-29 | Publication (journal finder, fit analysis, manuscript readiness) |
| GAIA-30 | Approve & export (citation styles, export formats, research package, approved-content lock) |
| GAIA-31 | Traceability (source → evidence → finding → output, and the reverse lookup) |
| GAIA-32 | Research integrity & audit log |
| GAIA-33 | Workspace configuration (what is extensible rather than hard-coded) |
| GAIA-34 | Business requirements coverage map (BR-001 … BR-076) |

## Notes on the BRD extension

- The **Draft → Verify sources → Approve** gate, the approved-content lock and audit logging are unchanged and apply identically to all four research types (BR-065 – BR-067).
- Verification ("is this source real and checked?") and evidence classification ("how does it relate to the claim?") are **separate** controls that sit side by side on each source row (BR-017, BR-018).
- Anything Gaia cannot substantiate — a paper, author, DOI, statistic, quotation or finding — is shown in an explicit **"Evidence not verified — requires verification"** state and is blocked from citation and export (BR-072, BR-073).
- Research types, note templates, document types, assistant tools, source classifications, evidence-matrix columns, citation styles, export formats and traceable output types are all registry-driven configuration, not branches in the core workflow (BR-076).
