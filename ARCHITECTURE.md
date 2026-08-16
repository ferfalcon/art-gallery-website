---
artifact: ARCHITECTURE
status: Reviewed
baseline:
  design:
    - SRC-DS-001
  repository:
    - SRC-REPO-002
  runtime:
    - SRC-RUN-001
  documentation: []
  assets: []
created: 2026-08-15
updated: 2026-08-15
---

# Architecture

## 1. Document Information

- Status: Reviewed; canonical lifecycle is owned by `.workflow/workflow-record.json`.
- Version: 0.1
- Last updated: 2026-08-15
- Owner: ChatGPT
- Scope: Home and Location experiences represented on the approved `🤖 Workflow` Figma page and implemented in `frontend/`.
- Source baseline: `SOURCE-BASELINE.md`
- Repository snapshot: `SRC-REPO-002`
- Runtime snapshot: `SRC-RUN-001`
- Related documents:
  - `REQUIREMENTS.md`
  - `DESIGN.md`
  - `SPEC.md`
  - `DOCUMENT-REVIEW.md`
  - `WORKFLOW-STATE.md`

Stage 6 explicitly records architecture as **Required**. Although the product is a small static site, the implementation has meaningful routing, shared presentation boundaries, asset/font delivery, responsive composition, accessibility ownership, and Vercel build/deployment decisions that should be protected before planning.

## 2. Purpose and Scope

This document owns structural technical decisions for the approved two-page Astro implementation.

### Included

- Astro rendering and routing boundaries.
- Page and shared-component responsibilities.
- Static content, asset, and design-token ownership.
- Responsive and accessibility responsibilities that cross component boundaries.
- Build and deployment boundaries relevant to `frontend/` and Vercel.
- Testing boundaries needed to validate the approved design and specification.

### Excluded

- Backend services, APIs, persistence, authentication, CMS, analytics, commerce, booking, personalization, and server-side business logic.
- Interactive maps, geolocation, routing services, or third-party map SDKs.
- Social-network destinations that have not been approved by an authoritative source.
- Additional routes beyond Home and Location.
- Exact implementation task order or filenames beyond architecturally significant boundaries; those belong to Stage 7 planning.

## 3. Evidence and Sources

### Confirmed and observed inputs

- `SRC-DS-001`: approved Figma `🤖 Workflow` page with Home and Location at 1440 px, 768 px, and 375 px plus reusable Hero, Gallery Content, Location Details, Map Hero, Footer, navigation, imagery, and style-guide resources.
- `SRC-REPO-002`: current repository input at commit `f28f02bb303a4f486e73e2ca1a326751e6c3fd02`.
- `SRC-RUN-001`: time-bound Vercel project observation used only for current hosting/runtime context.
- Approved behavioral ownership remains in `REQUIREMENTS.md`, `DESIGN.md`, and `SPEC.md`.

### Repository paths inspected from `SRC-REPO-002`

- `frontend/package.json`
- `frontend/astro.config.mjs`
- `frontend/src/`
- `frontend/src/pages/`
- `frontend/src/components/`
- `frontend/AGENTS.md`
- `frontend/vercel.json`

### Source-change note

`SRC-REPO-001` remains the immutable Stage 0 implementation baseline used by Stages 0–5. After Stage 5, approved PR #7 added `frontend/vercel.json`; that change is recorded as `SRC-REPO-002`. It affects build/deployment architecture and later planning, but it does not invalidate the already-approved product, design, or behavioral artifacts.

## 4. System Context

```text
Visitor
  → statically generated Art gallery website
    → local/source-controlled HTML, CSS, fonts, and image assets
      → Vercel static hosting

No application API, database, authentication service, analytics service,
interactive map service, or social-network integration is in approved scope.
```

- **User boundary:** public visitors navigate between Home and Location.
- **Application boundary:** the Astro site under `frontend/`.
- **External runtime boundary:** Vercel serves the generated site.
- **Trust boundary:** no user-submitted data, credentials, sessions, or secrets are required by the approved product scope.

## 5. Architectural Goals

