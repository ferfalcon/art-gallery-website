---
artifact: REQUIREMENTS
project: Art gallery website
profile: Standard
execution_mode: Gated
created: 2026-08-15
updated: 2026-08-15
---

# Project Requirements

## 1. Document information

- Lifecycle state: Draft; canonical lifecycle is owned by `.workflow/workflow-record.json`.
- Version: 0.1
- Last updated: 2026-08-15
- Owner: ChatGPT
- Project: Art gallery website
- Scope: Home and Location pages represented on the approved `🤖 Workflow` Figma page.
- Project context: `PROJECT-CONTEXT.md`
- Source baseline: `SOURCE-BASELINE.md`
- Evidence baseline: `DESIGN-AUDIT.md`
- Active design snapshot: `SRC-DS-001`
- Repository snapshot used for project constraints: `SRC-REPO-001`
- Stage 2 source verification: `VER-003`

This document defines outcomes, product requirements, constraints, accessibility expectations, and quality requirements. It intentionally does not choose implementation structure, CSS breakpoints, route file names, semantic element details, asset-loading mechanisms, or other Stage 3–7 decisions.

## 2. Overview and problem

The approved source describes a two-page static art-gallery website: a Home experience introducing the gallery and a Location experience presenting the venue address, descriptive information, map artwork, and a way back to Home.

The implementation must reproduce the approved content and visual intent in the existing Astro frontend while remaining usable across responsive conditions and accessible interaction modes. Requirements must stay within demonstrated source authority: Figma proves visual compositions, supplied content, component states, and prototype navigation, but it does not prove backend behavior, social destinations, implementation breakpoints, browser targets, or complete accessibility semantics.

## 3. Goals and non-goals

### Goals

- Present the approved Home content hierarchy and gallery identity.
- Present the approved Location content hierarchy, address information, and map artwork.
- Provide bidirectional navigation between Home and Location.
- Preserve the responsive intent demonstrated by the desktop, tablet, and mobile source compositions while remaining robust between those evidence anchors.
- Preserve the approved visual identity, imagery, content, component-state intent, and page-specific footer themes.
- Deliver semantic, keyboard-accessible, focus-visible, assistive-technology-friendly behavior consistent with the project quality baseline.
- Produce requirements that remain traceable to approved source evidence without inventing unsupported behavior.

### Non-goals

- Backend services, persistence, authentication, authorization, APIs, CMS integration, or dynamic data loading.
- Additional product pages, menus, forms, modals, or multi-step flows not present in `SRC-DS-001`.
- An interactive map or geolocation behavior; the approved source demonstrates map artwork, not a map service.
- Analytics, personalization, commerce, booking, or account behavior.
- Defining social-network destination URLs without authoritative source evidence.
- Selecting implementation breakpoints, route file names, component architecture, or CSS strategy in Stage 2.
- Inventing browser-support matrices, performance thresholds, uptime targets, security policies, retention rules, or localization requirements.
- Structural or visual modification of Figma pages outside the authorized `🤖 Workflow` scope.

## 4. Users and needs

| User or actor | Need | Evidence or authority |
|---|---|---|
| Gallery website visitor | Understand the gallery proposition and editorial content on Home. | `EVD-007`, `EVD-009`–`EVD-011` |
| Gallery website visitor | Find the gallery address and location information. | `EVD-008`, `EVD-012`–`EVD-014`, `EVD-050` |
| Gallery website visitor | Move from Home to Location and return to Home. | `EVD-046`, `EVD-047` |
| Visitor using a narrow, medium, or wide viewport | Read and operate the same core experience without clipping, overlap, or loss of content. | `EVD-009`–`EVD-019`, `AUD-001` |
| Keyboard or assistive-technology user | Navigate interactive controls with a meaningful reading/focus order, visible focus, and accessible names. | Project quality baseline, `EVD-049`, `EVD-059`, `AUD-002`, `AUD-003` |

## 5. Functional requirements

### REQ-FR-001 — Present the Home experience

