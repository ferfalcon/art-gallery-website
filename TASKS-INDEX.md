---
artifact: TASKS-INDEX
status: Approved
baseline:
  design:
    - SRC-DS-001
  repository:
    - SRC-REPO-002
created: 2026-08-16
updated: 2026-08-16
---

<!-- control:cli-managed:start -->
Canonical task IDs, mutable status, prerequisites, baseline, references, output, and validation summaries are owned by `.workflow/workflow-record.json` and rendered in `.workflow/generated/TASK-INDEX.md`.
<!-- control:cli-managed:end -->

# Tasks Index

## 1. State Ownership Mode

- [x] CLI-managed — task registry: `.workflow/generated/TASK-INDEX.md`
- [ ] Markdown-only — not used

The connected environment cannot execute the local workflow CLI because no checkout is available to it; mutations follow the repository's schema-v2/CLI contract through the GitHub connector and generated views are synchronized deterministically.

## 2. Document Information

- Status: Approved by the project owner on 2026-08-16; `GATE-010` is Passed with assumptions.
- Version: 1.0
- Last updated: 2026-08-16
- Project: Art gallery website
- Source plan: `PLAN.md` / `ART-PLAN`
- Plan review: `PLAN-REVIEW.md` / `ART-PLAN-REVIEW`
- Architecture: `ARCHITECTURE.md` / `ART-ARCHITECTURE`
- Active inputs: `SRC-DS-001`, `SRC-REPO-002`
- Stage 9 source verification: `VER-017`, `VER-018`
- Canonical trace definitions: required `PLAN-001` through `PLAN-005`, each owned by `ART-PLAN` and mapped to one Ready task.

## 3. Scope

### Included

- Decompose every approved plan item into one coherent independently verifiable implementation task.
- Preserve the plan's dependency order while allowing Home and Location route work to proceed in parallel after shared foundations stabilize.
- Declare build, accessibility, responsive, visual, route, and preview validation before implementation starts.
- Carry source verification, repository guidance, font fidelity, semantic landmark, native-link, static-map, split-title, and theme-specific Footer constraints into the owning task.

### Excluded

- Implementation code or frontend changes.
- Any Stage 10 task execution before a separate workflow continuation advances Stage 9 to Stage 10.
- New requirements, architecture, routes, services, interactions, social destinations, or Figma edits.

## 4. Execution Rules

- Execute only tasks whose prerequisites are complete.
- Reverify the relevant design/repository inputs at each task start; expected predecessor output may become the next task start only with recorded lineage.
- Run root/nested `AGENTS.md`, modern-web guidance, and relevant Astro guidance preflight before frontend implementation.
- Do not silently update a task to newer source content or work around documentation/source errors.
- Do not mark a task complete while required validation is failed, blocked, or not executed.
- Keep accessibility, responsive behavior, image semantics, focus behavior, and tests/checks inside the task that creates the feature.
- Preserve `frontend/vercel.json` unless separate deployment evidence requires review.
- The unresolved font-source risk is not permission to pass typography fidelity with a fallback: resolve matching distributable local files or obtain an explicit owner-approved deviation.

## 5. Phase Summary

| Phase | Objective | Depends on | Parallel work | Completion criteria |
|---|---|---|---|---|
| Phase 01 | Establish shared visual/document foundation, navigation, and Footer contracts. | None | Sequential: `P01-T01` → `P01-T02` | Shared inputs/components build and satisfy declared accessibility/responsive/visual checks. |
| Phase 02 | Implement the two approved page routes. | Phase 01 | `P02-T01` Home and `P02-T02` Location may run in parallel after `P01-T02`. | Both routes independently satisfy build/accessibility/responsive/visual checks and produce implementation-output snapshots. |
| Phase 03 | Integrate, clean starter residue, and perform final regression/preview verification. | Both Phase 02 tasks | No | Two-route build, cross-page checks, six-anchor visual regression, and Vercel preview verification pass. |

## 6. Phase Details

### Phase 01 — Shared foundation

`P01-T01` establishes assets, semantic tokens, global CSS, typography delivery/fallback handling, and `Layout.astro`. It owns the Stage 8 font-source risk and cannot declare typography fidelity complete on an undocumented fallback.

`P01-T02` builds `PrimaryAction.astro` and `Footer.astro` on that foundation. It owns explicit native hrefs, keyboard/focus behavior, non-interactive social artwork, and the Dark/Gold 375 px Footer spacing distinction.

### Phase 02 — Route implementation

`P02-T01` builds Home and protects the defining desktop split/inverted hero title plus the tablet/mobile transformations and editorial content.

`P02-T02` builds Location with a static map/marker/action composition, semantic location details, native return navigation, and Gold Footer. It intentionally introduces no map SDK or interactive affordance.

### Phase 03 — Integration and preview

`P03-T01` runs only after both routes complete. It removes confirmed-unused starter residue, verifies exact bidirectional routes, reruns cross-page accessibility/reflow/visual regression, and validates the frontend-changing PR in Vercel preview before merge.

## 7. Plan Coverage

| `PLAN.md` item | Task | Coverage status | Notes |
|---|---|---|---|
| `PLAN-001` | `P01-T01` | Complete | Foundation/assets/fonts/document shell. |
| `PLAN-002` | `P01-T02` | Complete | Native actions and themed Footer. |
| `PLAN-003` | `P02-T01` | Complete | Complete Home route. |
| `PLAN-004` | `P02-T02` | Complete | Complete Location route. |
| `PLAN-005` | `P03-T01` | Complete | Integration, cleanup, regressions, Vercel preview. |