1. **Fidelity without unnecessary runtime complexity.** Preserve the approved visual/responsive intent while favoring static HTML and CSS.
2. **Accessible structure by default.** Page semantics, native navigation, document order, and reusable focus behavior are structural responsibilities, not cleanup work.
3. **Small, explicit component boundaries.** Reuse stable repeated presentation patterns while keeping page-specific composition understandable.
4. **Responsive behavior based on layout failure.** Figma widths are validation anchors, not automatic CSS breakpoints.
5. **Source-controlled, deterministic delivery.** Required assets and fonts should not depend on unapproved runtime services.
6. **Simple deployment.** Use Astro's static build and the existing Vercel project/runtime contract without adding a server runtime.
7. **Low JavaScript surface.** Do not hydrate components unless approved behavior cannot be implemented with semantic HTML/CSS.

## 6. Current Architecture

### Observed in `SRC-REPO-002`

- `frontend/` is an Astro application using Astro `^7.2.2`, TypeScript configuration, pnpm, and Node.js `24.x`.
- `astro.config.mjs` is currently the default `defineConfig({})`; no adapter or server output is configured.
- `src/pages/` currently contains only the starter `index.astro`.
- `src/components/` currently contains only the starter `Welcome.astro`.
- Existing starter layout/assets structure is not yet the approved Art Gallery implementation.
- There is no backend package, API layer, persistence layer, client-state library, or framework integration.
- `frontend/vercel.json` contains the Vercel ignored-build command `git diff --quiet HEAD^ HEAD ./`, matching the repository policy that documentation-only commits outside the Vercel project root should not trigger a build.

### Supporting runtime observation from `SRC-RUN-001`

- The connected Vercel project reports Node.js `24.x`.
- At capture time it had a READY production deployment.
- This observation is not an implementation validation runtime and does not prove Stage 6 architecture has been implemented.

## 7. Target and Transitional Architecture

### Target

A statically generated Astro site with two ordinary routes:

- Home: `/`
- Location: `/location/`

The target uses semantic Astro components, local/source-controlled assets, CSS-driven responsive layouts, and native links for bidirectional navigation. It requires no client-side state or application JavaScript for approved behavior.

### Transitional

The current Astro starter content is replaced incrementally during implementation. Existing starter `Welcome.astro` and starter page composition have no architectural authority and may be removed when tasks implement the approved site.

No compatibility layer, migration service, data migration, or dual-runtime transition is required.

## 8. High-Level Structure

```text
Astro page routes
  → page composition
    → shared layout and shared presentation primitives
      → page-specific sections
        → source-controlled assets and CSS tokens

Astro build
  → static output
    → Vercel deployment
```

The architecture intentionally avoids application layers that solve no approved problem.

## 9. Components and Responsibilities

### Page routes

**Responsibilities**
- Own the route URL, page title/metadata, page-level landmark structure, and section composition.
- Keep Home and Location reading order coherent independent of wide-layout visual positioning.

**Must not**
- Duplicate shared footer/navigation behavior unnecessarily.
- Introduce data fetching, state stores, or client hydration for static content.

### Shared layout

**Responsibilities**
- Own document shell concerns shared by both pages: base HTML metadata, global styles/tokens, and common structural defaults.

**Must not**
- Encode page-specific content or force both pages into identical section spacing where the design intentionally differs.

### Primary navigation action

**Responsibilities**
- Render native page navigation with the approved label, arrow treatment, hover state, and visible focus state.
- Support both `OUR LOCATION` and `BACK TO HOME` presentation without changing native link semantics.

**Must not**
- Behave like a menu, modal trigger, SPA router control, or JavaScript-only button.

### Footer

**Responsibilities**
- Own the repeated logo, descriptive copy, social-brand artwork, responsive layout, and Dark/Gold visual themes.

**Must not**
- Invent social destinations.
- Make social marks keyboard-focusable until authoritative destinations exist.

### Home sections

A Home Hero and Gallery Content boundary may be used because the approved Figma source exposes these as stable reusable compositions across desktop/tablet/mobile.

**Responsibilities**
- Preserve approved content hierarchy, image roles, and responsive transformations.

