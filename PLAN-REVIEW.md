---
artifact: PLAN-REVIEW
status: Approved
baseline:
  design:
    - SRC-DS-001
  repository:
    - SRC-REPO-002
  runtime: []
  documentation: []
  assets: []
created: 2026-08-16
updated: 2026-08-16
---

# Plan Review

## 1. Document Information

- Status: Approved by the project owner on 2026-08-16.
- Review date: 2026-08-16.
- Reviewer: ChatGPT.
- Project: Art gallery website.
- Source baseline: `SOURCE-BASELINE.md`.
- Reviewed `PLAN.md`: Stage 7 plan merged on `main` at `4fabacc63fc63da2392fbc828c29fc57ca214682`; Stage 8 corrections applied on `workflow/stage-8-plan-review` beginning with `1c89f3fcc57c67574d1ff0fe7b3efad41ca9d5f3`.
- Active inputs: `SRC-DS-001`, `SRC-REPO-002`.
- Stage 8 source verification: `VER-015`, `VER-016`.

## 2. Review Sources

- `PLAN.md`
- `REQUIREMENTS.md`
- `DESIGN.md`
- `SPEC.md`
- `ARCHITECTURE.md`
- `DOCUMENT-REVIEW.md`
- `SOURCE-BASELINE.md`
- Root `AGENTS.md`
- `frontend/AGENTS.md`
- `.agents/skills/modern-web-guidance/SKILL.md`
- Active Figma source `SRC-DS-001`, including fresh Stage 8 inspection of `🤖 Workflow` and Home/Desktop design context
- Active repository input `SRC-REPO-002` and current-main comparison

## 3. Baseline Integrity and Repository Assumption Check

| Plan claim | Snapshot and repository evidence | Accurate at pinned commit | Newer source detected | Required correction |
|---|---|---:|---:|---|
| Astro `^7.2.2`, Node `24.x`, pnpm, static starter structure | `SRC-REPO-002`; `VER-016` | Yes | Workflow/docs only | None |
| `frontend/vercel.json` is part of the active implementation baseline | `SRC-REPO-002` | Yes | No frontend change | None |
| Required gallery/map/brand/font assets are absent from the repository baseline | `SRC-REPO-002`; `SRC-DS-001` | Yes | No frontend change | Clarify font-source handling before fidelity acceptance |
| Only confirmed repository validation command is `pnpm build` | `frontend/package.json` at `SRC-REPO-002` | Yes | No frontend change | None; do not invent lint/test scripts |
| Frontend tasks must follow nested repository instructions and modern-web guidance | Root `AGENTS.md`, `frontend/AGENTS.md`, `.agents/skills/modern-web-guidance/SKILL.md` | Yes | No | Add explicit task-start preflight to plan |
| Home desktop includes the split/inverted title treatment bridging dark field and hero image | `SRC-DS-001`; fresh Home/Desktop design context | Yes | No design change | Protect explicitly in Home approach/validation |
| `PrimaryAction.astro` can represent both native navigation destinations | Architecture + `SPEC-INT-001/002` | Proposed capability | N/A | Require explicit `href`; do not infer route from label |

Stage 8 repository verification compared `SRC-REPO-002` (`f28f02bb303a4f486e73e2ca1a326751e6c3fd02`) with current `main` (`4fabacc63fc63da2392fbc828c29fc57ca214682`). The newer commits add only workflow/documentation outputs; the `frontend/` tree remains identical to the pinned active implementation input. No repository rebaseline is required.

## 4. Review Method

### Pass 1 — Feasibility and completeness

The review challenged source validity, current-repository claims, dependency ordering, proposed files, asset/font acquisition, component APIs, responsive transformations, accessibility ownership, validation executability, deployment behavior, rollback, and task-size suitability.

Corrections were made directly in `PLAN.md` where the approved evidence supported a more explicit requirement. No new product behavior was added.

### Pass 2 — Consistency, traceability, source integrity, risks, and uncertainty

The corrected plan was reviewed end-to-end against all Must requirements, material `SPEC-*` behavior and `AC-*` criteria, approved Stage 6 architecture, the exact active snapshots, and repository operating contracts. Residual uncertainty is kept explicit rather than treated as confirmed implementation input.

## 5. Executive Summary

The Stage 7 plan is technically feasible and remains correctly scoped to a static two-route Astro implementation. Stage 8 found no product, architecture, repository, or design change requiring rollback to an earlier stage.

Six plan-quality issues were found. All were correctable in the owning plan without changing approved behavior:

