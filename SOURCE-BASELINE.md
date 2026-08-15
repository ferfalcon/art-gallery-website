---
artifact: SOURCE-BASELINE
project: Art gallery website
profile: Standard
execution_mode: Gated
created: 2026-08-15
updated: 2026-08-15
---

# Source Baseline

## Document information

- Project: Art gallery website
- Source registry: `.workflow/generated/SOURCE-INDEX.md`
- Related context: `PROJECT-CONTEXT.md`
- Operational state: `WORKFLOW-STATE.md`

## Design source evidence

### SRC-DS-001 — Figma implementation source

- **Source type:** Figma
- **Reference:** `https://www.figma.com/design/g2a8iUAviJAsHl5PBUwaUY/art-gallery-website?node-id=2148-2`
- **File key:** `g2a8iUAviJAsHl5PBUwaUY`
- **Primary page:** `🤖 Workflow` (`2148:2`)
- **Included implementation screens:** Home and Location at desktop, tablet, and mobile sizes.
- **Supporting design evidence:** component resources and style-guide documentation on the same page.
- **Authority:** approved visual and responsive implementation source for this project.
- **Pin strength:** time-bound until a named/versioned Figma revision is recorded.
- **Verification:** `VER-001` — Unchanged on 2026-08-15 via Figma structure comparison.
- **Known limitation:** Figma does not by itself define semantic HTML, keyboard/screen-reader behavior, intermediate responsive behavior, or runtime performance.

## Repository source evidence

### SRC-REPO-001 — Git repository baseline

- **Repository:** `ferfalcon/art-gallery-website`
- **Relevant application:** `frontend/`
- **Framework:** Astro + TypeScript
- **Package manager:** pnpm
- **Node.js:** `24.x`
- **Baseline commit:** `fa000a21be23460757fdf09a4c9e49a677f695fb`
- **Baseline branch at capture:** `main`
- **Reference in canonical record:** `.`
- **Pin strength:** immutable commit SHA.
- **Verification:** `VER-002` — Unchanged on 2026-08-15; GitHub `main` still resolves to the baseline commit.

## Runtime source evidence

- Production URL: `https://art-gallery-website-ferfalcon.vercel.app/`
- Vercel project: `fer-falcons-team/art-gallery-website`
- A runtime snapshot is not an active input at this stage.

## Source authority

| Snapshot | Authority | Scope |
|---|---|---|
| `SRC-DS-001` | Design | Visual design, responsive compositions, components, styles, imagery, and content represented in Figma |
| `SRC-REPO-001` | Current implementation / technical constraint | Repository structure, Astro setup, package/runtime constraints, project operating contract |

## Stage 0 review

- Both active inputs were reverified unchanged.
- The project owner explicitly approved the Stage 0 baseline on 2026-08-15.
- Stage 0 passed and the workflow advanced to the design-audit stage.

## Rebaseline rule

Any unexpected design or repository change after this baseline must be recorded as a new `SRC-*` snapshot with impact assessment rather than silently replacing these inputs.