**Must not**
- Become a generic design-system abstraction for unrelated future pages.

### Location sections

Map Hero and Location Details boundaries may be used because the approved source exposes them as stable compositions.

**Responsibilities**
- Keep the map informational/static.
- Keep textual address and visit information independent from interpretation of the map artwork.
- Keep `BACK TO HOME` visible and operable across responsive conditions.

**Must not**
- Add map controls, geolocation, third-party map APIs, or routing behavior.

## 10. Dependency Rules

1. `src/pages/` may compose shared and page-specific Astro components.
2. Page-specific sections may depend on shared presentation primitives and shared design tokens.
3. Shared presentation primitives must not import page-specific sections or page content.
4. Static assets may be imported by components/pages that render them; assets must not own behavior.
5. CSS/token definitions may be shared downward; page-specific CSS must not silently redefine global semantic tokens for unrelated components.
6. No approved feature may require a backend, API client, persistence adapter, authentication module, or state store.
7. Client-side JavaScript is prohibited by default; introducing hydration requires a concrete approved interaction that cannot be expressed with native HTML/CSS and must trigger architecture impact review.

## 11. Important Data and Interaction Flows

### Home → Location

```text
Visitor activates native `OUR LOCATION` link
  → browser performs ordinary navigation
    → `/location/` static page loads
```

No client router, shared state, or side effect is required.

### Location → Home

```text
Visitor activates native `BACK TO HOME` link
  → browser performs ordinary navigation
    → `/` static page loads
```

### Static content and assets

```text
Repository content/assets
  → Astro build
    → generated static HTML/CSS/assets
      → Vercel delivery
```

Missing required content or assets is a build/implementation defect rather than an approved runtime empty/error state.

## 12. State and Data Ownership

- **Persistent application state:** none.
- **Server state:** none.
- **Client application state:** none.
- **Authoritative editorial content for current scope:** approved project documentation/design source and implementation files created from it.
- **Map:** static visual asset plus independent textual address content.
- **Social destinations:** absent; social marks remain non-interactive artwork.
- **Caching/synchronization/concurrency:** no application-level mechanism is required.
- **Sensitive data:** none is collected or persisted by the approved implementation.

## 13. Frontend Architecture

### Routing

Use Astro file-based routing with one page for `/` and one page for `/location/`. Ordinary `<a>` navigation fulfills the approved behavior and preserves browser expectations.

### Rendering

Use Astro's static output. No adapter/server rendering or hydrated island is required for the approved static experience.

### Styling and design-system integration

- Represent stable approved color, typography, and spacing values as CSS custom properties or equivalent shared CSS tokens.
- Keep structural page/section styles close to the component that owns the layout.
- Prefer CSS Grid/Flexbox and intrinsic/fluid sizing over absolute page positioning.
- Select responsive transition thresholds from actual layout failure. The 1440/768/375 Figma compositions remain visual validation anchors.
- Do not encode Figma component names as a requirement when a simpler semantic code boundary communicates responsibility better.

### Assets and fonts

- Required gallery/map/icon assets should be source-controlled implementation inputs.
- Use the Astro asset pipeline for assets that benefit from build-time optimization/responsive output; use `public/` only for assets that require stable public paths or are not transformed.
- Font delivery should be local/source-controlled when the approved font files are legally available to the project; otherwise Stage 7 must document the authoritative source and fallback strategy before implementation.
- Do not add a runtime map SDK, social SDK, or remote image dependency to reproduce approved static content.

## 14. Backend, API, and Integration Architecture

Not applicable to approved scope.

No backend, API contract, third-party application integration, webhook, background job, or runtime data fetch is required. Adding one is a material scope/architecture change and must not occur during implementation without workflow impact assessment.

## 15. Persistence Architecture

Not applicable. No database, local persistence, cache-backed application state, or migration is required.

## 16. Authentication and Authorization

Not applicable. There are no protected routes, identities, sessions, tokens, roles, or authorization checks in approved scope.

## 17. Accessibility Architecture

Accessibility ownership is distributed with the component that creates the behavior:

- Page routes/layout own landmark and heading hierarchy.
- Primary navigation owns native link semantics, accessible labels, keyboard activation, hover/focus treatment, and focus visibility.
- Section components own meaningful image alternatives or decorative treatment according to image purpose.
- Footer owns non-interactive social artwork semantics and prevents fake link/focus behavior.
- DOM/document order remains logical even when desktop layouts visually reposition content.
- Responsive layout must preserve content and keyboard order without page-level horizontal scrolling.
- Motion is not required. If motion is introduced later, reduced-motion behavior becomes part of the owning component and architecture review.

No custom focus manager, roving tabindex, ARIA widget pattern, or announcement region is required by current behavior.

## 18. Error Handling and Reliability

- There is no approved product-level loading, empty, success-message, or recoverable dynamic-error state.
- Broken routes, missing required assets, invalid imports, or missing required content are implementation/build failures.
- Native browser navigation failure does not receive an invented application recovery UI.
- Static delivery reduces runtime failure surface; reliability validation focuses on successful build, valid routes, asset delivery, and Vercel preview behavior.

## 19. Security and Privacy

Current scope has a minimal attack/data surface:

- no forms or untrusted input;
- no authentication/session data;
- no API secrets;
- no cookies required by application behavior;
- no analytics or personalization;
- no third-party map/social runtime code.

Implementation must not introduce remote scripts, secrets, tracking, or user-data collection merely for visual fidelity. Any future integration changes this section and requires architecture impact assessment.

## 20. Build, Deployment, Runtime, and Observability

### Build

- Package manager: pnpm.
- Runtime contract: Node.js `24.x`.
- Build command: `astro build` through the existing package script.
- Expected output: static site output; no application server is required.

### Vercel

- Vercel project root is `frontend/` according to the project operating contract.
- `frontend/vercel.json` is part of the current repository architecture and defines an ignored build step so changes outside the project root can be skipped.
- Workflow/architecture documentation changes should not require a frontend deployment when that ignore command evaluates the frontend subtree as unchanged.
- Implementation follows branch → pull request → preview/verification → merge. Production is not manually promoted unless explicitly requested.

### Observability

No application observability stack is required for a static two-page site. Build/deployment status and browser validation are sufficient for current scope. Adding runtime logging/analytics would require an approved need and architecture review.

## 21. Testing Architecture

Validation responsibilities align with the boundaries above:

- **Build:** `pnpm build`/Astro build must succeed.
- **Route integration:** `/` and `/location/` must render and link bidirectionally.
- **Accessibility:** semantic landmarks/headings, keyboard navigation, visible focus, image semantics, non-focusable social artwork, and reflow are checked in the rendered site.
- **Responsive:** validate the 1440 px, 768 px, and 375 px evidence anchors plus representative intermediate/narrow/wide widths selected around actual layout-failure points.
- **Visual:** compare rendered pages against the approved Figma compositions; inspect imagery/crops, typography, spacing, color, footer themes, map/marker positioning, and navigation states.
- **Regression:** both routes and shared components are rechecked after shared-token/component changes.
- **Deployment:** verify the PR preview when a frontend change triggers a deployment; a legitimately skipped docs-only deployment is not a failed validation.

No unit-test framework is introduced solely to test static markup unless Stage 7 identifies behavior that benefits from it.

## 22. Architectural Decisions

### ADR-001 — Keep the product a statically generated Astro site

- **Status:** Proposed for Stage 6 owner approval.
- **Context:** Approved scope is two static content pages with ordinary navigation and no dynamic data.
- **Source snapshots:** `SRC-DS-001`, `SRC-REPO-002`.
- **Decision:** Use Astro static rendering and add no server adapter, API layer, state store, or hydrated client framework for current scope.
- **Rationale:** It satisfies all approved behavior with the smallest runtime and failure surface.
- **Alternatives considered:** SPA/client router; SSR/server runtime.
- **Tradeoffs and consequences:** Future dynamic features may require revisiting architecture, but current implementation remains simpler, faster to reason about, and easier to validate.
- **Requirement/specification references:** `REQ-FR-001`–`REQ-FR-007`, `SPEC-BEH-001`–`SPEC-BEH-006`, `SPEC-INT-001`, `SPEC-INT-002`.