- **Classification:** Confirmed
- **Priority:** Must
- **Description:** The product must provide a Home page containing the approved gallery hero/title, introductory copy, `OUR LOCATION` primary action, `Your Day at the Gallery` content, `COME & BE INSPIRED` content, associated gallery imagery, and Home footer content.
- **Rationale:** These items form the complete Home information hierarchy in the approved source.
- **Evidence:** `EVD-001`–`EVD-003`, `EVD-007`, `EVD-009`–`EVD-011`.
- **Acceptance ownership:** Stage 4 `SPEC.md` will define observable `AC-*` checks; the implementation must preserve all required content and hierarchy across supported responsive conditions.

### REQ-FR-002 — Present the Location experience

- **Classification:** Confirmed
- **Priority:** Must
- **Description:** The product must provide a Location page containing the approved map artwork and marker, `BACK TO HOME` action, `OUR LOCATION` heading, `99 King Street` address heading, Newport / Rhode Island / United States address copy, gallery location/opening-hours description, and Location footer content.
- **Rationale:** These items form the complete Location information hierarchy in the approved source.
- **Evidence:** `EVD-004`–`EVD-006`, `EVD-008`, `EVD-012`–`EVD-014`.
- **Acceptance ownership:** Stage 4 `SPEC.md` will define observable `AC-*` checks for presence and content preservation.

### REQ-FR-003 — Navigate from Home to Location

- **Classification:** Confirmed
- **Priority:** Must
- **Description:** Activating the `OUR LOCATION` primary action must take the user from Home to the Location experience.
- **Rationale:** Bidirectional page navigation is an explicit prototype behavior.
- **Evidence:** `EVD-046`; navigation component evidence `EVD-034`.
- **Acceptance ownership:** Stage 4 will define route-observable behavior without assuming a route implementation in this document.

### REQ-FR-004 — Navigate from Location to Home

- **Classification:** Confirmed
- **Priority:** Must
- **Description:** Activating the `BACK TO HOME` action must take the user from Location back to the Home experience.
- **Rationale:** The return path is explicit in the approved prototype.
- **Evidence:** `EVD-047`; navigation component evidence `EVD-035`.
- **Acceptance ownership:** Stage 4 will define route-observable behavior without assuming a route implementation in this document.

### REQ-FR-005 — Present the shared gallery footer identity

- **Classification:** Confirmed
- **Priority:** Must
- **Description:** Both pages must present the approved gallery logo, footer descriptive copy, and Facebook, Instagram, and Twitter icon artwork, using the page-appropriate footer theme demonstrated by the source.
- **Rationale:** The footer is a repeated identity/content pattern across Home and Location.
- **Evidence:** `EVD-007`, `EVD-008`, `EVD-019`, `EVD-037`, `EVD-051`–`EVD-054`.
- **Acceptance ownership:** Stage 4 will define observable content/theme behavior. This requirement does not assert destination URLs or that the icons are links because those behaviors are not demonstrated.

### REQ-FR-006 — Preserve the responsive experience

- **Classification:** Confirmed outcome; transition behavior requires later definition
- **Priority:** Must
- **Description:** Home and Location must preserve their complete content and intended hierarchy across narrow, medium, and wide layout conditions, without primary content being clipped, overlapped, or requiring horizontal page scrolling because of the page layout.
- **Rationale:** The source provides distinct desktop, tablet, and mobile compositions, while `AUD-001` establishes that the supplied widths are evidence anchors rather than proven implementation breakpoints.
- **Evidence:** `EVD-009`–`EVD-019`, `AUD-001`.
- **Acceptance ownership:** Stage 3 will define responsive intent and Stage 4 will define testable behavior and conditions.

### REQ-FR-007 — Preserve source imagery and map-artwork intent

- **Classification:** Confirmed
- **Priority:** Must
- **Description:** The implementation must use the approved gallery imagery, logo/vector assets, map artwork, and marker in the roles demonstrated by the source, preserving the intended subject/crop emphasis across responsive conditions.
- **Rationale:** Imagery is a material part of the approved composition, and the map crop changes structurally between supplied viewports.
- **Evidence:** `EVD-044`, `EVD-045`, `EVD-051`–`EVD-058`, `AUD-006`.
- **Acceptance ownership:** Stage 3 will define visual/crop intent; Stage 4 and implementation validation will define observable checks.

