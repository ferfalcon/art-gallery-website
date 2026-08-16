---
artifact: PLAN
status: Reviewed
baseline:
  design:
    - SRC-DS-001
  repository:
    - SRC-REPO-002
  runtime: []
  documentation: []
  assets: []
created: 2026-08-15
updated: 2026-08-15
---

# Implementation Plan

## 1. Document Information

- Status: Reviewed; canonical lifecycle is owned by `.workflow/workflow-record.json`.
- Scope: Implement the approved Home and Location experiences in the existing `frontend/` Astro application.
- Last updated: 2026-08-15.
- Source baseline: `SOURCE-BASELINE.md`.
- Repository snapshot: `SRC-REPO-002` (`f28f02bb303a4f486e73e2ca1a326751e6c3fd02`).
- Source documents:
  - `PROJECT-CONTEXT.md`
  - `REQUIREMENTS.md`
  - `DESIGN.md`
  - `SPEC.md`
  - `ARCHITECTURE.md`
  - `DOCUMENT-REVIEW.md`

Stage 7 planning reverified `SRC-DS-001` and `SRC-REPO-002` through `VER-013` and `VER-014`. The active implementation input remains the Astro starter plus the approved `frontend/vercel.json` ignored-build configuration. This plan introduces no implementation code.

## 2. Objective and Scope

Translate the approved product, design, specification, and architecture decisions into small repository-aware implementation increments that can later be decomposed into Stage 9 tasks.

### Included

- Replace the Astro starter presentation with the approved two-route static website.
- Establish source-controlled design tokens, typography delivery, and gallery assets without adding runtime services.
- Build shared native navigation and themed footer presentation.
- Build the Home hero and gallery-content sections.
- Build the Location map hero and location-details sections.
- Integrate `/` and `/location/` with ordinary links and semantic page structure.
- Select responsive transitions from observed layout failure rather than copying Figma anchor widths as automatic CSS breakpoints.
- Integrate accessibility, responsive behavior, image semantics, focus behavior, and relevant validation into the work that creates each feature.
- Validate build, routing, keyboard behavior, reflow, visual fidelity, and Vercel preview behavior.

### Excluded

- Backend/API/persistence/authentication/CMS/analytics/commerce/booking/personalization.
- Client-side routing, application state, hydrated UI islands, or JavaScript added only for presentation.
- Interactive map APIs, geolocation, map controls, or routing services.
- Social destinations or social-link interaction until an authoritative destination is supplied.
- Additional routes or content not approved by the current artifacts.
- Changes to Figma outside the authorized `🤖 Workflow` scope.

## 3. Current Repository State

Observed at `SRC-REPO-002`:

- `frontend/package.json` declares Astro `^7.2.2`, Node.js `24.x`, pnpm, and only `dev`, `build`, `preview`, and `astro` scripts.
- `frontend/astro.config.mjs` is the default static Astro configuration; no server adapter or framework integration exists.
- `frontend/src/pages/index.astro` is the starter page and renders `Welcome.astro`.
- `frontend/src/layouts/Layout.astro` is the starter document shell with the title `Astro Basics`.
- `frontend/src/components/Welcome.astro` is starter content and has no authority for the approved site.
- `frontend/src/assets/` contains only starter `astro.svg` and `background.svg`; required gallery, map, logo, marker, social, and font assets are not yet source-controlled.
- There is no `src/styles/` directory, shared token layer, test framework, client-state library, API layer, or application JavaScript pattern to preserve.
- `frontend/vercel.json` is an existing approved file and must remain unchanged unless deployment validation demonstrates a separate need.
- `frontend/AGENTS.md` requires background-mode Astro development when the dev server is used.
- The repository has no confirmed lint/test script. Stage 7 therefore does not invent `pnpm lint` or `pnpm test`; `pnpm build` is the confirmed repository validation command.

The current structure is intentionally minimal. Proposed component/style/asset paths below are implementation choices justified by the approved architecture, not existing conventions.

## 4. Technical Approach

### Component and module boundaries

Use Astro components with no hydration:

- Keep `src/pages/index.astro` as Home route composition.
- Create `src/pages/location.astro` for `/location/`.
- Modify `src/layouts/Layout.astro` into the shared document shell with page-title support and global styles.
- Create one shared native-link component for the two primary navigation actions.
- Create one shared Footer component with explicit `dark` and `gold` themes.
- Create page-section components only where the approved design exposes stable composition boundaries: Home Hero, Gallery Content, Map Hero, and Location Details.
- Remove starter `Welcome.astro` once no route imports it.

