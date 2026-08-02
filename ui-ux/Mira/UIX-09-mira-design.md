# UIX-09 — Mira Design Studio

**Mockup:** `Mira/mira.html` · **Status:** ✅ Built
**Requirements:** [SEC-05](../../docs/SEC-05-architecture.md) (UI/UX + Figma + Mira), [SEC-09](../../docs/SEC-09-suggestions.md) (UI/UX lead owns design sign-off), [SEC-07](../../docs/SEC-07-roadmap.md) Phase 4

## Purpose

Mira's workspace with **three separate sections** (tabs):

1. **Design settings** — the inputs Mira audits against: UI/UX philosophy and an advanced
   color palette (50–900 scales, semantic tokens with light/dark values, per-token contrast
   grades, CVD checks, token export / Figma-variable sync).
2. **Design system** — the common design module, `@moderta/ui`, a React component library
   shared across Moderta products (npm package, Storybook, code ↔ Figma sync, per-component
   variants/props and audit state). Consumes the MIRA-06 tokens.
3. **UI/UX Builder** — pre-made designs generated from approved wireframes + the design settings
   + published `@moderta/ui` components; the designer opens them in Figma, refines, and owns
   sign-off. Mira's audit comments are suggestions.

## Section codes (visible in the UI)

| Code | Section | Tab |
|---|---|---|
| MIRA-01 | Sidebar navigation | — |
| MIRA-02 | Topbar | — |
| MIRA-03 | Page header | — |
| MIRA-04 | Section tabs (settings / design system / builder) | — |
| MIRA-05 | UI/UX philosophy (principles) | Settings |
| MIRA-06 | Color palette (scales, semantic tokens, contrast/CVD validation, export) | Settings |
| MIRA-07 | Design system — `@moderta/ui` React library (components, versions, sync, audit state) | Design system |
| MIRA-08 | Pre-made designs gallery (open in Figma to edit) | Builder |
| MIRA-09 | Mira design audit (findings vs MIRA-05/06/07) | Builder |
| MIRA-10 | Mira Assistant chat (always visible) | Both |