1. typography delivery was deferred too loosely despite Stage 6 architecture requiring an explicit source/fallback strategy;
2. the proposed shared native-link interface omitted an explicit `href`;
3. the defining Home desktop split-color hero-title behavior was not protected explicitly enough;
4. the plan did not carry the repository-mandated modern-web guidance into implementation task preflight;
5. page-landmark ownership needed to be separated more clearly from the shared document shell;
6. shared Footer ownership needed to state the source-demonstrated Dark/Gold mobile spacing difference explicitly.

All six findings are corrected in `PLAN.md`. Stage 8 is approved and the plan is eligible for Stage 9 task decomposition when the project owner separately instructs the workflow to continue. The only material residual risk is the absence of authoritative distributable font binaries/source metadata in current repository inputs. That risk does not prevent task decomposition, but the foundation task cannot claim typography fidelity until matching source-controlled font files are resolved or the project owner explicitly accepts the documented fallback deviation.

**Readiness:** Ready with documented risks.

## 6. Plan Coverage

| Requirement or specification | Snapshot or evidence | Plan item | Coverage | Validation defined | Notes |
|---|---|---|---|---:|---|
| Home content and editorial hierarchy — `REQ-FR-001`, `SPEC-BEH-001` | `SRC-DS-001` | `PLAN-003` | Complete | Yes | Includes explicit desktop split-title protection |
| Location content/static map — `REQ-FR-002`, `SPEC-BEH-002/003` | `SRC-DS-001` | `PLAN-004` | Complete | Yes | No interactive map behavior introduced |
| Home → Location native navigation — `REQ-FR-003`, `SPEC-INT-001` | `SRC-DS-001`, architecture | `PLAN-002`, `PLAN-003` | Complete | Yes | Explicit `href="/location/"` correction |
| Location → Home native navigation — `REQ-FR-004`, `SPEC-INT-002` | `SRC-DS-001`, architecture | `PLAN-002`, `PLAN-004` | Complete | Yes | Explicit `href="/"` correction |
| Footer identity/themes/social non-interactivity — `REQ-FR-005`, `SPEC-BEH-004`, `SPEC-INT-003` | `SRC-DS-001` | `PLAN-002`, `PLAN-005` | Complete | Yes | Includes theme-specific 375 px spacing |
| Responsive/reflow behavior — `REQ-FR-006`, `REQ-NFR-002`, `SPEC-BEH-006`, `SPEC-VAL-001` | `SRC-DS-001` | `PLAN-002`–`PLAN-005` | Complete | Yes | Transition thresholds based on layout failure, not anchor widths |
| Approved imagery/assets — `REQ-FR-007`, `REQ-DR-001`, `SPEC-BEH-005` | `SRC-DS-001`, `SRC-REPO-002` | `PLAN-001`, `PLAN-003`, `PLAN-004` | Complete with input risk | Yes | Exact asset filenames remain intentionally unresolved until export |
| Semantics/reading order — `REQ-AR-001`, `SPEC-ACC-001` | Upstream artifacts | `PLAN-001`, `PLAN-003`, `PLAN-004` | Complete | Yes | Page routes explicitly own `<main>` and heading hierarchy |
| Keyboard/focus — `REQ-AR-002/003`, `SPEC-ACC-002` | `SRC-DS-001` | `PLAN-002`–`PLAN-005` | Complete | Yes | Native links and `:focus-visible` |
| Image/social semantics — `REQ-AR-004`, `SPEC-ACC-003` | `SRC-DS-001` | `PLAN-001`, `PLAN-002`, page items | Complete | Yes | No fake social controls |
| Reflow/reduced motion — `REQ-AR-005/006`, `SPEC-ACC-004` | `SRC-DS-001` | `PLAN-002`–`PLAN-005` | Complete | Yes | Motion remains optional and reduced-motion aware |
| Visual fidelity — `REQ-NFR-001`, `AC-002/004/010/014` | `SRC-DS-001` | All implementation items | Complete with font risk | Yes | Font risk cannot be silently treated as passed fidelity |
| Astro/pnpm/Node contract — `REQ-CON-001/002` | `SRC-REPO-002` | `PLAN-001`, all tasks | Complete | Yes | No unapproved framework/runtime changes |
| Git/Vercel process — `REQ-CON-003` | Root `AGENTS.md`, `SRC-REPO-002` | `PLAN-005` | Complete | Yes | Branch → PR → preview → verification → merge |
| Unsupported-capability exclusions — `REQ-CON-005` | Upstream artifacts | All items | Complete | Yes | No backend, API, auth, map SDK, social destinations, or hydration invented |