### Data and state flow

All content is static and authored in page/section markup. There is no client or server state, data fetching, persistence, loading state, or dynamic error state. Broken imports, missing required assets, or broken routes are implementation defects.

### Styling and design-system integration

- Create a shared `src/styles/global.css` layer for reset/base rules, color/typography/spacing custom properties, focus defaults, and reusable layout constraints.
- Keep section-specific layout CSS scoped to the owning Astro component unless a value is truly shared.
- Translate approved design values into semantic CSS custom properties rather than reproducing Figma layer names mechanically.
- Prefer Grid/Flexbox, intrinsic sizing, `min()`, `max()`, `clamp()`, and content-sized constraints over page-level absolute positioning.
- Absolute positioning is acceptable only for local overlays that are structurally evidenced, such as the marker/action composition over static map artwork.

### Responsive strategy

The 1440 px, 768 px, and 375 px Figma frames are visual validation anchors, not automatic breakpoints. Each owning component will begin from a fluid layout, then select a transition at the narrowest width where the current composition would otherwise cause a documented layout failure. The chosen values will be recorded during implementation and checked immediately on both sides of each transition.

### Accessibility strategy

- Use semantic landmarks and heading order in the page compositions.
- Implement primary navigation as ordinary `<a>` elements so pointer and keyboard activation are native.
- Reproduce visible hover/focus intent with `:hover` and `:focus-visible`; do not hide browser focus without an equivalent.
- Keep social artwork non-interactive and outside the tab order until destinations are approved.
- Assign alt text only where an image conveys meaningful content; mark decorative/redundant artwork accordingly.
- Preserve logical DOM order independently of wide-screen visual placement.
- Do not introduce animation unless useful for matching the approved state transition; if introduced, suppress non-essential motion under `prefers-reduced-motion`.

### Error and state handling

Approved runtime states are static/default plus primary-link hover/focus. There are no loading, empty, disabled, success-message, or recoverable application-error states. Missing static content/assets and broken navigation fail validation rather than receiving invented UI.

### Testing and validation strategy

- Run the confirmed `pnpm build` from `frontend/`.
- Start development only with the repository-required background mode when interactive browser validation is needed.
- Verify both routes and bidirectional native navigation.
- Validate keyboard reachability, activation, visible focus, landmarks/headings, image semantics, social non-interactivity, and logical order.
- Compare rendered pages against all six approved Figma frames at 1440, 768, and 375 px.
- Test representative intermediate widths and widths immediately around each selected layout transition.
- Check for page-level horizontal scrolling and content loss.
- Verify the PR preview on Vercel for frontend-changing implementation PRs. Documentation-only planning PRs may legitimately skip a Vercel build under the existing configuration.

## 5. Files and Modules