## 6. Business rules

No independent business rule is confirmed by the approved sources at Stage 2. The website is currently evidenced as a static editorial experience.

No rule for opening hours logic, visitor eligibility, commerce, bookings, geographic availability, account ownership, permissions, or social-network policy may be inferred from the visible copy alone.

## 7. Data requirements

### REQ-DR-001 — Use approved static editorial content and assets

- **Classification:** Confirmed
- **Priority:** Must
- **Description:** The initial implementation must present the approved static gallery copy, address/location information, logo, social icon artwork, gallery images, map artwork, and marker represented by `SRC-DS-001`.
- **Required and optional data:** Required content is the content demonstrated in the approved Home and Location compositions. No optional/dynamic-field model is established.
- **Validation or ownership:** Content ownership remains the approved design source for this implementation scope.
- **Privacy or retention evidence:** None applicable or demonstrated; no collection/persistence requirement is introduced.
- **Evidence:** `EVD-007`, `EVD-008`, `EVD-050`–`EVD-058`.

## 8. Accessibility requirements

### REQ-AR-001 — Preserve a meaningful semantic reading hierarchy

- **Classification:** Recommended quality requirement from approved project context
- **Priority:** Must
- **Description:** The implemented pages must expose a semantic structure and reading order that follows the visible information hierarchy of Home and Location, including meaningful page/section headings and page landmarks where applicable.
- **Rationale:** Figma demonstrates visual hierarchy but cannot establish DOM semantics or screen-reader reading order.
- **Evidence or authority:** Project quality baseline; `EVD-007`, `EVD-008`, `EVD-059`.
- **Acceptance ownership:** Stage 3/4 must translate this into explicit semantic and observable behavior.

### REQ-AR-002 — Make interactive controls keyboard operable

- **Classification:** Recommended quality requirement from approved project context
- **Priority:** Must
- **Description:** Every implemented interactive control must be reachable and operable by keyboard in a logical order. This includes `OUR LOCATION`, `BACK TO HOME`, and any social item that is implemented as an interactive destination.
- **Rationale:** The design supplies focus visuals for primary actions but does not prove keyboard behavior; social interaction is underspecified.
- **Evidence or authority:** Project quality baseline; `EVD-049`, `EVD-059`, `AUD-002`, `AUD-003`.
- **Acceptance ownership:** Stage 4 will define keyboard-observable checks.

### REQ-AR-003 — Provide clearly visible focus indication

- **Classification:** Confirmed visual intent plus recommended implementation requirement
- **Priority:** Must
- **Description:** Keyboard-focusable controls must expose a clearly visible focus indication. The two primary navigation actions must preserve the intent of the supplied focus variants; any additional interactive controls must also have a discernible focus state.
- **Rationale:** Explicit focus variants exist for the primary actions, but the source does not define browser focus mechanics for them or any social icons.
- **Evidence or authority:** `EVD-049`, `EVD-059`, `AUD-002`, `AUD-003`.
- **Acceptance ownership:** Stage 3 owns visual focus intent; Stage 4 owns testable focus behavior.

### REQ-AR-004 — Provide accessible names and image semantics

- **Classification:** Recommended quality requirement from approved project context
- **Priority:** Must
- **Description:** Interactive controls must expose programmatic accessible names that communicate their purpose. Icon-only social controls, if interactive, must have meaningful accessible names. Images must receive text alternatives when they convey content and be excluded from assistive technology when they are purely decorative.
- **Rationale:** The design source cannot define accessible names or image semantics.
- **Evidence or authority:** Project quality baseline; `EVD-051`–`EVD-059`, `AUD-003`.
- **Acceptance ownership:** Stage 3/4 will classify individual assets and controls.

### REQ-AR-005 — Preserve accessible reflow and reading order