All Must requirements and material acceptance criteria have an implementation and validation path. No must-have behavior is deferred solely to the final cleanup phase.

## 7. Findings

### PLANREV-001 — Font delivery lacked the Stage 6 source/fallback constraint

- **Impact:** Medium
- **Category:** Dependency / Source baseline / Validation
- **Finding:** `PLAN-001` originally deferred font source/licensing resolution to implementation and referred to an unspecified fallback strategy. `ARCHITECTURE.md` requires local/source-controlled delivery when legally available and an explicit source/fallback strategy when it is not.
- **Snapshot and evidence:** `SRC-DS-001` proves Big Shoulders Display Black 900, Big Shoulders Display ExtraBold 800, and Outfit Light 300; `SRC-REPO-002` contains no distributable font binaries/source metadata.
- **Plan section:** Technical Approach / Typography; `PLAN-001`; Risks.
- **Resolution:** Define exact required family/style identities, prohibit silently adding an unapproved runtime font dependency, define fallback stacks, and require the owning task to block fidelity acceptance or obtain explicit owner acceptance if matching distributable files remain unavailable.
- **Change made to `PLAN.md`:** Added a typography-delivery subsection, strengthened `PLAN-001`, file impact, dependencies, validation, and risk language.
- **Remaining risk:** Matching source-controlled font binaries/source metadata are still not present in current approved repository inputs.
- **Status:** Corrected; residual risk documented.

### PLANREV-002 — Shared native-link interface omitted an explicit destination

- **Impact:** Medium
- **Category:** Integration / Accessibility / Abstraction
- **Finding:** `PLAN-002` originally described a native-anchor component with label/direction/theme inputs only. A reusable native link must receive its destination explicitly rather than infer routing from the visible label or variant.
- **Snapshot and evidence:** `SPEC-INT-001`, `SPEC-INT-002`, Stage 6 routing architecture.
- **Plan section:** Component boundaries; Files and Modules; `PLAN-002`; validation.
- **Resolution:** Add an explicit `href` input; Home supplies `/location/`, Location supplies `/`.
- **Change made to `PLAN.md`:** Updated component responsibility, approach, validation, and route items.
- **Remaining risk:** None beyond ordinary implementation correctness.
- **Status:** Corrected.

### PLANREV-003 — Home desktop hero-title fidelity was under-specified

- **Impact:** Medium
- **Category:** Responsive / Validation / Traceability
- **Finding:** The plan protected the Home editorial hierarchy generally but did not explicitly protect the distinctive desktop title treatment that spans the dark field and image with inverted/split coloring. A generic responsive title implementation could satisfy content presence while materially missing the approved 1440 px composition.
- **Snapshot and evidence:** `SRC-DS-001`; fresh Stage 8 Home/Desktop design context; `DES-001`, `DES-005`; `AC-002`.
- **Plan section:** Technical Approach validation; `HomeHero.astro`; `PLAN-003`; `PLAN-005`.
- **Resolution:** Make the split-color desktop title and its tablet/mobile transformation explicit validation targets while requiring semantic text to remain available.
- **Change made to `PLAN.md`:** Added HomeHero responsibility, implementation technique constraints, anchor-specific validation, and regression coverage.
- **Remaining risk:** CSS implementation may require careful layering/clipping; this is an implementation risk, not an unresolved design decision.
- **Status:** Corrected.

### PLANREV-004 — Repository-required frontend guidance was missing from execution preflight

- **Impact:** Low
- **Category:** Repository assumption / Dependency
- **Finding:** Root `AGENTS.md` requires `.agents/skills/modern-web-guidance/SKILL.md` before HTML/CSS/client-side work, while `frontend/AGENTS.md` adds Astro-specific development instructions. Stage 7 described background dev-server use but did not carry the full prerequisite into implementation tasks.
- **Snapshot and evidence:** `SRC-REPO-002`, root `AGENTS.md`, `frontend/AGENTS.md`, `.agents/skills/modern-web-guidance/SKILL.md`.
- **Plan section:** Current Repository State; Technical Approach; `PLAN-001`.
- **Resolution:** Add an explicit task-start frontend guidance preflight that Stage 9 tasks must retain.
- **Change made to `PLAN.md`:** Added five-step task-start preflight and linked it to `PLAN-001`.
- **Remaining risk:** None if Stage 9 task templates preserve this prerequisite.
- **Status:** Corrected.

### PLANREV-005 — Shared layout and page landmark ownership needed clearer separation