| Path | Action | Existing or proposed | Responsibility | Repository evidence |
|---|---|---|---|---|
| `frontend/src/layouts/Layout.astro` | Modify | Existing | Shared document shell, metadata, global style import, base landmarks/defaults | Starter shell exists in `SRC-REPO-002` |
| `frontend/src/styles/global.css` | Create | Proposed | Reset/base rules, semantic design tokens, typography declarations, focus defaults, shared sizing constraints | No shared style layer exists; `ARCHITECTURE.md` requires shared tokens |
| `frontend/src/components/PrimaryAction.astro` | Create | Proposed | Native `OUR LOCATION` / `BACK TO HOME` link presentation and focus/hover treatment | Repeated navigation responsibility approved in architecture |
| `frontend/src/components/Footer.astro` | Create | Proposed | Shared footer content with Dark/Gold themes and responsive layout | Repeated Footer resource exists in `SRC-DS-001` |
| `frontend/src/components/HomeHero.astro` | Create | Proposed | Home hero content, imagery, CTA, responsive transformation | Hero is a stable reusable source composition |
| `frontend/src/components/GalleryContent.astro` | Create | Proposed | Home editorial sections and gallery imagery | Gallery Content is a stable source composition |
| `frontend/src/components/MapHero.astro` | Create | Proposed | Static map artwork, marker, return CTA, responsive crop/overlay | Map Hero is a stable source composition |
| `frontend/src/components/LocationDetails.astro` | Create | Proposed | Location heading, address, visit copy, responsive columns/stack | Location Details is a stable source composition |
| `frontend/src/pages/index.astro` | Modify | Existing | Compose semantic Home route | Starter Home route exists |
| `frontend/src/pages/location.astro` | Create | Proposed | Compose semantic Location route | Architecture approves `/location/` |
| `frontend/src/assets/gallery/` | Create/populate | Proposed collection | Source-controlled hero/gallery/map raster assets; exact filenames/formats follow source exports | Required assets absent from `SRC-REPO-002` |
| `frontend/src/assets/brand/` | Create/populate | Proposed collection | Logo, marker, and social vector artwork; exact filenames follow source exports | Required vectors absent from `SRC-REPO-002` |
| `frontend/src/assets/fonts/` | Create/populate if authoritative local files are available | Proposed/conditional | Source-controlled font delivery | Architecture requires local delivery when legally available; files are not yet in repo |
| `frontend/src/components/Welcome.astro` | Delete | Existing | Remove unused Astro starter component after route replacement | Starter-only component |
| `frontend/src/assets/astro.svg` | Delete when unused | Existing | Remove unused starter asset | Starter-only asset |
| `frontend/src/assets/background.svg` | Delete when unused | Existing | Remove unused starter asset | Starter-only asset |
| `frontend/vercel.json` | Preserve | Existing | Keep ignored-build behavior for changes outside project root | Approved PR #7 / `SRC-REPO-002` |

Exact individual asset filenames and font filenames are deliberately not invented at planning time.

## 6. Plan Items

### PLAN-001 — Establish source-controlled visual foundation and shared page shell

- **Objective:** Replace starter-level document styling with the shared implementation foundation needed by both routes.
- **Requirement and specification references:** `REQ-DR-001`, `REQ-AR-001`, `REQ-AR-004`, `REQ-CON-001`, `REQ-CON-002`, `REQ-FR-007`; `SPEC-BEH-005`, `SPEC-ACC-001`, `SPEC-ACC-003`.
- **Source snapshots:** `SRC-DS-001`, `SRC-REPO-002`.
- **File impact:** Modify `Layout.astro`; create `global.css`; populate proposed asset collections; conditionally populate `assets/fonts/`.
- **Dependencies:** None.
- **Implementation approach:** Export approved source artwork into source-controlled assets, classify meaningful/decorative images, define shared semantic CSS tokens, establish typography delivery, and make Layout accept route-specific metadata while preserving static Astro output.
- **Integrated accessibility, responsive, state, and error work:** Establish base semantic document defaults, accessible image conventions, robust box sizing, overflow prevention, focus defaults, and fluid page constraints. Missing required assets/fonts are treated as implementation blockers for fidelity, not runtime fallback states.
- **Validation:** Confirm every required asset role has an implementation input; check font rendering/fallback; inspect document metadata/landmarks; run `pnpm build`.
- **Risks:** Font files/licensing are not currently in the repo. If authoritative local files cannot be obtained from the approved project inputs, use the documented fallback strategy without adding an unapproved runtime dependency and record the fidelity impact.

### PLAN-002 — Implement shared primary navigation and themed Footer

- **Objective:** Provide the repeated navigation and footer responsibilities once, with source-accurate themes and accessible semantics.
- **Requirement and specification references:** `REQ-FR-003`, `REQ-FR-004`, `REQ-FR-005`, `REQ-AR-002`, `REQ-AR-003`, `REQ-AR-004`, `REQ-AR-006`; `SPEC-BEH-004`, `SPEC-INT-001`, `SPEC-INT-002`, `SPEC-INT-003`, `SPEC-ACC-002`.
- **Source snapshots:** `SRC-DS-001`, `SRC-REPO-002`.
- **File impact:** Create `PrimaryAction.astro` and `Footer.astro`; consume shared tokens/assets from PLAN-001.
- **Dependencies:** `PLAN-001`.
- **Implementation approach:** Implement primary actions as native anchors with label/direction/theme inputs only; implement Footer with explicit Dark/Gold theme input and static social artwork.
- **Integrated accessibility, responsive, state, and error work:** Native keyboard activation, visible `:focus-visible`, pointer hover, no fake social links/tab stops, coherent stacked/horizontal footer order, and `prefers-reduced-motion` handling only if transition motion is introduced.
- **Validation:** Keyboard-only activation and focus review; inspect accessibility tree for social artwork; compare default/hover/focus and footer themes at source anchors; test footer transition around actual layout failure.
- **Risks:** Future social destinations would require a specification/architecture impact review rather than silently changing artwork into links.

