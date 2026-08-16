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

- **Role:** Input baseline.
- **Status:** Active.
- **Source type:** Figma.
- **Reference:** `https://www.figma.com/design/g2a8iUAviJAsHl5PBUwaUY/art-gallery-website?node-id=2148-2`
- **File key:** `g2a8iUAviJAsHl5PBUwaUY`
- **Primary page:** `🤖 Workflow` (`2148:2`).
- **Included implementation screens:** Home and Location at desktop, tablet, and mobile sizes.
- **Supporting design evidence:** component resources and style-guide documentation on the same page.
- **Authority:** approved visual and responsive implementation source for this project.
- **Pin strength:** Time-bound until a named/versioned Figma revision is recorded.
- **Latest verification:** `VER-010` — Unchanged at Stage 6.
- **Known limitation:** Figma does not by itself define semantic HTML, keyboard/screen-reader behavior, intermediate responsive behavior, or runtime performance.

## Repository source evidence

### SRC-REPO-001 — Original Stage 0 repository baseline

- **Role:** Input baseline used by Stages 0–5.
- **Status:** Superseded for current implementation input by `SRC-REPO-002`; retained as immutable historical lineage for artifacts that reference it.
- **Repository:** `ferfalcon/art-gallery-website`
- **Relevant application:** `frontend/`
- **Framework:** Astro + TypeScript.
- **Package manager:** pnpm.
- **Node.js:** `24.x`.
- **Baseline commit:** `fa000a21be23460757fdf09a4c9e49a677f695fb`.
- **Baseline branch at capture:** `main`.
- **Reference in canonical record:** `.`.
- **Pin strength:** Immutable commit SHA.
- **Stage 5 verification:** `VER-009` — Unchanged at the Stage 5 checkpoint.
- **Stage 6 change detection:** `VER-011` — Unexpected upstream or concurrent change; replacement `SRC-REPO-002`.

### SRC-REPO-002 — Stage 6 current repository input

- **Role:** Input baseline for Stage 6 and later planning.
- **Status:** Active.
- **Repository:** `ferfalcon/art-gallery-website`
- **Relevant application:** `frontend/`
- **Commit:** `f28f02bb303a4f486e73e2ca1a326751e6c3fd02`.
- **Branch at capture:** `main`.
- **Reference in canonical record:** `.`.
- **Pin strength:** Immutable commit SHA.
- **Reason created:** after Stage 5, approved PR #7 added `frontend/vercel.json` with the Vercel ignored-build command for docs-only changes.
- **Relevant inspected paths:** `frontend/package.json`, `frontend/astro.config.mjs`, `frontend/src/`, `frontend/AGENTS.md`, and `frontend/vercel.json`.
- **Verification:** `VER-012` — current commit and relevant repository structure inspected at Stage 6.
- **Authority:** current repository structure, Astro/runtime constraints, and repository-owned deployment configuration.

## Runtime source evidence

### SRC-RUN-001 — Vercel project observation

- **Role:** Supporting source for Stage 6 deployment architecture.
- **Status:** Active.
- **Source type:** Vercel project/runtime observation.
- **Reference:** `https://vercel.com/fer-falcons-team/art-gallery-website`
- **Project:** `fer-falcons-team/art-gallery-website`
- **Project ID:** `prj_c1Co0SgYyStXUE6Qgd3FgDUBDx5x`
- **Observed Node.js runtime:** `24.x`.
- **Observed production deployment:** `dpl_7Grr79zVrDMSoHW5f6AK4q9qWGvH`
- **Observed deployment state:** `READY`.
- **Production domain:** `https://art-gallery-website-ferfalcon.vercel.app/`
- **Captured:** `2026-08-16T00:32:00.000Z`.
- **Pin strength:** Time-bound; project settings may change after capture.
- **Known limitation:** this is supporting architecture evidence, not a Stage 10/11 validation-runtime snapshot.

## Stage 6 repository rebaseline impact assessment

| New snapshot | Previous snapshot | Change summary | Affected artifacts/stages | Earliest affected stage | Action | Status |
|---|---|---|---|---:|---|---|
| `SRC-REPO-002` | `SRC-REPO-001` | `main` advanced through approved workflow/docs changes and PR #7; material frontend difference is new `frontend/vercel.json` deployment-skip configuration. | Architecture, plan, task decomposition, implementation/deployment validation | 6 | Preserve Stages 0–5 against `SRC-REPO-001`; use `SRC-REPO-002` for current architecture and later repository-aware work. | Resolved |

The repository change does **not** alter approved visual design, product requirements, responsive intent, navigation behavior, map/social scope, or acceptance criteria. No rollback to Stages 1–5 is required.

## Source authority

| Snapshot | Authority | Scope |
|---|---|---|
| `SRC-DS-001` | Design | Visual design, responsive compositions, components, styles, imagery, and content represented in Figma |
| `SRC-REPO-001` | Historical repository input | Immutable implementation/technical baseline used by approved Stages 0–5 |
| `SRC-REPO-002` | Current repository input | Current Astro structure, package/runtime constraints, project operating contract, and repository-owned Vercel configuration |
| `SRC-RUN-001` | Supporting runtime evidence | Time-bound Vercel project/runtime observation used by Stage 6 architecture |

## Stage history

- Stage 0 established `SRC-DS-001` and `SRC-REPO-001`.
- Stages 1–5 were approved against those inputs and remain valid.
- Stage 6 reverified `SRC-DS-001` as unchanged.
- Stage 6 detected the repository change, created `SRC-REPO-002`, performed impact assessment, and limited the rebaseline to architecture and downstream work.
- `SRC-RUN-001` was added as supporting evidence for deployment/runtime architecture.

## Rebaseline rule

Any later unexpected design, repository, runtime, documentation, or asset change must be recorded as a new `SRC-*` snapshot with impact assessment rather than silently replacing an existing snapshot ID.