- **Classification:** Recommended quality requirement from approved project context
- **Priority:** Must
- **Description:** Responsive transformations must preserve all essential content, logical reading order, and interactive operability as the available inline space changes. Layout must not rely on a single supplied Figma width to remain understandable or usable.
- **Rationale:** Only three viewport anchors are demonstrated; accessibility and intermediate-width behavior must be designed in the implementation.
- **Evidence or authority:** Project quality baseline; `EVD-015`–`EVD-019`, `AUD-001`.
- **Acceptance ownership:** Stage 3 defines intent; Stage 4 defines concrete validation conditions.

### REQ-AR-006 — Respect reduced-motion preferences for introduced motion

- **Classification:** Recommended quality requirement from approved project context
- **Priority:** Should
- **Description:** If the implementation reproduces or adds non-essential animated transitions, it should respect the user's reduced-motion preference while preserving state clarity and operability.
- **Rationale:** The source demonstrates a 0.2-second dissolve for CTA hover, while the project quality baseline explicitly calls for reduced-motion consideration.
- **Evidence or authority:** Project quality baseline; `EVD-048`.
- **Acceptance ownership:** Stage 3/4 will determine whether motion is implemented and how it degrades.

## 9. Other non-functional requirements

### REQ-NFR-001 — Preserve visual fidelity at approved evidence anchors

- **Classification:** Confirmed project quality requirement
- **Priority:** Must
- **Category:** Visual quality
- **Description:** Rendered Home and Location pages must preserve the material visual composition, typography hierarchy, colors, imagery, spacing relationships, component-state intent, and page-specific footer themes demonstrated at the supplied 1440 px, 768 px, and 375 px design anchors.
- **Measurement conditions:** Compare rendered implementation against the corresponding approved Figma frames during visual validation. This requirement does not define arbitrary pixel-difference tolerances.
- **Evidence:** Project quality baseline; `EVD-009`–`EVD-033`, `EVD-034`–`EVD-045`.

### REQ-NFR-002 — Remain robust between supplied viewport anchors

- **Classification:** Recommended quality requirement supported by a documented evidence gap
- **Priority:** Must
- **Category:** Responsive quality
- **Description:** The layout must remain coherent between and around the supplied Figma viewport anchors, without introducing avoidable overlap, clipping, unreadable text, or broken interaction merely because the viewport does not equal 375, 768, or 1440 pixels.
- **Measurement conditions:** Stage 3/4 must select validation widths from observed layout transformation needs and failure points rather than treating the three source widths as automatic implementation breakpoints.
- **Evidence:** `AUD-001`, `EVD-015`–`EVD-019`.

No browser matrix, performance budget, uptime target, or numeric performance threshold is approved at Stage 2.

## 10. Security requirements

No product-specific security requirement is evidenced for the current static, non-authenticated scope. Stage 2 does not invent authentication, authorization, data-protection, retention, or application-security policies.

Normal secure implementation and dependency hygiene remain engineering responsibilities, but no unsupported product security rule is promoted to a `REQ-SEC-*` requirement here.

## 11. Responsive and content requirements

The following outcome-level expectations refine `REQ-FR-006`, `REQ-AR-005`, and `REQ-NFR-002` without selecting CSS breakpoints:

- Preserve the desktop, tablet, and mobile content hierarchy demonstrated by `EVD-009`–`EVD-014`.
- Preserve the Hero transformation from the desktop composition to the tablet and stacked mobile compositions (`EVD-015`).
- Preserve Gallery Content as horizontal groupings at the supplied desktop/tablet states and vertical stacks at the supplied mobile state (`EVD-016`).
- Preserve Location Details as side-by-side at supplied desktop/tablet states and stacked at the supplied mobile state (`EVD-017`).
- Preserve the responsive map marker/action positioning and the distinct supplied map crops (`EVD-018`, `AUD-006`).
- Preserve horizontal desktop/tablet footers and vertical mobile footers (`EVD-019`).
- Do not silently normalize the observed Dark-mobile 40 px versus Gold-mobile 16 px side-padding difference; Stage 3 must preserve or explicitly resolve it (`AUD-005`).
- Preserve approved source copy as the initial implementation content. Long-copy, localization, missing-image, and alternate-content behavior is not defined by the design evidence (`AUD-007`).

## 12. Constraints

