# SEC-09 — Team Operating Requirements

**1. The first workflow must support multiple roles.** The system must allow a research or product requirement to become acceptance criteria, test cases, edge cases, implementation notes, and review comments that BA, UI/UX, engineering, QA, and architecture can refine together.

**2. The team must understand how the system works.** BA, UI/UX, engineering, QA, and leadership must understand agent inputs, company document retrieval, approval gates, audit logs, and how AI output is evaluated.

**3. The first technical setup must stay simple and maintainable**

- Backend must expose controlled APIs for approved enterprise AI providers
- Document search must use an approved vector store for company context
- Frontend must provide review, approve, reject, edit, comment, and final-source-of-truth actions
- Integrations must connect only the systems required for the workflow: Jira, Git, Figma, documentation, Slack/email, and reporting

**4. The system must use focused agents, not one generic chat.** Gaia, Atlas, Ada, Mira, Uncle Bob, and Leonidas must have clear responsibilities, inputs, outputs, review rules, and audit logs.

**5. Evaluation must be built from the start.** Each agent must be tested against real examples, expected outputs, review effort, edit rate, and quality score before being expanded to more teams.

**6. Required roles and ownership**

| Role | Owns |
|---|---|
| CEO/leadership | Business direction, priorities, and AI usage visibility |
| CTO/architect | Architecture, security, integrations, maintainability, and source-of-truth rules |
| Business Analyst | Requirements refinement, final requirement approval, and Jira readiness |
| Research Assistant | Research quality, sustainability context, and source validation |
| UI/UX lead | Design quality, Figma standards, accessibility, and design sign-off |
| Engineering lead | Implementation quality, estimates, branches, pull requests, and code standards |
| QA lead | Test design, release confidence, regression coverage, and quality gates |

**7. Required risk controls**

- Research, market, and finance outputs must include sources and stay in draft state until human approval
- Code suggestions must pass human review, static analysis, standards checks, and security review
- Secrets, customer data, and proprietary code must stay inside approved enterprise systems
- Final human-approved work must never be modified automatically by AI; AI may only report or suggest separately

**8. Required first build candidates**

- Shared prompt and standards library for Gaia, Atlas, Ada, Mira, Uncle Bob, and Leonidas
- Indexed core sustainability product documents for company-context answers
- Internal Atlas workflow for requirements, mockup, acceptance criteria, and Jira task creation
- Internal Ada workflow for test case design and copy-to-Jira support