### ADR-002 — Use native file-based routes and links

- **Status:** Proposed for Stage 6 owner approval.
- **Context:** The only approved interaction flow is Home ↔ Location.
- **Source snapshots:** `SRC-DS-001`, `SRC-REPO-002`.
- **Decision:** Route Home at `/`, Location at `/location/`, and navigate with semantic anchors.
- **Rationale:** Native navigation directly satisfies keyboard, focus, URL, and browser behavior without client routing.
- **Alternatives considered:** JavaScript click handlers or SPA routing.
- **Tradeoffs and consequences:** Full document navigation is accepted because no cross-route application state exists.
- **Requirement/specification references:** `REQ-FR-003`, `REQ-FR-004`, `REQ-AR-002`, `REQ-AR-003`, `SPEC-INT-001`, `SPEC-INT-002`.

### ADR-003 — Share stable presentation boundaries without building a generic component framework

- **Status:** Proposed for Stage 6 owner approval.
- **Context:** Figma exposes repeated Footer/navigation resources and stable responsive section compositions.
- **Source snapshots:** `SRC-DS-001`, `SRC-REPO-002`.
- **Decision:** Reuse shared layout, navigation, footer, and stable page-section boundaries while retaining page-specific composition.
- **Rationale:** This reduces duplication while keeping the code proportional to a two-page site.
- **Alternatives considered:** Duplicate all page markup; build a broad design-system/component abstraction layer before need exists.
- **Tradeoffs and consequences:** Some page-specific CSS/content remains intentionally local instead of forced into variants.
- **Requirement/specification references:** `SPEC-BEH-001`, `SPEC-BEH-002`, `SPEC-BEH-004`, `SPEC-ACC-001`, `SPEC-ACC-002`.

### ADR-004 — Keep map/social behavior and required visual assets local and static

- **Status:** Proposed for Stage 6 owner approval.
- **Context:** The approved map is informational artwork and social destinations are not authoritative.
- **Source snapshots:** `SRC-DS-001`.
- **Decision:** Use local/source-controlled map, gallery, logo, marker, and social artwork; do not add runtime map/social integrations.
- **Rationale:** This preserves the approved experience without inventing behavior or external dependencies.
- **Alternatives considered:** Map SDK/API, live social links/SDKs, remote runtime asset dependencies.
- **Tradeoffs and consequences:** Map data is not interactive; social artwork remains non-interactive until product documentation changes.
- **Requirement/specification references:** `SPEC-BEH-003`, `SPEC-BEH-004`, `SPEC-INT-003`, `SPEC-ACC-003`.

### ADR-005 — Treat Vercel deployment policy as repository architecture

- **Status:** Proposed for Stage 6 owner approval.
- **Context:** `SRC-REPO-002` added `frontend/vercel.json` after Stage 5 to stop documentation-only changes from consuming frontend deployments.
- **Source snapshots:** `SRC-REPO-002`, `SRC-RUN-001`.
- **Decision:** Preserve the `frontend/` project-root deployment boundary and the repository-managed ignored build step; frontend implementation PRs use Vercel previews when a deployment is triggered.
- **Rationale:** Deployment behavior now affects repository workflow, cost/rate-limit exposure, and validation.
- **Alternatives considered:** deploy every repository commit; manually coordinate deployments outside source control.
- **Tradeoffs and consequences:** Documentation-only PRs may have no Vercel preview by design; implementation PRs that touch `frontend/` remain deployable.
- **Requirement/specification references:** technical/project constraint; no product behavior is changed.

## 23. Constraints, Risks, Assumptions, and Open Questions