### REQ-CON-001 — Use the existing Astro frontend

- **Classification:** Confirmed
- **Priority:** Must
- **Description:** Implementation must integrate with the existing `frontend/` Astro + TypeScript application rather than replacing the application framework.
- **Evidence:** `SRC-REPO-001`, `PROJECT-CONTEXT.md`, root `AGENTS.md`.
- **Impact:** Later architecture, planning, and implementation decisions must fit the existing frontend.

### REQ-CON-002 — Preserve the repository runtime/tooling contract

- **Classification:** Confirmed
- **Priority:** Must
- **Description:** Repository work must respect Node.js `24.x` and pnpm as the declared frontend runtime/package-manager constraints.
- **Evidence:** `SRC-REPO-001`, `PROJECT-CONTEXT.md`, root `AGENTS.md`.
- **Impact:** Build and dependency work must use the repository-approved environment.

### REQ-CON-003 — Follow the repository Git and deployment policy

- **Classification:** Confirmed
- **Priority:** Must
- **Description:** Implementation changes must use the repository's dedicated branch → pull request → Vercel preview → verification → merge process. Implementation must not be pushed directly to `main` or manually promoted to production unless explicitly requested.
- **Evidence:** Root `AGENTS.md`, `PROJECT-CONTEXT.md`.
- **Impact:** Planning and implementation tasks must include preview verification where deployment behavior matters.

### REQ-CON-004 — Respect the authorized Figma scope

- **Classification:** Confirmed
- **Priority:** Must
- **Description:** The primary Figma editing scope is `🤖 Workflow`; structural or visual changes to other Figma pages require explicit user authorization, subject only to the documented controlled global-resource exception.
- **Evidence:** Root `AGENTS.md`, project instructions.
- **Impact:** Design-source corrections must remain within the approved safety boundary.

### REQ-CON-005 — Do not add unsupported application capabilities

- **Classification:** Confirmed
- **Priority:** Must
- **Description:** The implementation must not add backend, persistence, authentication, external API, CMS, analytics, commerce, or other product behavior merely because it might be useful; additions require authoritative scope or a later approved decision.
- **Evidence:** `PROJECT-CONTEXT.md`, `DESIGN-AUDIT.md`, Stage 2 workflow rules.
- **Impact:** Later stages must preserve the static-site scope unless rebaselined or explicitly expanded.

## 13. Dependencies

| Dependency | Snapshot or evidence | Purpose | Availability | Risk |
|---|---|---|---|---|
| Approved Figma `🤖 Workflow` page | `SRC-DS-001`, `VER-003` | Visual/content/component/interaction evidence | Available; time-bound source reverified at Stage 2 entry | Mutable design URL requires continued verification before material downstream work |
| Existing Astro frontend repository | `SRC-REPO-001` | Implementation target and tooling constraints | Available as immutable input snapshot | Current working branch has workflow outputs beyond the pinned input; planning must distinguish baseline from workflow changes |
| Figma image/vector resources | `EVD-051`–`EVD-058` | Logo, social artwork, gallery imagery, map artwork, marker | Available in Figma | Export format/licensing metadata not established in the design source |
| Project operating contract | Root `AGENTS.md`, `PROJECT-CONTEXT.md` | Accessibility, source-fidelity, Git/deployment, scope constraints | Available | Must remain synchronized with actual repository policy |

## 14. Assumptions and open questions

### Assumptions

- The approved static copy and artwork in `SRC-DS-001` are the intended initial content for implementation.
- The Home and Location frames represent the complete page scope currently authorized for implementation.
- Source viewports are evidence anchors, not automatic CSS breakpoint values.

These assumptions do not create new product behavior; they preserve the explicit Stage 0/1 scope and evidence interpretation.

### Blocking questions

None at Stage 2.

### Non-blocking questions

