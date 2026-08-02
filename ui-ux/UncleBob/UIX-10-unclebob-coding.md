# UIX-10 — Uncle Bob Coding Studio

**Mockup:** `UncleBob/unclebob.html` · **Status:** ✅ Built (basic first version)
**Requirements:** [SEC-05](../../docs/SEC-05-architecture.md) (Development + Git + Uncle Bob; §11 human-approved work is locked), [SEC-09](../../docs/SEC-09-suggestions.md) (architect owns approval), [SEC-07](../../docs/SEC-07-roadmap.md)

## Purpose

Uncle Bob is the **coding agent** — sample code, branch support, code quality, and code review.
His studio has **two sections** (tabs) plus an always-visible chat:

1. **Architecture design** — an interactive **SVG knowledge map**, not a full diagramming tool.
   - Nodes are **repos, AWS infrastructure, and external services** of the real ESM system
     (esm-frontend, esm-api, esm-reporting-api/-frontend/-core, mint-design-system, PostgreSQL,
     S3, Supabase, Mint AI, …), each carrying an **evidence status** from scanning the repos:
     `verified` (solid green), `partial` (amber), `planned` (dashed amber — code exists but not
     wired), `unknown` (dashed gray — no implementation evidence).
   - Edges are typed connections (REST, SDK, database, npm package, navigation) with the same
     evidence statuses and arrow markers.
   - **Interactive:** selecting a node (click or keyboard) highlights its direct incoming and
     outgoing connections, dims the rest, and opens a detail panel; clicking the background
     clears the selection.
   - Every component carries its own **section code `ARC-01`…`ARC-16`** (shown on the tile,
     usable in chat to request changes) plus a **description** and **implementation details**
     (modules, routes, env vars) — all rendered in the detail panel on selection.
   - The architecture has **levels** (C4-style): L1 system context, L2 services & infrastructure
     (the default, populated view), L3 components.
   - The map is edited **through chat**: ask Uncle Bob to add / connect / re-verify components;
     changes land as drafts until the architect approves, and statuses update on re-scan.
2. **Technical designs** — plain **HTML documents** stored in a designs repo (no special tooling).
   Uncle Bob drafts and edits them via chat; each design links back to the architecture tiles it
   covers. Once a human approves a design it is **locked** — AI may only propose separate
   suggestions (SEC-05 §11).

The chat (BOB-07) is the single editing surface for both sections — the UI itself stays read-mostly.

## Section codes (visible in the UI)

| Code | Section | Tab |
|---|---|---|
| BOB-01 | Sidebar navigation | — |
| BOB-02 | Topbar | — |
| BOB-03 | Page header | — |
| BOB-04 | Section tabs (architecture / technical designs) | — |
| BOB-05 | Architecture designer (level selector L1–L3, interactive knowledge map, detail panel, evidence legend) | Architecture |
| BOB-06 | Technical designs (HTML documents: draft → in review → approved · locked) | Technical designs |
| BOB-07 | Uncle Bob Assistant chat (always visible) | Both |

## Later (not in this basic version)

- L1 / L3 level views rendered (level selector is present but only L2 is populated)
- Per-node drill-down (branches, open PRs, sample code, review checklist) beyond the connection list
- Node search / filter over the `data-search` text each node already carries
- Diagram export and repo/AWS re-scan are mocked buttons