## 8. Requirement and Specification Coverage

| Requirement/specification group | Priority | Task or tasks | Validation owner | Coverage |
|---|---|---|---|---|
| Visual assets, typography, static Astro constraints | Must | `P01-T01` | `P01-T01` | Complete with documented font-input stop condition |
| Native Home ↔ Location navigation, focus/hover | Must | `P01-T02`, route tasks, `P03-T01` | `P01-T02`, `P03-T01` | Complete |
| Footer identity/themes/social non-interactivity | Must | `P01-T02`, `P03-T01` | `P01-T02`, `P03-T01` | Complete |
| Home content, hero, editorial hierarchy | Must | `P02-T01` | `P02-T01` | Complete |
| Location content and static map composition | Must | `P02-T02` | `P02-T02` | Complete |
| Responsive/reflow behavior | Must | All UI tasks | Owning task + `P03-T01` regression | Complete |
| Semantic structure/image semantics/accessibility | Must | All UI tasks | Owning task + `P03-T01` regression | Complete |
| Git/Vercel delivery policy | Must | `P03-T01` | `P03-T01` | Complete |
| Unsupported capabilities remain excluded | Must | All tasks | Scope/deviation review | Complete |

## 9. Cross-Cutting Coverage

| Concern | Integrated tasks | Final validation | Gap |
|---|---|---|---|
| Source verification and rebaseline | All | `P03-T01` verifies prerequisite lineage | None |
| Accessibility | `P01-T01`–`P02-T02` | `P03-T01` cross-page check | None |
| Responsive behavior | `P01-T01`–`P02-T02` | `P03-T01` cross-page regression | None |
| Approved states/errors | Shared and route tasks | `P03-T01` regression | No dynamic loading/empty/error UI is approved |
| Security/privacy | Scope exclusions | Not applicable: static site, no data/auth/API | None |
| Performance | Asset/layout discipline in owning tasks | Production build/preview sanity | No dedicated benchmark required by approved plan |
| Documentation/lineage | Every task | `P03-T01` completion report | None |
| Regression protection | Route tasks | `P03-T01` | None |

## 10. Blocked Work and Coordination Risks

| Task | Blocker or coordination risk | Decision owner | Required action | Impact | Status |
|---|---|---|---|---|---|
| `P01-T01` | Authoritative distributable font files/source metadata are absent from current repository inputs. | Project owner if fallback is proposed | Resolve matching source-controlled fonts, or explicitly approve the documented fidelity deviation. | Typography visual fidelity cannot pass silently on fallback. | Open risk; accepted for Stage 9 exit |
| `P02-T01`, `P02-T02` | Both depend on stable shared component contracts. | Implementation workflow | Complete `P01-T02` before either route task starts. | Prevents duplicated/incompatible shared implementations. | Controlled by prerequisites |
| `P03-T01` | Requires both routes and their output lineage. | Implementation workflow | Complete `P02-T01` and `P02-T02`. | Final regression/preview cannot start early. | Controlled by prerequisites |

## 11. Source-change Log

| Date | Changed snapshot | Affected tasks | Impact and action | Status |
|---|---|---|---|---|
| 2026-08-16 | None at Stage 9 entry | All | `VER-017` reverified Figma; `VER-018` proved current `main` and `SRC-REPO-002` share frontend tree `e3af997b8fdf9beb136b8f78561adf1d2c4d2d17`. No rebaseline required. | Complete |

## 12. Overall Completion Criteria

- [ ] Every canonical task is Complete in `.workflow/generated/TASK-INDEX.md`.
- [ ] Every required validation passes with evidence.
- [ ] Every approved plan item and Must behavior remains covered.
- [ ] Task source/input lineage remains valid or is explicitly rebased/reviewed.
- [ ] Documentation discoveries are propagated to the owning artifact.
- [ ] No critical/high blocker remains.
- [ ] Final implementation validation is ready for Stage 11.

## 13. Index Validation

### Review pass 1 — Completeness and correctness

- [x] Every `PLAN-001`–`PLAN-005` item maps to one independently verifiable task.
- [x] Every task has a stable ID, task-start baseline, prerequisites, scope/files, non-code steps, validation, acceptance criteria, risks, and DoD.
- [x] Canonical task state and generated task index are synchronized.
- [x] Phase criteria/dependency ordering permit intended Home/Location parallelism without overlapping shared ownership.
- [x] All required validation definitions exist before task readiness.

### Review pass 2 — Consistency, traceability, source integrity, risks, and uncertainty

- [x] `VER-017` and `VER-018` show no material source change requiring rebaseline.
- [x] Required `PLAN-001`–`PLAN-005` trace definitions each reach exactly one Ready task and its declared validation.
- [x] Stage 8 safeguards are preserved in owning tasks: fonts, explicit hrefs, Home split-title, modern-web preflight, page landmark ownership, Footer mobile spacing.
- [x] No task introduces unsupported scope, hydration, runtime service, interactive map, or social destination.
- [x] The font-source uncertainty remains explicit and cannot be silently treated as passed visual fidelity.
- [x] Stage 9 was explicitly approved by the project owner; `GATE-010` is Passed with assumptions and the workflow intentionally remains at Stage 9 Ready.