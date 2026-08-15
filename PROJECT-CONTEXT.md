---
artifact: PROJECT-CONTEXT
project: Art gallery website
profile: Standard
execution_mode: Gated
created: 2026-08-15
updated: 2026-08-15
---

# Project Context

## Project

- **Project name:** Art gallery website
- **Goal:** implement the approved Figma source faithfully in the existing Astro frontend and ship through the repository's GitHub → Vercel workflow.
- **Project type:** Multi-page static website.
- **Selected profile:** Standard.
- **Profile rationale:** the approved source contains connected Home and Location pages with desktop, tablet, and mobile variants, reusable UI patterns, repository integration, and deployment verification. This exceeds Lite/Express scope but does not currently require Full-profile backend, persistence, authentication, or multi-service architecture.

## Active source baseline

- Design input: `SRC-DS-001` — verified unchanged as `VER-001`.
- Repository input: `SRC-REPO-001` — verified unchanged as `VER-002`.
- Detailed source evidence: `SOURCE-BASELINE.md`.

## Design scope

### Included

- `🤖 Workflow` page (`2148:2`)
- Home: Desktop (`2148:1957`), Tablet (`2148:2140`), Mobile (`2148:2169`)
- Location: Desktop (`2148:2069`), Tablet (`2148:2196`), Mobile (`2148:2218`)
- Supporting components and style-guide resources on `🤖 Workflow`

### Excluded

- Structural or visual edits to other Figma pages unless explicitly requested.
- Backend, authentication, persistence, or API features not supported by the source.

## Repository scope

- Target application: `frontend/`
- Framework: Astro `^7.2.2`
- Runtime constraint: Node `24.x`
- Package manager: pnpm
- Production state: `main`
- Implementation policy: dedicated branch → PR → Vercel preview → verification → merge.
- Before frontend implementation, follow `frontend/AGENTS.md` and `.agents/skills/modern-web-guidance/SKILL.md`.

## Quality baseline

- Preserve Figma visual and responsive intent.
- Use semantic HTML and accessible keyboard/focus behavior.
- Integrate screen-reader relationships and accessible names where applicable.
- Respect reduced-motion preferences for any motion introduced.
- Validate relevant content edge cases and intermediate responsive behavior rather than treating Figma breakpoints as the only supported widths.
- Run actual build/validation checks before claiming success.
- Verify visual implementation against Figma and, when deployment behavior matters, against the Vercel preview.

## Current risks and questions

### Blocking

- None at Stage 1 entry.

### Non-blocking

- Architecture remains undecided until Stage 6; current evidence suggests it may be explicitly skippable for this static Astro implementation.
- Semantic, keyboard, assistive-technology, and intermediate responsive behavior require implementation-side definition because Figma cannot prove them.

## Stage 0 decision

The active inputs and control artifacts were reviewed and explicitly approved by the project owner on 2026-08-15. The workflow is ready for the pinned design evidence audit.