### PLAN-003 — Implement the complete Home route

- **Objective:** Replace the starter Home experience with the approved Home hero, editorial gallery content, navigation, and dark footer.
- **Requirement and specification references:** `REQ-FR-001`, `REQ-FR-003`, `REQ-FR-006`, `REQ-FR-007`, `REQ-AR-001`, `REQ-AR-005`, `REQ-NFR-001`, `REQ-NFR-002`; `SPEC-BEH-001`, `SPEC-BEH-005`, `SPEC-BEH-006`, `SPEC-INT-001`, `SPEC-ACC-001`, `SPEC-ACC-003`.
- **Source snapshots:** `SRC-DS-001`, `SRC-REPO-002`.
- **File impact:** Create `HomeHero.astro` and `GalleryContent.astro`; modify `pages/index.astro`; use shared `PrimaryAction` and Footer; remove Home-related starter imports.
- **Dependencies:** `PLAN-001`, `PLAN-002`.
- **Implementation approach:** Keep semantic reading order in markup, compose image/text relationships with Grid/Flexbox, preserve editorial hierarchy and crops, and allow copy to wrap naturally.
- **Integrated accessibility, responsive, state, and error work:** Meaningful section headings, logical link order, image alt/decorative classification, no content hiding for fit, mobile stacking before layout failure, and no horizontal page scroll.
- **Validation:** Visual comparison at Home 1440/768/375; keyboard navigation to `OUR LOCATION`; representative intermediate widths; transition-boundary checks; zoom/reflow sanity check; `pnpm build`.
- **Risks:** Desktop editorial composition is visually asymmetric; CSS must preserve the hierarchy without coupling semantic order to absolute coordinates.

### PLAN-004 — Implement the complete Location route

- **Objective:** Add the approved Location route with static map composition, return navigation, address/visit content, and gold footer.
- **Requirement and specification references:** `REQ-FR-002`, `REQ-FR-004`, `REQ-FR-006`, `REQ-FR-007`, `REQ-AR-001`, `REQ-AR-005`, `REQ-NFR-001`, `REQ-NFR-002`; `SPEC-BEH-002`, `SPEC-BEH-003`, `SPEC-BEH-005`, `SPEC-BEH-006`, `SPEC-INT-002`, `SPEC-ACC-001`, `SPEC-ACC-003`.
- **Source snapshots:** `SRC-DS-001`, `SRC-REPO-002`.
- **File impact:** Create `MapHero.astro`, `LocationDetails.astro`, and `pages/location.astro`; use shared `PrimaryAction` and Footer.
- **Dependencies:** `PLAN-001`, `PLAN-002`.
- **Implementation approach:** Render map as static artwork with local marker/action overlay, keep address text outside the map, compose details as responsive columns that stack before readability failure, and preserve Location footer spacing/theme.
- **Integrated accessibility, responsive, state, and error work:** Map must not expose interactive-map affordances; `BACK TO HOME` remains a native link; marker/artwork semantics are classified appropriately; overlay stays visible and operable; mobile footer spacing preserves the demonstrated Gold variant.
- **Validation:** Visual comparison at Location 1440/768/375; keyboard activation back to Home; inspect map semantics/non-interactivity; intermediate crop/overlay checks; transition-boundary checks; no horizontal scroll; `pnpm build`.
- **Risks:** Map crop/overlay changes materially by viewport. Adapt conservatively and validate subject/marker/action visibility rather than inventing continuous interpolation.

### PLAN-005 — Integrate routes, remove starter residue, and complete regression/preview validation