1. **OQ-001 — Social destinations:** What URLs, if any, should the Facebook, Instagram, and Twitter items use? `AUD-003` confirms the source does not demonstrate destinations.
2. **OQ-002 — Responsive transition points:** At which content/layout failure points should the supplied desktop/tablet/mobile compositions transform? `AUD-001` leaves exact transition points for Stage 3/4.
3. **OQ-003 — Continuous map crop:** How should the map artwork interpolate between the supplied crops at intermediate widths? `AUD-006` requires Stage 3/4 resolution.
4. **OQ-004 — Mobile footer side padding:** Is the Dark 40 px versus Gold 16 px mobile footer padding difference intentional? `AUD-005` requires preserving the distinction unless later evidence authorizes normalization.
5. **OQ-005 — Asset export/licensing:** Which implementation/export formats should be used for Figma image/vector assets, and is any licensing metadata needed outside the design file? The audit found no licensing metadata.
6. **OQ-006 — Content-edge behavior:** Are localization, unusually long copy, missing images, or alternate content within project scope? `AUD-007` provides no source evidence; no such feature is required unless scope changes.

## 15. Risks

| Risk | Impact | Likelihood | Mitigation | Blocking |
|---|---|---|---|---|
| Treating 375/768/1440 as arbitrary implementation breakpoints | Intermediate layouts may fail despite matching source anchors | Medium | Derive Stage 3/4 transitions from design evidence and layout failure rather than width labels alone | No |
| Inventing social destinations or interaction behavior | Incorrect product behavior and accessibility semantics | Medium | Keep icons' destinations unresolved until authoritative input exists | No |
| Losing map subject/crop intent between viewports | Location page can materially diverge from approved design | Medium | Define crop behavior in Stage 3 and validate representative intermediate widths | No |
| Normalizing page-specific mobile footer spacing | Unapproved visual divergence | Medium | Preserve the observed difference until explicitly resolved | No |
| Asset/export or licensing uncertainty discovered late | Implementation rework or release delay | Low/Unknown | Resolve export formats/licensing during planning before affected implementation tasks | No |
| Figma source changes after this time-bound verification | Downstream documents may use stale design evidence | Medium | Reverify `SRC-DS-001` before each material downstream stage as required by workflow rules | No |

## 16. Definition of Done

Stage 2 requirements are ready for owner review when:

- [x] Goals, non-goals, users, functional needs, data expectations, accessibility, quality, constraints, dependencies, risks, assumptions, and questions are covered for the current scope.
- [x] Every material requirement is specific, prioritized, and traceable to approved evidence or project authority.
- [x] Confirmed, recommended, and unresolved information remain explicitly distinct.
- [x] Unsupported business rules, route implementation, breakpoints, social URLs, browser targets, security policy, persistence, and performance thresholds have not been invented.
- [x] Responsive requirements define outcomes rather than arbitrary breakpoint numbers.
- [x] Accessibility is represented as a first-class product quality requirement.
- [x] Both required document-review passes have been completed.
- [ ] The project owner has reviewed and approved `ART-REQUIREMENTS`.
- [ ] `GATE-003` has been recorded as a passing Stage 2 gate.

Project implementation Definition of Done remains downstream: later `DESIGN.md`, `SPEC.md`, planning/tasks, implementation validation, and final review must demonstrate satisfaction of the approved requirements.

## 17. Traceability

