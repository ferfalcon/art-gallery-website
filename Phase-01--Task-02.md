---
artifact: TASK
id: P01-T02
status: Complete
baseline:
  design: [SRC-DS-001]
  repository: [SRC-REPO-002]
  runtime: []
  documentation: []
  assets: []
created: 2026-08-16
updated: 2026-08-16
---

<!-- control:cli-managed:start -->
Canonical task state, prerequisites, references, validation, and output lineage are owned by `.workflow/workflow-record.json` and `.workflow/generated/TASK-INDEX.md`.
<!-- control:cli-managed:end -->

# Phase 01 — Task 02: Implement shared primary navigation and themed Footer

## 1. Status

Complete. Shared navigation and Footer responsibilities are implemented and all required validation passed.

## 2. Objective

Create the repeated native primary-action and Footer responsibilities once, with explicit destinations, accessible focus/hover behavior, Dark/Gold themes, static social artwork, and source-accurate responsive spacing.

## 3. Source References

- `PLAN-002`; approved Stage 8 plan-review corrections.
- `REQ-FR-003`, `REQ-FR-004`, `REQ-FR-005`, `REQ-AR-002`, `REQ-AR-003`, `REQ-AR-004`, `REQ-AR-006`.
- `SPEC-BEH-004`, `SPEC-INT-001`, `SPEC-INT-002`, `SPEC-INT-003`, `SPEC-ACC-002`.
- Active inputs: `SRC-DS-001`, `SRC-REPO-002`; Stage 9 checks: `VER-017`, `VER-018`.

## 4. Snapshot Verification

At Stage 10 start verify the approved `P01-T01` implementation output and relevant navigation/Footer Figma resources. Unexpected unrelated changes require rebaseline handling.

## 5. Prerequisites

`P01-T01` complete with shared tokens/assets/document-shell conventions available. Repeat the repository-required frontend guidance preflight before HTML/CSS work.

## 6. Scope

Included: `PrimaryAction.astro`, `Footer.astro`, explicit Home/Location href contracts, default/hover/focus presentation, Dark/Gold Footer themes, static social artwork, responsive Footer behavior. Excluded: page-specific composition, invented social links, JS navigation, backend/state.

## 7. Repository Context

Builds on the Phase 01 foundation while preserving static Astro output and repository conventions. No test framework or client-state layer is assumed.

## 8. Files and Modules

- `frontend/src/components/PrimaryAction.astro` — create native anchor component with explicit `href`.
- `frontend/src/components/Footer.astro` — create shared Dark/Gold Footer.
- `frontend/src/styles/global.css` — modify only for truly shared component helpers/tokens.

## 9. Dependencies and Interfaces

Prerequisite: `P01-T01`. Home action destination is `/location/`; Location action destination is `/`. Social artwork remains non-interactive. `PLAN-002` is the canonical trace item.

## 10. Implementation Steps

1. Verify the predecessor output and current Figma navigation/Footer resources.
2. Complete frontend guidance preflight.
3. Implement `PrimaryAction.astro` with an explicit `href` contract; never infer destination from label/variant.
4. Implement source-supported default/hover/focus states using native anchors without hydration.
5. Implement `Footer.astro` with Dark and Gold themes and semantic content order.
6. Keep social artwork outside the tab order until authoritative destinations exist.
7. Preserve the source-demonstrated Dark/Home versus Gold/Location mobile side-spacing difference at 375 px; choose transitions from layout failure.
8. Run declared validation and record output lineage.

No implementation code is included in this decomposition.

## 11. State, Responsive, and Accessibility Requirements

Primary actions support default, hover, and focus-visible. Footer supports Dark and Gold themes; social icons are static artwork. No loading/empty/error/success/disabled states apply. Footer stacks before layout failure while preserving theme-specific 375 px spacing. Use ordinary anchors with native keyboard activation and visible focus.

## 12. Validation

- **Astro build — Build, required:** `pnpm build` succeeds with shared components.
- **Navigation accessibility — Accessibility, required:** explicit native anchors, keyboard activation/focus, and non-interactive social artwork are correct.
- **Footer responsive fidelity — Responsive, required:** Dark/Gold variants preserve approved responsive layouts and 375 px theme-specific spacing without overflow.
- **Shared states visual review — Visual, required:** both navigation directions and Footer themes match approved default/hover/focus evidence.

All checks remain `Not executed` until Stage 10.

## 13. Acceptance Criteria

- [x] `PLAN-002` objective and referenced Must behavior are implemented.
- [x] Explicit `/location/` and `/` href contracts are preserved.
- [x] Accessibility/responsive/visual checks pass.
- [x] Output snapshot lineage and discoveries/deviations are recorded.

## 14. Risks and Considerations

- Medium: a shared Footer could normalize distinct mobile theme spacing. Treat spacing as explicit theme responsibility and validate both 375 px variants.
- Low: future social URLs may arrive later. Do not introduce them in this task without upstream impact review.

## 15. Implementation Discoveries

- PrimaryAction keeps `href`, `label`, and direction explicit so route destinations are never inferred from visual variants.
- Footer breakpoint selection is based on the 450px tablet content group plus 60px social group and required breathing room; it stacks at 630px while retaining the 375px Dark/Gold padding difference.
- Social artwork stays purely visual and outside the tab/accessibility flow because no authoritative social destinations exist.

## 16. Deviations

None. The task is implemented without owner-approved deviations.

## 17. Output Lineage

Complete. Implementation output commit: `7997bc12db9db5089f5004f2d3f0e38ecb7d603a`; the canonical workflow record owns the generated output snapshot and validation lineage.

## 18. Definition of Done

- [x] Objective/acceptance criteria complete.
- [x] All required validation passes.
- [x] Source/output lineage and documentation are current.
- [x] No unapproved deviation/blocker remains.

## 19. Completion Report

Pending Stage 10 implementation.
