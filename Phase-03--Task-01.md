---
artifact: TASK
id: P03-T01
status: Ready
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

# Phase 03 — Task 01: Integrate routes, remove starter residue, and verify the preview

## 1. Status

Ready for Stage 10 only after explicit Stage 9 approval. Implementation has not started.

## 2. Objective

Deliver and verify the coherent two-route static site by removing confirmed-unused starter residue, exercising cross-page navigation/accessibility/reflow/visual regressions, and validating the frontend-changing pull request in Vercel preview.

## 3. Source References

- `PLAN-005`; approved Stage 8 plan-review corrections.
- All Must requirements, especially `REQ-FR-003`–`REQ-FR-006`, `REQ-AR-001`–`REQ-AR-005`, `REQ-NFR-001`, `REQ-NFR-002`, `REQ-CON-003`.
- `SPEC-BEH-006`, `SPEC-INT-001`–`SPEC-INT-003`, `SPEC-VAL-001`, and `AC-001`–`AC-017` as applicable.
- Active inputs: `SRC-DS-001`, `SRC-REPO-002`; Stage 9 checks: `VER-017`, `VER-018`.

## 4. Snapshot Verification

Before integration verify approved outputs from `P02-T01` and `P02-T02`, their parent lineage, and relevant design/runtime inputs. Unexpected unrelated change triggers rebaseline handling.

## 5. Prerequisites

`P02-T01` and `P02-T02` complete with implementation-output snapshots.

## 6. Scope

Included: two-route integration, confirmed-unused starter cleanup, build/routing/keyboard/reflow/six-anchor visual regression, Vercel preview verification. Excluded: unrelated refactors, new features/dependencies, changing `frontend/vercel.json` without separate deployment evidence/review.

## 7. Repository Context

This task integrates the earlier static Astro outputs under the repository branch → PR → Vercel preview → verify → merge policy.

## 8. Files and Modules

- `frontend/src/pages/index.astro`, `frontend/src/pages/location.astro` — verify/fix only evidenced integration defects.
- `frontend/src/components/*.astro`, `frontend/src/styles/global.css` — modify only for evidenced cross-page defects.
- `frontend/src/components/Welcome.astro`, `frontend/src/assets/astro.svg`, `frontend/src/assets/background.svg` — delete only if confirmed unreferenced.
- `frontend/vercel.json` — preserve unless separate deployment evidence requires architecture review.

## 9. Dependencies and Interfaces

Requires both route tasks. Exact navigation remains `/` ↔ `/location/`; static Astro and shared-component contracts remain intact. `PLAN-005` is the canonical trace item.

## 10. Implementation Steps

1. Verify both prerequisite outputs and active source inputs.
2. Inspect imports/references and remove only confirmed-unused starter residue.
3. Run final production build and verify both routes plus exact bidirectional native hrefs.
4. Run keyboard/accessibility regression across both routes.
5. Run responsive/reflow checks at all six Figma anchors, representative intermediate widths, zoom/reflow sanity points, and transition boundaries.
6. Perform six-anchor visual regression protecting Home split-title, Location map crop/overlay, and theme-specific Footer mobile spacing.
7. Use the frontend-changing PR's Vercel preview and verify both routes/navigation in that runtime.
8. Record validation evidence, deviations, remaining risks, and final output lineage; do not merge without repository-required review/verification.

No implementation code is included in this decomposition.

## 11. State, Responsive, and Accessibility Requirements

No new runtime states. Verify only approved default and link hover/focus states. Broken routes/assets are defects, not designed error states. Cross-page checks cover 1440/768/375 anchors, intermediate widths, transitions, wrapping, and no content loss/horizontal scroll. Verify native navigation, keyboard activation/focus, landmarks/headings, image semantics, logical order, social non-interactivity, and reduced-motion handling if any non-essential motion appears.

## 12. Validation

- **Production build — Build, required:** final `pnpm build` succeeds.
- **Route integration — Manual, required:** `/` and `/location/` render and navigate bidirectionally with exact hrefs.
- **Cross-page accessibility — Accessibility, required:** keyboard/focus/landmarks/headings/images/social semantics pass.
- **Cross-page responsive regression — Responsive, required:** both routes pass all anchors/intermediate/transition widths without content loss or page-level overflow.
- **Six-anchor visual regression — Visual, required:** all six approved Figma frames match within approved intent.
- **Vercel preview verification — Manual, required:** frontend PR receives READY preview and both routes/navigation work; `frontend/vercel.json` remains preserved unless separately reviewed.

All checks remain `Not executed` until Stage 10.

## 13. Acceptance Criteria

- [ ] `PLAN-005` and applicable acceptance criteria are satisfied.
- [ ] Both routes/build/navigation pass.
- [ ] Cross-page accessibility/responsive/visual validation passes.
- [ ] Vercel preview validation passes.
- [ ] Starter cleanup is reference-proven and no unrelated refactor is introduced.
- [ ] Final output lineage/deviations are recorded.

## 14. Risks and Considerations

- Medium: late shared fixes may regress the sibling route. Change shared code only for evidenced defects and rerun both-route checks.
- Low: Vercel preview is time-bound; record the specific implementation PR runtime evidence.
- High fidelity stop: unresolved typography cannot silently pass final visual review without matching source-controlled fonts or explicit owner-approved fallback deviation.

## 15. Implementation Discoveries

None during decomposition.

## 16. Deviations

None during decomposition.

## 17. Output Lineage

Pending Stage 10 implementation.

## 18. Definition of Done

- [ ] Objective/acceptance criteria complete.
- [ ] All required validation passes with evidence.
- [ ] Output/rebaseline lineage and documentation are current.
- [ ] No unresolved critical/high blocker or unapproved deviation remains.

## 19. Completion Report

Pending Stage 10 implementation.