| Requirement | Snapshot or evidence | Stage 3 design intent | Stage 4 specification / acceptance | Validation |
|---|---|---|---|---|
| `REQ-FR-001` | `EVD-001`–`EVD-003`, `EVD-007`, `EVD-009`–`EVD-011` | Pending | Pending | Pending |
| `REQ-FR-002` | `EVD-004`–`EVD-006`, `EVD-008`, `EVD-012`–`EVD-014` | Pending | Pending | Pending |
| `REQ-FR-003` | `EVD-034`, `EVD-046` | Pending | Pending | Pending |
| `REQ-FR-004` | `EVD-035`, `EVD-047` | Pending | Pending | Pending |
| `REQ-FR-005` | `EVD-007`, `EVD-008`, `EVD-019`, `EVD-037`, `EVD-051`–`EVD-054` | Pending | Pending | Pending |
| `REQ-FR-006` | `EVD-009`–`EVD-019`, `AUD-001` | Pending | Pending | Pending |
| `REQ-FR-007` | `EVD-044`, `EVD-045`, `EVD-051`–`EVD-058`, `AUD-006` | Pending | Pending | Pending |
| `REQ-DR-001` | `EVD-007`, `EVD-008`, `EVD-050`–`EVD-058` | Pending | Pending | Pending |
| `REQ-AR-001` | Project quality baseline, `EVD-007`, `EVD-008`, `EVD-059` | Pending | Pending | Pending |
| `REQ-AR-002` | Project quality baseline, `EVD-049`, `EVD-059`, `AUD-002`, `AUD-003` | Pending | Pending | Pending |
| `REQ-AR-003` | `EVD-049`, `EVD-059`, `AUD-002`, `AUD-003` | Pending | Pending | Pending |
| `REQ-AR-004` | Project quality baseline, `EVD-051`–`EVD-059`, `AUD-003` | Pending | Pending | Pending |
| `REQ-AR-005` | Project quality baseline, `EVD-015`–`EVD-019`, `AUD-001` | Pending | Pending | Pending |
| `REQ-AR-006` | Project quality baseline, `EVD-048` | Pending | Pending | Pending |
| `REQ-NFR-001` | Project quality baseline, `EVD-009`–`EVD-045` | Pending | Pending | Pending |
| `REQ-NFR-002` | `AUD-001`, `EVD-015`–`EVD-019` | Pending | Pending | Pending |
| `REQ-CON-001` | `SRC-REPO-001`, `PROJECT-CONTEXT.md`, root `AGENTS.md` | N/A | Pending constraints | Pending |
| `REQ-CON-002` | `SRC-REPO-001`, `PROJECT-CONTEXT.md`, root `AGENTS.md` | N/A | Pending constraints | Pending |
| `REQ-CON-003` | Root `AGENTS.md`, `PROJECT-CONTEXT.md` | N/A | Pending constraints | Pending |
| `REQ-CON-004` | Root `AGENTS.md`, project instructions | N/A | Pending constraints | Pending |
| `REQ-CON-005` | `PROJECT-CONTEXT.md`, `DESIGN-AUDIT.md`, Stage 2 rules | N/A | Pending constraints | Pending |

## 18. Review

### Pass 1 — Completeness and correctness

- [x] Requirements cover the agreed Home and Location scope.
- [x] Goals and non-goals reflect the approved project context and Stage 1 audit.
- [x] Functional requirements preserve the demonstrated pages, content, navigation, imagery, and responsive outcomes.
- [x] Accessibility requirements cover semantics, keyboard operation, focus visibility, accessible names/image semantics, reflow, and reduced-motion considerations as applicable.
- [x] Data requirements remain static and do not infer a CMS/API model.
- [x] Business/security sections explicitly avoid unsupported rules.
- [x] Constraints reflect the actual repository, Figma, runtime, and Git/deployment contract.
- [x] Requirements are necessary, prioritized, and testable at the appropriate downstream stage.

**Pass 1 result:** Passed. No blocking omission or unsupported product rule was found.

### Pass 2 — Consistency, traceability, source integrity, risks, and uncertainty

- [x] Requirement identifiers use the canonical `REQ-*` namespaces.
- [x] Every material requirement cites approved evidence or authoritative project constraints.
- [x] `SRC-DS-001` was structurally reverified as unchanged at Stage 2 entry through `VER-003`.
- [x] The document does not silently treat 375, 768, or 1440 px as implementation breakpoints.
- [x] The document does not invent social destinations, an interactive map, backend behavior, browser targets, performance thresholds, or security/privacy rules.
- [x] Observed source gaps are retained as non-blocking questions and risks for the owning downstream stages.
- [x] The document remains consistent with `PROJECT-CONTEXT.md`, `DESIGN-AUDIT.md`, root `AGENTS.md`, and the Standard/Gated workflow rules.
- [x] No Stage 2 blocker requires a profile upgrade or rebaseline.

**Pass 2 result:** Passed. `REQUIREMENTS.md` is ready for project-owner review. The workflow remains at Stage 2 in Gated mode; no Stage 2 passing gate is recorded until explicit owner approval.
