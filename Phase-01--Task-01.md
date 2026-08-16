---
artifact: TASK
id: P01-T01
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

# Phase 01 — Task 01: Establish the visual foundation and shared document shell

## 1. Status

Stage 10 implementation is validated; canonical task completion is recorded through the workflow CLI.

## 2. Objective

Create the source-controlled visual foundation shared by both routes: approved assets, semantic tokens, typography delivery/fallback handling, global CSS, and a reusable Astro document shell without hydration or runtime state.

## 3. Source References

- `PLAN-001`; `PLAN-REVIEW.md`; `ARCHITECTURE.md`.
- `REQ-DR-001`, `REQ-AR-001`, `REQ-AR-004`, `REQ-CON-001`, `REQ-CON-002`, `REQ-FR-007`, `REQ-NFR-001`.
- `SPEC-BEH-005`, `SPEC-ACC-001`, `SPEC-ACC-003`.
- Active inputs: `SRC-DS-001`, `SRC-REPO-002`; Stage 9 checks: `VER-017`, `VER-018`.

## 4. Snapshot Verification

Before implementation, verify the task-start repository snapshot and relevant Figma resources. Expected predecessor output may be adopted only with recorded lineage; any unrelated material change triggers the workflow rebaseline protocol.

## 5. Prerequisites

None. Before frontend edits, read root `AGENTS.md`, `frontend/AGENTS.md`, `.agents/skills/modern-web-guidance/SKILL.md`, and relevant Astro guidance.

## 6. Scope

Included: shared document shell, global base styles/tokens, gallery/brand assets, font delivery/fallback decision, focus defaults, semantic image conventions. Excluded: page-specific compositions, backend/API/state, hydration, interactive map behavior, social destinations, unrelated refactors.

## 7. Repository Context

`SRC-REPO-002` is the minimal Astro starter using Astro `^7.2.2`, Node `24.x`, pnpm, static output, and `frontend/vercel.json`. Stage 9 proved current `main` retains the identical frontend tree `e3af997b8fdf9beb136b8f78561adf1d2c4d2d17`.

## 8. Files and Modules

- `frontend/src/layouts/Layout.astro` — modify into the shared document shell; route files retain `<main>` and heading ownership.
- `frontend/src/styles/global.css` — create semantic global tokens/base rules.
- `frontend/src/assets/gallery/` — approved raster assets.
- `frontend/src/assets/brand/` — logo, marker, and social artwork.
- `frontend/src/assets/fonts/` — only authoritative distributable Big Shoulders Display 900/800 and Outfit 300 files.

## 9. Dependencies and Interfaces

No task prerequisites. Static Astro rendering is the compatibility boundary. `PLAN-001` is the canonical trace item.

## 10. Implementation Steps

1. Reverify source/repository inputs and complete the required frontend guidance preflight.
2. Inspect starter layout/assets and current repository conventions.
3. Export/classify approved artwork as meaningful or decorative.
4. Define semantic CSS tokens/base layout/focus/overflow rules from approved design values.
5. Resolve typography delivery: use authoritative local files, or use the approved fallback stacks only with the documented fidelity stop/deviation path.
6. Refactor `Layout.astro` into the shared document shell with route metadata support while preserving page-owned landmarks/headings.
7. Run declared validation and record implementation-output lineage.

No implementation code is included in this decomposition.

## 11. State, Responsive, and Accessibility Requirements

Static/default only; missing required assets/fonts are blockers or explicit deviations, not UI states. Establish fluid intrinsic constraints supporting 375/768/1440 without treating anchors as automatic breakpoints. Preserve logical DOM order, semantic document structure, visible focus defaults, and meaningful/decorative image semantics.

## 12. Validation

- **Astro build — Build, required:** `pnpm build` from `frontend/` succeeds without missing asset/font failures.
- **Foundation semantics — Accessibility, required:** page-owned `<main>`/heading structure, image semantics, and focus defaults remain correct.
- **Foundation visual inputs — Visual, required:** approved colors/spacing/type roles/assets are represented; typography fidelity is backed by authoritative fonts or explicitly blocked/accepted as a deviation.

All checks remain `Not executed` until Stage 10.

## 13. Acceptance Criteria

- [x] `PLAN-001` objective and referenced Must behavior are implemented.
- [x] Accessibility/responsive requirements are verified.
- [x] All required validation passes with evidence.
- [x] Task-start verification and output snapshot lineage are recorded.
- [x] Discoveries/deviations are documented.

## 14. Risks and Considerations

- High: authoritative font binaries/source metadata are absent. Resolve them before typography fidelity acceptance, otherwise block or obtain explicit owner-approved fallback deviation.
- Low: exact exported asset filenames/formats are implementation details; preserve approved roles and semantics.

## 15. Implementation Discoveries

- Resolved the font-fidelity stop condition with pinned Google Fonts binaries and their SIL Open Font License files.
- Retained source-controlled desktop/tablet/mobile art-direction variants and documented meaningful/decorative image conventions.
- Applied the required modern-web guidance before HTML/CSS edits: stable font fallbacks, semantic ownership, visible focus defaults, and no client hydration.

## 16. Deviations

None. No owner-approved deviation is required.

## 17. Output Lineage

Parent task-start snapshot, implementation-output snapshot, output commit, validation status, and downstream approval are pending Stage 10.

## 18. Definition of Done

- [x] Objective and acceptance criteria complete.
- [x] Required validation passes.
- [x] Source lineage and documentation updates recorded.
- [x] No unapproved deviation or blocker remains.

## 19. Completion Report

Implementation and all required validations passed; canonical output identity follows from `task complete`.
