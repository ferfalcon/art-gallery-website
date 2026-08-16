---
artifact: TASK
id: P02-T02
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

# Phase 02 — Task 02: Implement the complete Location route

## 1. Status

Ready for Stage 10 only after explicit Stage 9 approval. Implementation has not started.

## 2. Objective

Add the approved `/location/` page with static map artwork/marker/action composition, semantic location details, native return navigation, and the Gold Footer without introducing interactive-map behavior.

## 3. Source References

- `PLAN-004`; approved Stage 8 plan-review corrections.
- `REQ-FR-002`, `REQ-FR-004`, `REQ-FR-006`, `REQ-FR-007`, `REQ-AR-001`, `REQ-AR-005`, `REQ-NFR-001`, `REQ-NFR-002`.
- `SPEC-BEH-002`, `SPEC-BEH-003`, `SPEC-BEH-005`, `SPEC-BEH-006`, `SPEC-INT-002`, `SPEC-ACC-001`, `SPEC-ACC-003`.
- Active inputs: `SRC-DS-001`, `SRC-REPO-002`; Stage 9 checks: `VER-017`, `VER-018`.

## 4. Snapshot Verification

At Stage 10 start verify the approved `P01-T02` output and Location desktop/tablet/mobile plus Map Hero/Location Details resources. Unexpected unrelated changes require rebaseline handling.

## 5. Prerequisites

`P01-T02` complete. May run in parallel with `P02-T01` once shared interfaces are stable. Repeat the frontend guidance preflight before implementation.

## 6. Scope

Included: static map image/marker/action composition, semantic location details, `/` return action, Gold Footer, responsive crop/overlay/details behavior. Excluded: map SDK, geolocation, routes/controls, hydration, new behavior.

## 7. Repository Context

Static Astro route composition using Phase 01 shared contracts. The map is source artwork, not a live map product.

## 8. Files and Modules

- `frontend/src/components/MapHero.astro` — create static map artwork, marker, return action, responsive crop/overlay.
- `frontend/src/components/LocationDetails.astro` — create semantic location heading/address/visit content and responsive layout.
- `frontend/src/pages/location.astro` — create semantic `/location/` composition and page-owned `<main>`/heading structure.

## 9. Dependencies and Interfaces

Prerequisite: `P01-T02`. Use shared `PrimaryAction` with explicit `href="/"` and Gold Footer. `PLAN-004` is the canonical trace item.

## 10. Implementation Steps

1. Verify predecessor/source inputs and complete frontend guidance preflight.
2. Implement Map Hero as static local artwork with approved marker/action overlay and native Home action.
3. Expose no interactive-map controls, gestures, geolocation, routes, or misleading interactive semantics.
4. Implement Location Details with semantic address/visit content and responsive columns that stack before readability/overflow failure.
5. Compose `/location/` with Gold Footer and its demonstrated mobile spacing.
6. Validate crop, marker/action visibility, details readability, navigation, and Footer at anchors/intermediate widths.
7. Run declared validation and record output lineage.

No implementation code is included in this decomposition.

## 11. State, Responsive, and Accessibility Requirements

Static/default plus shared `BACK TO HOME` hover/focus. No map loading/interaction/geolocation/error states apply. Validate 1440/768/375 and intermediate/transition widths with marker/action visibility and no horizontal overflow. Use native Home link, logical landmarks/headings, semantic address content, visible focus, and appropriate static map/marker image semantics.

## 12. Validation

- **Astro build — Build, required:** `pnpm build` succeeds with `/location/` and assets.
- **Location accessibility — Accessibility, required:** address/visit semantics, native return link, static-map semantics, focus order and visible focus pass.
- **Location responsive reflow — Responsive, required:** map/details remain usable at anchors/intermediate/transition widths without overflow.
- **Location visual fidelity — Visual, required:** approved map/details/navigation/Gold Footer compositions match without invented map interaction.

All checks remain `Not executed` until Stage 10.

## 13. Acceptance Criteria

- [ ] `PLAN-004` objective and referenced Must behavior are implemented.
- [ ] Map remains static and semantically non-interactive.
- [ ] Accessibility/responsive/visual/build checks pass.
- [ ] Output lineage and deviations are recorded.

## 14. Risks and Considerations

- Medium: map subject/crop and overlay placement vary by viewport. Adapt conservatively from the three anchors and test transitions.
- Low: static map may be mistaken for interactive UI. Avoid controls/interactive roles and classify artwork semantics explicitly.

## 15. Implementation Discoveries

None during decomposition.

## 16. Deviations

None during decomposition.

## 17. Output Lineage

Pending Stage 10 implementation.

## 18. Definition of Done

- [ ] Objective/acceptance criteria complete.
- [ ] All required validation passes.
- [ ] Source/output lineage and documentation are current.
- [ ] No unapproved deviation/blocker remains.

## 19. Completion Report

Pending Stage 10 implementation.
