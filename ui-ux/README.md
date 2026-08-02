# Moderta Orchestrate — UI/UX Specifications

UI/UX documentation for the Moderta Orchestrate mockups. Each screen spec maps to one static HTML file in the repository root and traces back to the system requirements in [../docs/](../docs/README.md).

Use the UIX codes (like the SEC codes) when asking AI or team members to update a specific spec.

## Foundation

| Code | Spec | Covers |
|---|---|---|
| UIX-00 | [Design system](UIX-00-design-system.md) | Tokens, colors, typography, components in `styles.css` |
| UIX-07 | [Shared UX guidelines](UIX-07-ui-guidelines.md) | Approval gates, status rules, source-of-truth, accessibility |

## Screens

| Code | Spec | Mockup file | Related project / agent | Status |
|---|---|---|---|---|
| UIX-01 | [Delivery Dashboard](UIX-01-dashboard.md) | `index.html` | All agents, whole workflow | ✅ Built |
| UIX-02 | [Atlas Workflow](UIX-02-atlas-workflow.md) | `atlas.html` | Atlas (Phase 1 MVP) | ⏳ Next |
| UIX-03 | [Review & Approvals](UIX-03-review-approvals.md) | `review.html` | All agents — human gate | Planned |
| UIX-04 | [Jira Breakdown](UIX-04-jira-breakdown.md) | `jira-breakdown.html` | Atlas + Jira integration | Planned |
| UIX-05 | [Audit Log](UIX-05-audit-log.md) | `audit-log.html` | Governance / all agents | Planned |
| UIX-06 | [Leadership Metrics](UIX-06-metrics.md) | `metrics.html` | CEO/CTO visibility | Planned |
| UIX-08 | [Gaia Research Workspace](Gaia/UIX-08-gaia-research.md) | `Gaia/gaia.html` | Gaia (Phase 2 build) | ✅ Built |
| UIX-09 | [Mira Design Studio](Mira/UIX-09-mira-design.md) | `Mira/mira.html` | Mira (Phase 4) | ✅ Built |

## Build order (start slow, file by file)

1. `styles.css` + `index.html` — foundation and overview ✅
2. `atlas.html` — the Phase 1 MVP workflow (SEC-07 Phase 1, SEC-08 item 5)
3. `review.html` — the human approval gate (SEC-02 principle 1)
4. `jira-breakdown.html` — delivery structure (SEC-05 Atlas + Jira)
5. `audit-log.html` — audit trail (SEC-05 "All AI work is audited")
6. `metrics.html` — CEO/CTO dashboard (SEC-11 item 6)
7. `gaia.html` — Gaia research workspace (SEC-07 Phase 2)
