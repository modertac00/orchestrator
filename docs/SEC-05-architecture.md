# SEC-05 — High-Level Architecture

Moderta is a product company building sustainability products. The AI ecosystem should support the full product delivery flow: research → business analysis → mockups → task breakdown → test design → UI/UX → architecture review → development → code review → security and quality checks. People stay responsible for decisions and refinement, while AI helps generate, review, connect, and improve the work.

## Layer diagram

```
┌─────────────────────────────────────────────────────────────────┐
│                         PEOPLE LAYER                             │
│ Research Assistant │ Business Analyst │ UI/UX │ Architect │ Devs │
│ QA │ Leadership                                                  │
│ People refine, review, estimate, approve, and own final decisions│
└────────────────────────────┬────────────────────────────────────┘
                             │ direction / review / approval
┌────────────────────────────▼────────────────────────────────────┐
│                       PRODUCT WORKFLOW                           │
│ Sustainability research → requirements → mockups → Jira tasks    │
│ test cases → UI/UX → architecture review → dev → review → release│
└────────────────────────────┬────────────────────────────────────┘
                             │ creates / updates / connects
┌─────────────────────────────────────────────────────────────────┐
│                    WORK SYSTEMS / SOURCES                        │
│ Docs: research, requirements, PRD, guidelines, decisions         │
│ HTML/CSS mockups: early system mockups generated with AI         │
│ Jira: epics, stories, subtasks, estimates, status, QA tasks      │
│ Figma: reusable UI/UX samples, prototypes, design system         │
│ Git: branches, sample code, implementation, pull requests        │
└────────────────────────────┬────────────────────────────────────┘
                             │ read / update / trigger
┌─────────────────────────────────────────────────────────────────┐
│                    AUTOMATION / ORCHESTRATION                    │
│ n8n connects Docs ↔ Jira ↔ Figma ↔ Git ↔ Slack/Email             │
│ Moves approved work forward, requests reviews, logs handoffs     │
└────────────────────────────┬────────────────────────────────────┘
                             │ sends context / receives output
┌────────────────────────────▼────────────────────────────────────┐
│                          AI LAYER                                │
│ Gaia: sustainability research summaries and insights             │
│ Atlas: requirements, mockups, tasks, acceptance criteria         │
│ Ada: test cases, regression ideas, edge cases                    │
│ Mira: design audit, guideline comments, accessibility            │
│ Uncle Bob: sample code, branch support, code quality, code review│
│ Leonidas: security review, risky patterns, dependency checks     │
└────────────────────────────┬────────────────────────────────────┘
                             │ uses company context
┌────────────────────────────▼────────────────────────────────────┐
│                     KNOWLEDGE / CONTEXT LAYER                    │
│ Sustainability knowledge, product docs, past requirements, Jira  │
│ history, Figma guidelines, coding standards, test cases, security│
│ rules, architecture decisions, customer and market research      │
└────────────────────────────┬────────────────────────────────────┘
                             │ powered by
┌────────────────────────────▼────────────────────────────────────┐
│                       MODEL / API LAYER                          │
│ Enterprise AI APIs, embeddings, retrieval, optional fine-tuning  │
└─────────────────────────────────────────────────────────────────┘
```

## How it connects

1. **Research starts the flow** — The Research Assistant researches sustainability topics, market needs, regulations, competitors, and customer problems. Gaia helps summarize findings and turn them into structured inputs.
2. **BA converts research into requirements** — The Business Analyst explains and refines requirements, creates the product brief, and uses Atlas to generate an early HTML/CSS system mockup.
3. **Atlas creates delivery structure** — From the approved requirements and mockup, Atlas breaks work into epics, stories, subtasks, and acceptance criteria. Ada drafts the test case designs. The BA reviews and refines before it becomes execution work.
4. **Developers estimate and validate feasibility** — Developers review the BA-refined tasks, estimate effort, identify technical risks, and confirm what can be built.
5. **UI/UX turns mockups into product design** — The UI/UX team starts from reusable sample UI/UX patterns and customizes them for the product. Mira audits the design against guidelines, accessibility, consistency, and usability.
6. **Review happens before development** — Mira comments are reviewed by the BA, Research Assistant, and Architect so the requirement, design, and technical direction are aligned.
7. **Development starts with connected systems** — Jira tasks are ready, Git branches are created for developers, sample code or implementation guidance is prepared by Uncle Bob, and developers review before implementing.
8. **Agents support quality and security** — Uncle Bob, Ada, and Leonidas support code review, code quality checks, standards enforcement, test suggestions, security testing, dependency checks, and release notes. Humans still approve merges and releases.
9. **All AI work is audited** — Every AI-generated output should keep a record of who reviewed it, what was edited, what was accepted, what was rejected, and how long employees spent assessing, editing, and refining it.
10. **CEO and CTO get visibility** — Leadership should receive detailed inputs on AI usage, human review time, quality improvements, repeated corrections, bottlenecks, and where AI is helping or failing.
11. **Human-approved work becomes source of truth** — Once a human edits, refines, approves, or marks something as final, AI must not change the actual work. After human touch, AI can only create reports, summaries, audit notes, or separate suggestions for human review. Future AI work should treat the final human-approved version as the source of truth.

## Example connection flow

| Pairing | What happens |
|---|---|
| **Research Assistant + Gaia** | Research sustainability product opportunities, regulations, competitors, customer needs, and risks; save findings in documentation. |
| **Business Analyst + Atlas** | Convert research into requirements, PRD notes, user flows, acceptance criteria, and an early HTML/CSS mockup. |
| **Atlas + Jira** | Break the approved requirement into epics, stories, subtasks, QA tasks, and initial test cases. n8n can create or update Jira items automatically after BA approval. |
| **BA + Developers** | BA refines the work; developers review feasibility, give estimates, and flag dependencies or architecture concerns. |
| **UI/UX + Figma + Mira** | UI/UX converts the HTML/CSS mockup into a proper Figma design using reusable sample components. Mira audits design quality, accessibility, consistency, and guideline alignment. |
| **BA + RA + Architect** | Review AI comments, UI/UX updates, technical constraints, and final requirement alignment before development begins. |
| **Development + Git + Uncle Bob** | n8n or the engineering workflow creates Git branches from Jira work. Uncle Bob prepares sample code, implementation notes, standards guidance, and review checklists for developers. |
| **Review + Ada + Leonidas** | Ada and Leonidas support code review, security checks, test suggestions, quality checks, and release documentation. Engineers, QA, Architect, and BA approve final movement to release. |

## Simple rule

> Research drives requirements, BA refines, AI accelerates, systems connect, UI/UX polishes, architects guide, developers build, QA and security protect, humans approve.
