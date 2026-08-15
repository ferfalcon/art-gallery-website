# Repository Operating Contract

## Purpose

This repository implements the Art gallery website from the approved design source. Agents working here must preserve design fidelity, accessibility, maintainability, and traceability between Figma, implementation, Git history, and deployments.

## Project sources

- Repository: `ferfalcon/art-gallery-website`
- Frontend application: `frontend/`
- Framework: Astro + TypeScript
- Package manager: pnpm
- Node.js: follow `frontend/package.json` (`24.x`)
- Figma design: `https://www.figma.com/design/g2a8iUAviJAsHl5PBUwaUY/art-gallery-website?node-id=2148-2`
- Primary Figma page: `🤖 Workflow` (`2148:2`)
- Vercel team: `fer-falcons-team`
- Vercel project: `art-gallery-website`

## Instruction hierarchy

Apply instructions in this order, with scope-specific rules overriding broader ones where they do not conflict:

1. Explicit user instruction for the current task.
2. This root `AGENTS.md`.
3. The nearest nested `AGENTS.md` for the files being changed.
4. Once the implementation workflow is initialized, `design-workflow context --json` is canonical for mutable workflow state such as current stage, task, mode, blockers, artifacts, and code-edit policy.
5. Actual repository, Figma, and deployment sources.
6. Narrative documentation and generated artifacts.

Do not infer mutable workflow state from prose when canonical CLI state is available.

## Figma scope

The primary editing scope is the `🤖 Workflow` page.

Do not create, move, delete, rename, restructure, or visually modify nodes on any other Figma page unless the user explicitly asks for it.

### File-global design-system exception

Agents may inspect and modify file-global design-system resources when necessary to correctly prepare, normalize, or audit `🤖 Workflow`. This includes:

- local text styles
- local color, effect, and grid styles
- variable collections and modes
- variables, names, hierarchy, scopes, aliases, and code syntax
- style names and descriptions

Before any global change:

1. Inspect usage across the file.
2. Assess impact on other pages.
3. Preserve existing references whenever possible instead of detaching or duplicating values.
4. Preserve visual output on other pages unless the user explicitly approves a visual change.
5. Verify affected references after the change and check for unintended visual regressions.

This exception does not permit structural or content edits on other pages. If a required fix would structurally or visually alter another page rather than only a shared global resource, stop and request explicit approval.

## Source fidelity and implementation

Inspect actual design and repository sources before implementing. Do not invent files, APIs, commands, dependencies, breakpoint values, tokens, component behavior, interaction rules, or accessibility behavior.

When implementing from Figma, inspect as applicable:

- target screens and viewports
- component and variant structure
- variables, styles, and tokens
- typography and spacing
- imagery and assets
- interaction states
- responsive transformations
- content edge cases
- accessibility implications

Figma does not independently prove semantic HTML, keyboard or screen-reader behavior, intermediate responsive behavior, backend rules, or browser performance. Those must be designed and validated in the implementation.

Implementation should integrate semantic HTML, keyboard and focus behavior, accessible names and relationships, responsive behavior, reduced-motion considerations, relevant UI states, content edges, and regression checks as applicable.

Avoid unrelated refactors and premature abstractions.

## Frontend guidance

Before HTML, CSS, or client-side JavaScript work, follow the installed project skill at `.agents/skills/modern-web-guidance/SKILL.md` and retrieve the relevant modern web guidance before implementation.

Also follow `frontend/AGENTS.md` for Astro-specific development instructions.

## Git and deployment policy

Treat `main` as production state.

- Make implementation and project-guidance changes on a dedicated branch.
- Prefer branch → pull request → Vercel preview → verification → merge.
- Do not push implementation changes directly to `main` unless the user explicitly requests it.
- Do not manually trigger or promote a production deployment unless the user explicitly requests it.
- Keep commits narrowly scoped and use clear, imperative subjects.
- Before merging, verify the relevant implementation and, when applicable, the Vercel preview.

## Implementation workflow lifecycle

The workflow source lives in `docs/implementation-workflow/`.

Before workflow initialization, the absence of `.workflow/` is expected and is not an error.

Do not create `.workflow/`, infer workflow state, or manually fabricate workflow records unless the user explicitly asks to start or initialize the workflow.

Once initialized, begin workflow-related work by running:

```bash
design-workflow context --json
```

Treat that output as canonical operational state. Respect its current execution kind, stage, mode, blockers, artifacts, task scope, and code-edit policy.

Never manually edit `.workflow/generated/*`.

## Validation and evidence

Never claim a check passed unless it actually ran successfully and there is evidence.

For task-oriented work, report:

- what changed
- relevant input and output snapshots
- verification or validation actually executed
- deviations, blockers, or risks
- generated-state status when applicable
- the next permitted action

When implementation changes are visual, verify against the relevant Figma source and the rendered application. When deployment behavior matters, verify the relevant Vercel deployment or preview rather than assuming Git state alone proves correctness.

## Scope-specific instructions

Nested `AGENTS.md` files remain authoritative for their directories:

- `frontend/AGENTS.md` — Astro/frontend development behavior
- `docs/implementation-workflow/AGENTS.md` — workflow package development rules

Do not duplicate or override those rules here unless a repository-wide constraint genuinely applies.