| Item | Type | Impact | Evidence or snapshot | Mitigation or owner | Status |
|---|---|---|---|---|---|
| Social destinations are not authoritative. | Constraint | Social marks cannot be links yet. | `SRC-DS-001`, `SPEC-INT-003` | Keep artwork non-interactive; revise specification before adding destinations. | Open, non-blocking |
| Final font-file delivery source is not yet pinned. | Question | Typography implementation may depend on available/licensed files. | Stage 5 assumption | Resolve in Stage 7 before typography/assets task scope is finalized. | Open, non-blocking |
| Exact CSS transition thresholds are not prescribed by Figma anchors. | Constraint | Planning must choose transitions from layout failure. | `DESIGN.md`, `SPEC.md` | Validate at anchors and intermediate failure points. | Accepted |
| Current application is still Astro starter content. | Transitional constraint | Implementation replaces rather than incrementally extends meaningful product UI. | `SRC-REPO-002` | Keep task boundaries small and verify shared foundations before page completion. | Accepted |
| Vercel project observation is time-bound. | Assumption | Runtime settings can change independently of repository files. | `SRC-RUN-001` | Reverify before deployment-sensitive implementation validation. | Open, non-blocking |

No Stage 6 blocking question is identified.

## 24. Source-change Handling

Before Stage 7 planning and before each implementation task:

1. reverify `SRC-DS-001` or record a replacement if the Figma implementation scope materially changes;
2. compare the active repository state with `SRC-REPO-002`;
3. classify differences as unchanged, expected workflow output, or unexpected upstream/concurrent change;
4. create new snapshot IDs rather than silently moving an existing snapshot.

Changes to product scope, routes, map/social behavior, integrations, persistence, authentication, or deployment/runtime boundaries can invalidate this architecture and require return to Stage 6 or an earlier owning stage.

## 25. Traceability

| Architecture item | Snapshot | Requirement or specification | Repository/runtime evidence | Validation |
|---|---|---|---|---|
| ADR-001 static Astro rendering | `SRC-REPO-002` | Home/Location static behaviors | Astro package/config with no adapter | Build and rendered-route validation |
| ADR-002 native two-route navigation | `SRC-DS-001`, `SRC-REPO-002` | `SPEC-INT-001`, `SPEC-INT-002` | Astro file-based routing target | Keyboard + route integration |
| ADR-003 shared presentation boundaries | `SRC-DS-001` | shared footer/navigation and responsive specs | Figma reusable resources | Visual/responsive regression |
| ADR-004 local static assets/integrations | `SRC-DS-001` | `SPEC-BEH-003`, `SPEC-BEH-004`, `SPEC-INT-003` | no runtime integrations in repo | Network/semantic/visual inspection |
| ADR-005 Vercel deployment policy | `SRC-REPO-002`, `SRC-RUN-001` | project technical constraint | `frontend/vercel.json`, Vercel project observation | PR/deployment behavior verification |

## 26. Architecture Validation

### Pass 1 — Completeness and correctness

- [x] Scope and pinned current-state observations are explicit.
- [x] Current, target, and transitional architecture are distinct.
- [x] Routing, component responsibility, state/data, asset, accessibility, build, deployment, and testing boundaries are covered.
- [x] Inapplicable backend, persistence, and authentication concerns are explicitly excluded rather than invented.
- [x] The Stage 5 → Stage 6 repository change is recorded instead of being silently attributed to `SRC-REPO-001`.

**Pass 1 result:** Complete. No blocking omission found.

### Pass 2 — Consistency, traceability, source integrity, risks, and uncertainty

- [x] Architecture decisions support approved requirements/specification and do not change product behavior.
- [x] Figma evidence anchors remain validation targets rather than arbitrary CSS breakpoint mandates.
- [x] Proposed target files/components are not presented as already existing.
- [x] Runtime claims are tied to `SRC-RUN-001`; repository claims use `SRC-REPO-002`.
- [x] Font delivery and social destinations remain visible non-blocking questions.
- [x] No backend, client framework, state library, map SDK, or other example technology was adopted without need.

**Pass 2 result:** Consistent and traceable with documented non-blocking questions.

## Stage 6 readiness

`ARCHITECTURE.md` is **Reviewed** and ready for the project-owner Stage 6 gate decision.

Because execution mode is **Gated**, do not enter Stage 7 or create `PLAN.md` until Stage 6 is explicitly approved.
