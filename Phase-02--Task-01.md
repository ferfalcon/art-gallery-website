---
artifact: TASK
id: P02-T01
status: In progress
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

# Phase 02 — Task 01: Implement the complete Home route

## 1. Status

Stage 10 Home implementation is complete and all required validation has passed; canonical completion is recorded through the workflow CLI.

## 2. Objective

Replace the Astro starter Home presentation with the approved Home hero, editorial gallery content, native location action, and Dark Footer while preserving semantic reading order and the defining responsive title treatment.

## 3. Source References

- `PLAN-003`; approved Stage 8 plan-review corrections.
- `REQ-FR-001`, `REQ-FR-003`, `REQ-FR-006`, `REQ-FR-007`, `REQ-AR-001`, `REQ-AR-005`, `REQ-NFR-001`, `REQ-NFR-002`.
- `SPEC-BEH-001`, `SPEC-BEH-005`, `SPEC-BEH-006`, `SPEC-INT-001`, `SPEC-ACC-001`, `SPEC-ACC-003`.
- Active inputs: `SRC-DS-001`, `SRC-REPO-002`; Stage 9 checks: `VER-017`, `VER-018`.

## 4. Snapshot Verification

At Stage 10 start verify the approved `P01-T02` output and Home desktop/tablet/mobile Figma anchors. Unexpected unrelated source changes require rebaseline handling.

## 5. Prerequisites

`P01-T02` complete. Shared foundation, `PrimaryAction`, and `Footer` contracts must be stable. Repeat the frontend guidance preflight before implementation.

## 6. Scope

Included: Home hero, semantic `MODERN ART GALLERY` title, `/location/` native action, gallery/editorial content, Dark Footer, responsive composition. Excluded: Location implementation, hydration, new behavior, unrelated refactors.

## 7. Repository Context

Static Astro route composition using Phase 01 shared contracts. The approved plan prefers semantic HTML plus Grid/Flexbox/intrinsic sizing over viewport-coordinate reconstruction.

## 8. Files and Modules

- `frontend/src/components/HomeHero.astro` — create hero, imagery, split/inverted desktop title, responsive transformations.
- `frontend/src/components/GalleryContent.astro` — create editorial/gallery content.
- `frontend/src/pages/index.astro` — replace starter presentation with semantic Home composition and page-owned `<main>`/heading structure.

## 9. Dependencies and Interfaces

Prerequisite: `P01-T02`. Use shared `PrimaryAction` with explicit `href="/location/"` and Dark Footer. `PLAN-003` is the canonical trace item.

## 10. Implementation Steps

1. Verify predecessor/source inputs and complete frontend guidance preflight.
2. Build Home hero in logical DOM/reading order using one semantic visible title.
3. Implement the 1440 px split/inverted title relationship across dark field/image using CSS layering/clipping without duplicate announced heading text.
4. Implement source-demonstrated tablet/mobile title transformations rather than forcing the desktop overlay narrow.
5. Build Gallery Content with Grid/Flexbox/intrinsic constraints, approved crops, hierarchy, wrapping, and image semantics.
6. Compose Home with Dark Footer; choose responsive transitions before real layout failure and check intermediate widths.
7. Run declared validation and record output lineage.

No implementation code is included in this decomposition.

## 11. State, Responsive, and Accessibility Requirements

Static/default plus shared `OUR LOCATION` hover/focus states. No loading/empty/error UI is approved. Validate at 1440/768/375 and representative intermediate/transition widths with no page-level horizontal scrolling/content hiding. Keep one semantic hero title, logical reading order, meaningful headings/images, native link, and visible focus.

## 12. Validation

- **Astro build — Build, required:** `pnpm build` succeeds after the Home route replaces starter content.
- **Home accessibility — Accessibility, required:** logical semantics/image handling/native action/focus pass.
- **Home responsive reflow — Responsive, required:** 375/768/1440 plus intermediate/transition widths remain usable without horizontal overflow.
- **Home visual fidelity — Visual, required:** approved three-anchor composition matches, especially desktop split/inverted title and tablet/mobile transformations.

All four required Stage 10 checks passed with recorded build, accessibility, responsive, and visual evidence.

## 13. Acceptance Criteria

- [x] `PLAN-003` objective and referenced Must behavior are implemented.
- [x] Desktop split-title and responsive transformations match design intent.
- [x] Accessibility/responsive/visual/build checks pass.
- [x] Output lineage and any deviations are recorded.

## 14. Risks and Considerations

- High: split desktop title can tempt duplicate text/brittle absolute reconstruction. Use one semantic title with local visual layering/clipping and test accessibility/responsiveness.
- Medium: editorial asymmetry may overflow at intermediate widths. Prefer fluid Grid/Flexbox/intrinsic constraints and test transitions.

## 15. Implementation Discoveries

- The desktop split title uses one semantic `<h1>` plus clipped `::before` generated text, so the visual inversion never duplicates announced heading content.
- The source-backed tablet composition takes over at 67rem, before the desktop intro/action relationship can fail.
- Home artwork uses local responsive `<picture>` sources; the hero is prioritized and below-the-fold gallery artwork lazy-loads.
- Runtime validation measured 1440/1276/1072/900/768/640/630 and exact 480/375 widths with zero horizontal overflow.

## 16. Deviations

None. The Home route is implemented without an owner-approved deviation.

## 17. Output Lineage

Validated Home implementation on the current task branch; canonical output snapshot identity is assigned by `task complete`.

## 18. Definition of Done

- [x] Objective/acceptance criteria complete.
- [x] All required validation passes.
- [x] Source/output lineage and documentation are current.
- [x] No unapproved deviation/blocker remains.

## 19. Completion Report

Implementation and all four required checks passed; canonical completion/output identity follows from `task complete`.