- **Objective:** Deliver a coherent two-page static build and prove that shared changes did not regress either route.
- **Requirement and specification references:** All Must requirements, especially `REQ-FR-003`–`REQ-FR-006`, `REQ-AR-001`–`REQ-AR-005`, `REQ-NFR-001`, `REQ-NFR-002`, `REQ-CON-003`; `SPEC-BEH-006`, `SPEC-INT-001`–`SPEC-INT-003`, `SPEC-VAL-001`, `AC-001`–`AC-017` as applicable.
- **Source snapshots:** `SRC-DS-001`, `SRC-REPO-002`.
- **File impact:** Both route compositions and shared components/styles; delete unused `Welcome.astro`, `astro.svg`, and `background.svg` when confirmed unreferenced. Preserve `frontend/vercel.json`.
- **Dependencies:** `PLAN-003`, `PLAN-004`.
- **Implementation approach:** Verify bidirectional routing and shared-component behavior, remove starter-only files, then run final build/browser/visual/accessibility checks against the same implementation commit.
- **Integrated accessibility, responsive, state, and error work:** This item verifies rather than first introduces semantics/focus/reflow. Correct any residual regression in the owning component rather than layering a separate accessibility or responsive patch.
- **Validation:** `pnpm build`; both routes; native navigation; keyboard/focus pass; semantic/image/social checks; six-anchor visual comparison; intermediate widths including either side of selected transitions; horizontal-overflow check; PR Vercel preview and deployment status.
- **Risks:** Shared token/component corrections can affect both pages; recheck both routes after every cross-cutting adjustment.

## 7. Recommended Phase Shape

### Phase 1 — Shared accessible foundation

- `PLAN-001`
- `PLAN-002`

Produces source-controlled inputs, global tokens/shell, native navigation, and shared Footer with accessibility/state behavior integrated.

### Phase 2 — Page implementation

- `PLAN-003`
- `PLAN-004`

Home and Location may proceed in parallel after shared interfaces are stable because they primarily own separate section and route files.

### Phase 3 — Integration and final validation

- `PLAN-005`

Performs cleanup and regression/preview verification; it does not defer first-time accessibility or responsive implementation.

## 8. Responsive Decision Process

For Hero, Gallery Content, Location Details, Map Hero, and Footer:

1. Use the corresponding 1440/768/375 `SRC-DS-001` frames as visual evidence.
2. Implement the wider/current composition fluidly without assigning the Figma width itself as a breakpoint.
3. Narrow/widen until a defined failure appears: collision, clipping, unreadable compression, loss of important subject/action visibility, or page-level horizontal scrolling.
4. Select the narrowest justified transition that prevents the failure while preserving the source hierarchy.
5. Test at the selected value, immediately below and above it, and at representative intermediate widths.
6. Recheck text zoom/reflow and natural copy wrapping.
7. Record the final CSS transition value and rationale in the implementation/task evidence.

The plan intentionally leaves exact breakpoint numbers unresolved until the rendered components provide the required evidence.

## 9. Dependencies and Ordering

| Plan item | Depends on | May run in parallel | Reason |
|---|---|---|---|
| `PLAN-001` | — | No | Both pages require shared assets/tokens/shell |
| `PLAN-002` | `PLAN-001` | No | Shared controls/footer consume the foundation |
| `PLAN-003` | `PLAN-001`, `PLAN-002` | Yes, with PLAN-004 | Home owns distinct page-section files |
| `PLAN-004` | `PLAN-001`, `PLAN-002` | Yes, with PLAN-003 | Location owns distinct page-section files |
| `PLAN-005` | `PLAN-003`, `PLAN-004` | No | Integration validation needs both routes complete |

## 10. Architecture Handling

- Separate `ARCHITECTURE.md`: **Required**.
- Reason: Stage 6 approved static Astro routing, component dependency boundaries, asset/font delivery, responsive/accessibility ownership, low-JavaScript policy, build/deployment behavior, and test boundaries.
- This plan implements those decisions without reopening architecture.

## 11. Migration, Compatibility, Deployment, and Rollback

- There is no data/schema migration.
- Replacing Astro starter markup is a direct content implementation, not a compatibility migration.
- Keep Node `24.x`, pnpm, Astro static output, and existing package scripts unless a later approved need requires change.
- Preserve `frontend/vercel.json`; frontend implementation commits should trigger Vercel preview deployment because they change the project root.
- Implementation uses the required branch → PR → preview → verification → merge flow.
- Rollback is Git-based: revert the implementation PR/commit. No database or runtime migration rollback exists.
- No new secrets, remote scripts, tracking, or user-data collection are planned.

## 12. Source-change Handling