- **Impact:** Low
- **Category:** Accessibility / Abstraction
- **Finding:** The files table described `Layout.astro` as owning “base landmarks/defaults,” which could conflict with Stage 6 architecture assigning page-level landmark/heading structure to route compositions.
- **Snapshot and evidence:** `ARCHITECTURE.md`; `SPEC-ACC-001`.
- **Plan section:** Component boundaries; Files and Modules; `PLAN-001`.
- **Resolution:** Make the shared layout own only document-shell concerns; Home and Location page routes explicitly own `<main>` and meaningful heading structure.
- **Change made to `PLAN.md`:** Corrected boundary language throughout the plan.
- **Remaining risk:** None.
- **Status:** Corrected.

### PLANREV-006 — Footer spacing distinction needed shared-component ownership

- **Impact:** Low
- **Category:** Responsive / Regression
- **Finding:** The original plan mentioned preserving Location mobile spacing, but the repeated Footer component did not explicitly own the demonstrated Dark/Home versus Gold/Location side-padding difference. A shared component could otherwise normalize the two themes accidentally.
- **Snapshot and evidence:** `SRC-DS-001`; `DES-004`; `AC-010`.
- **Plan section:** Files and Modules; `PLAN-002`; `PLAN-005` validation.
- **Resolution:** Make theme-specific mobile spacing a Footer responsibility and explicit 375 px validation target.
- **Change made to `PLAN.md`:** Updated Footer responsibility, responsive work, and regression checks.
- **Remaining risk:** None beyond implementation regression.
- **Status:** Corrected.

## 8. Ordering and Dependency Review

| Plan item | Depends on | Dependency supported | Ordering issue | Resolution |
|---|---|---:|---|---|
| `PLAN-001` | — | Yes | Font input can affect all typography | Resolve font delivery or recorded fallback decision before declaring foundation complete |
| `PLAN-002` | `PLAN-001` | Yes | Shared controls/footer require tokens/assets | No change; explicit `href` and theme spacing added |
| `PLAN-003` | `PLAN-001`, `PLAN-002` | Yes | Home depends on foundation/shared components | No change; title treatment made explicit |
| `PLAN-004` | `PLAN-001`, `PLAN-002` | Yes | Location depends on foundation/shared components | No change |
| `PLAN-005` | `PLAN-003`, `PLAN-004` | Yes | Final regression requires both routes | No change |

Home and Location remain reasonable parallel work only after shared interfaces are stable. Stage 9 may still decompose individual plan items into more than one task where independent verification or asset/foundation prerequisites justify it.

## 9. Integration and Cross-Cutting Coverage

| Concern | Covered in plan | Location | Gap or correction |
|---|---:|---|---|
| Source verification and rebaseline | Yes | Task-start preflight; Source-change Handling | Stage 8 added `VER-015/016`; no rebaseline needed |
| Accessibility | Yes | Every UI-owning plan item | Page landmark ownership clarified |
| Responsive behavior | Yes | Component items; Responsive Decision Process | Desktop title and footer spacing strengthened |
| Loading, empty, error, and success states | Yes / N/A | Error and state handling | Correctly classified as non-applicable static states |
| Data and API integration | N/A | Scope exclusions | No backend/API approved |
| Migration and compatibility | Yes | Section 11 | No data migration; starter replacement only |
| Security and privacy | Yes | Scope/rollback section | No secrets/tracking/remote runtime services planned |
| Testing and validation | Yes | Every plan item + `PLAN-005` | Uses only confirmed `pnpm build` plus browser/manual checks |
| Deployment and rollback | Yes | Section 11; `PLAN-005` | Existing `frontend/vercel.json` preserved; Git revert rollback |
| Regression protection | Yes | `PLAN-005` | Shared-change checks cover both routes |
| Repository implementation guidance | Yes | Task-start preflight | Added in Stage 8 |

## 10. Changes Applied to the Plan