- **Snapshot verification required before implementation:** reverify mutable `SRC-DS-001`; verify the task-start repository commit descends from or explicitly rebaselines `SRC-REPO-002`.
- **Material changes that invalidate this plan:** new/removed routes; changed approved content hierarchy; new interactions/social destinations; interactive map requirement; major component/responsive changes; framework/runtime/deployment-policy changes; new authoritative asset/font constraints.
- **Earliest stage to revisit:** requirements/design/specification for product/design behavior changes; Stage 6 for structural/runtime changes; Stage 7 for repository-only file/convention changes that do not alter approved behavior.
- New source content must receive a new snapshot ID and rebaseline impact assessment rather than silently updating this plan.

## 13. Risks and Open Questions

| Risk or question | Impact | Blocking | Mitigation or owner |
|---|---|---|---|
| Authoritative local font files/licensing are not represented in the repository | Typography fidelity may differ | No at planning; may block affected implementation validation | Resolve during `PLAN-001`; prefer approved/source-controlled local files, otherwise document fallback/fidelity impact |
| Individual asset export filenames/formats are not yet repository inputs | Cannot name exact imports in Stage 7 | No | Export from approved Figma source during `PLAN-001`; record concrete paths in Stage 9 tasks |
| Exact responsive transition values are intentionally unknown until rendered | Poor choices could break intermediate widths | No | Determine from layout failure in owning plan item and validate both sides |
| Map crop/overlay interpolation is underspecified | Location may diverge between anchors | No | Conservative crop/overlay adaptation plus intermediate validation |
| Social destinations remain unknown | Accidental fake links would be incorrect/a11y-hostile | No | Keep marks non-interactive until authoritative scope changes |
| Shared visual corrections may regress the other route | Cross-page visual/a11y regression | No | `PLAN-005` rechecks both routes after shared changes |
| No repository test/lint script is currently defined | Cannot claim automated checks that do not exist | No | Use confirmed `pnpm build` plus browser/manual validation; do not add test tooling solely for static markup without demonstrated value |

No blocking Stage 7 question remains.

## 14. Definition of Done

- [x] Every Must requirement and material specification has an implementation path.
- [x] Every plan item has file impact, dependencies, integrated quality work, validation, and risks.
- [x] Existing and proposed paths are explicitly distinguished.
- [x] Accessibility and responsive behavior are integrated into the work that creates the relevant UI.
- [x] Only repository-confirmed commands are named.
- [x] Migration, deployment, rollback, security, and privacy implications are addressed.
- [x] Snapshot IDs exist and the pinned repository commit was reverified.
- [x] No unsupported capability, arbitrary breakpoint, social destination, or dynamic state has been invented.
- [x] Two Stage 7 review passes are complete.
- [ ] Project-owner approval and the Stage 7 gate are still required before Stage 8.

## 15. Review

### Pass 1 — Feasibility and completeness

- [x] The plan reflects `SRC-REPO-002`: Astro starter structure, package/runtime constraints, existing scripts, no test framework, and existing Vercel ignore-build config.
- [x] Scope and technical approach implement the approved static two-route architecture without unnecessary JavaScript or services.
- [x] File/module impact clearly distinguishes existing paths from proposed paths.
- [x] Ordering has real prerequisites and permits Home/Location parallelism only after shared interfaces exist.
- [x] Semantics, keyboard/focus, image behavior, responsive transitions, state handling, and validation are integrated into owning plan items.
- [x] Each plan item produces a meaningful, verifiable result and is small enough for Stage 9 decomposition.

**Pass 1 result:** Passed. No feasibility or completeness blocker found.

### Pass 2 — Consistency, traceability, source integrity, risks, and uncertainty

- [x] `PLAN-*` identifiers follow the workflow conventions.
- [x] Every plan item maps to approved `REQ-*` and `SPEC-*` ownership.
- [x] `SRC-DS-001` and `SRC-REPO-002` were freshly reverified for planning (`VER-013`, `VER-014`).
- [x] The architecture decision remains Required and the plan does not contradict Stage 6.
- [x] Exact breakpoint values, asset filenames/formats, font delivery details, and social destinations are not invented.
- [x] The 1440/768/375 widths remain validation anchors rather than automatic CSS breakpoints.
- [x] Risks and non-blocking uncertainties remain visible with explicit mitigation.
- [x] No implementation code or Stage 8/9 work has been started.

**Pass 2 result:** Passed. `ART-PLAN` is ready for explicit project-owner approval.