| `PLAN.md` section | Change | Finding IDs | Result |
|---|---|---|---|
| Document/Repository State | Added Stage 8 verification and repository-guidance observations | `PLANREV-004` | Current-state claims now include execution contract |
| Technical Approach | Added frontend preflight, explicit landmark ownership, font strategy, `href`, title/footer validation | `PLANREV-001`–`006` | Plan is more executable without expanding scope |
| Files and Modules | Clarified Layout, PrimaryAction, Footer, HomeHero, font collection responsibilities | `PLANREV-001`, `002`, `003`, `005`, `006` | Proposed interfaces align with architecture/source |
| `PLAN-001` | Strengthened font/source/fallback and guidance preflight | `PLANREV-001`, `004`, `005` | Foundation has explicit stop conditions |
| `PLAN-002` | Added `href` and theme-specific mobile spacing | `PLANREV-002`, `006` | Shared component API/validation is unambiguous |
| `PLAN-003` | Added semantic split-color desktop title requirement | `PLANREV-003` | Material visual behavior protected |
| `PLAN-005` | Added regression checks for title, footer spacing, and font status | `PLANREV-001`, `003`, `006` | Cross-page validation is complete |
| Risks/DoD/Review | Updated font risk, Stage 7 approval marker, and Stage 8 correction status | All | Lifecycle/uncertainty no longer stale |

## 11. Residual Risks and Blocking Decisions

| Risk or decision | Impact | Likelihood | Mitigation or evidence needed | Owner | Status |
|---|---|---|---|---|---|
| Matching distributable Big Shoulders Display / Outfit font files are absent from approved repository inputs | Medium | Medium | Resolve authoritative distributable source in first foundation task; otherwise obtain explicit owner acceptance of fallback fidelity deviation | Project owner / implementation task | Open, non-blocking for Stage 9; may block fidelity acceptance |
| Exact exported image/vector filenames/formats are not yet repository inputs | Low | High until export | Export exact approved Figma assets and record concrete paths in task evidence | Implementation task | Open, non-blocking |
| Exact responsive threshold values require rendered failure evidence | Medium | Expected | Select at implementation from collision/compression/overflow evidence and test both sides | Owning UI tasks | Open by design |
| Map crop interpolation between anchors remains underspecified | Medium | Medium | Preserve source crop/marker/action intent and validate representative widths | Location task | Open, non-blocking |
| Social destinations remain unknown | Low | Expected | Keep artwork non-interactive; revisit upstream specification if destinations are supplied | Product owner | Safely constrained |

No unresolved technical decision requires returning to Stages 0–7. The font-source risk is intentionally carried forward with a hard fidelity stop condition rather than treated as solved.

## 12. Final Review Checklist

### Feasibility and completeness

- [x] The plan reflects the pinned repository snapshot.
- [x] Snapshot IDs exist and Stage 8 source verification was performed.
- [x] Included and excluded scope are explicit.
- [x] Phases produce meaningful, verifiable outcomes.
- [x] Dependencies, ordering, integration, migration, compatibility, and validation are complete.
- [x] Accessibility, responsiveness, states, errors, and tests are integrated.
- [x] Rollback/recovery is addressed where relevant.

### Consistency, traceability, source integrity, risks, and uncertainty

- [x] Every Must requirement and material specification is covered.
- [x] No plan item introduces unsupported product scope.
- [x] Proposed and existing files are distinguished.
- [x] No plan claim silently relies on newer source content.
- [x] Architecture decisions are respected.
- [x] Residual risks, accepted tradeoffs, and blockers are explicit.
- [x] The corrected plan received a second end-to-end review.
- [x] No Stage 9 tasks or implementation work have been created.

## 13. Final Readiness Status

**Ready with documented risks**

Stage 8 was explicitly approved by the project owner on 2026-08-16. The plan is eligible for Stage 9 task decomposition, but Stage 9 is intentionally not started until a separate instruction to continue. The unresolved font-binary/source input remains visible and must be resolved or explicitly accepted as a fidelity deviation before affected implementation validation can pass.

## 14. Completion Summary

- Files created or modified: `PLAN-REVIEW.md`; corrected `PLAN.md`; workflow control/generated views updated separately as part of the same Stage 8 review branch.
- Snapshot IDs reviewed: `SRC-DS-001`, `SRC-REPO-002`.
- Source verification performed: `VER-015` (design unchanged), `VER-016` (repository implementation input unchanged).
- Important findings: six; all corrected in the owning plan.
- Plan corrections: explicit font strategy/stop rule, explicit native-link `href`, protected desktop hero-title treatment, mandatory frontend guidance preflight, clarified page landmark ownership, explicit theme-specific mobile Footer spacing.
- Remaining risks: distributable font binaries/source metadata; implementation-time asset filenames; responsive thresholds; map interpolation; unresolved social destinations.
- Open questions or blockers: no blocker for task decomposition; font delivery may block foundation/fidelity acceptance unless resolved or explicitly accepted as a deviation.
- Project-owner decision: Stage 8 approved on 2026-08-16.
- Recommended next stage: Stage 9 — Decompose into tasks, only after the project owner separately instructs the workflow to continue.
