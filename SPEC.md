---
artifact: SPEC
project: Art gallery website
profile: Standard
execution_mode: Gated
created: 2026-08-15
updated: 2026-08-15
---

# Specification

## 1. Document information

- Lifecycle state: Reviewed; canonical lifecycle is owned by `.workflow/workflow-record.json`.
- Version: 0.1
- Last updated: 2026-08-15
- Owner: ChatGPT
- Project: Art gallery website
- Scope: Home and Location experiences represented on the approved `🤖 Workflow` Figma page.
- Source baseline: `SOURCE-BASELINE.md`
- Related requirements: `REQUIREMENTS.md`
- Related design intent: `DESIGN.md`
- Active design snapshot: `SRC-DS-001`
- Repository snapshot used for constraints: `SRC-REPO-001`

This specification translates the approved requirements and design intent into observable, testable behavior. It intentionally does not choose Astro file paths, component boundaries, CSS architecture, exact implementation breakpoints, deployment behavior, or unsupported product behavior.

## 2. Purpose and scope

### Included

- Observable Home and Location page behavior.
- Bidirectional page navigation.
- Static map-artwork behavior.
- Footer content and theme behavior.
- Responsive reflow at the approved 1440 px, 768 px, and 375 px evidence anchors and between/beyond those anchors.
- Keyboard, focus, semantic, image, reflow, and reduced-motion accessibility behavior.
- Static content and asset expectations.
- Acceptance criteria for implementation and visual validation.

### Excluded

- Backend services, persistence, authentication, APIs, CMS, analytics, commerce, booking, or personalization.
- Interactive map controls, geolocation, routing, or third-party map services.
- Social-network destinations that have not been approved by an authoritative source.
- Additional pages, menus, forms, dialogs, or application flows.
- Arbitrary numeric breakpoints, pixel-difference tolerances, performance budgets, or browser-support thresholds that are not supported by approved sources.

## 3. Terminology

| Term | Definition |
|---|---|
| Evidence anchor | One of the approved Figma page compositions at 1440 px, 768 px, or 375 px. It is a visual validation target, not automatically a CSS breakpoint. |
| Layout failure | A condition where the current arrangement causes content collision, clipping, unreadable compression, loss of required imagery/action visibility, or page-level horizontal scrolling. |
| Primary navigation action | `OUR LOCATION` on Home or `BACK TO HOME` on Location. |
| Static map artwork | The approved grayscale map image and marker composition; it is visual content, not an interactive map application. |
| Social-brand artwork | The Facebook, Instagram, and Twitter marks shown in the footer. No destination or link behavior is currently approved. |

## 4. Behavioral specifications

### SPEC-BEH-001 — Present the complete Home experience

- **Requirement references:** `REQ-FR-001`, `REQ-DR-001`, `REQ-NFR-001`.
- **Design references:** `DES-001`, `DES-002`, `DES-005`, `DES-006`.
- **Source snapshots:** `SRC-DS-001`, `SRC-REPO-001`.
- **Required behavior:** Home presents the approved gallery title/hero, introductory copy, `OUR LOCATION` action, `YOUR DAY AT THE GALLERY` content, `COME & BE INSPIRED` content, associated gallery imagery, and dark footer identity. Approved copy remains present and may wrap naturally without relying on source line breaks.
- **Applicable states:** Default layout plus supplied responsive variants; primary action Default/Hover/Focus states.
- **Acceptance criteria:** `AC-001`, `AC-002`, `AC-010`, `AC-011`, `AC-015`.

### SPEC-BEH-002 — Present the complete Location experience

- **Requirement references:** `REQ-FR-002`, `REQ-DR-001`, `REQ-NFR-001`.
- **Design references:** `DES-003`, `DES-004`, `DES-005`, `DES-006`.
- **Source snapshots:** `SRC-DS-001`, `SRC-REPO-001`.
- **Required behavior:** Location presents the approved map artwork and marker, `BACK TO HOME` action, `OUR LOCATION` heading, `99 KING STREET` heading, Newport / Rhode Island / United States address copy, visit/opening information, and gold footer identity.
- **Applicable states:** Default layout plus supplied responsive variants; primary action Default/Hover/Focus states.
- **Acceptance criteria:** `AC-003`, `AC-004`, `AC-009`, `AC-010`, `AC-011`, `AC-015`.

### SPEC-BEH-003 — Keep the map informational and non-interactive

- **Requirement references:** `REQ-FR-002`, `REQ-FR-007`, `REQ-DR-001`.
- **Design references:** `DES-003`, `DES-RWD-004`.
- **Source snapshots:** `SRC-DS-001`.
- **Required behavior:** The map region renders the approved static artwork, marker, and overlaid return action. The map itself exposes no zoom, pan, geolocation, routing, or map-control behavior. The textual address remains present outside the map and does not depend on interpreting the map image.
- **Applicable states:** Static/default only.
- **Acceptance criteria:** `AC-009`, `AC-014`.

### SPEC-BEH-004 — Preserve footer identity without inventing social behavior

- **Requirement references:** `REQ-FR-005`, `REQ-AR-002`, `REQ-AR-004`.
- **Design references:** `DES-004`, `DES-007`, `DES-INT-003`, `DES-RWD-005`.
- **Source snapshots:** `SRC-DS-001`.
- **Required behavior:** Both pages show the approved logo, descriptive copy, and Facebook/Instagram/Twitter artwork. Home uses the dark footer theme; Location uses the gold footer theme. Until authoritative destinations are supplied, the social marks remain non-interactive artwork and do not enter the keyboard focus order or expose misleading link semantics.
- **Applicable states:** Dark/Gold theme and responsive orientation variants; no social hover/focus/active state is required while non-interactive.
- **Acceptance criteria:** `AC-010`, `AC-013`.

### SPEC-BEH-005 — Preserve approved copy and image roles

- **Requirement references:** `REQ-FR-007`, `REQ-DR-001`, `REQ-NFR-001`.
- **Design references:** `DES-002`, `DES-005`, `DES-006`.
- **Source snapshots:** `SRC-DS-001`.
- **Required behavior:** Approved editorial copy and required imagery are present. Image crops may adapt responsively where the source demonstrates adaptation, but the intended subject emphasis and image role remain recognizable at each evidence anchor.
- **Applicable states:** All responsive conditions.
- **Acceptance criteria:** `AC-001`, `AC-003`, `AC-011`, `AC-014`.

### SPEC-BEH-006 — Reflow without page-level horizontal scrolling

- **Requirement references:** `REQ-FR-006`, `REQ-AR-005`, `REQ-NFR-002`.
- **Design references:** `DES-RWD-001`–`DES-RWD-006`.
- **Source snapshots:** `SRC-DS-001`.
- **Required behavior:** Essential content and controls remain present, readable, and operable as available inline space changes. A composition transitions before layout failure occurs. Page layout must not require horizontal scrolling to access ordinary page content.
- **Applicable states:** Approved anchors, representative widths between them, and nearby narrower/wider conditions selected from actual layout failure points.
- **Acceptance criteria:** `AC-002`, `AC-004`, `AC-011`, `AC-012`, `AC-016`.

## 5. Interaction specifications

### SPEC-INT-001 — Navigate from Home to Location

- **Source snapshots and evidence:** `SRC-DS-001`; `EVD-034`, `EVD-046`, `EVD-048`, `EVD-049`.
- **Requirement references:** `REQ-FR-003`, `REQ-AR-002`, `REQ-AR-003`, `REQ-AR-006`.
- **Design references:** `DES-INT-001`.
- **Trigger:** Pointer activation or keyboard activation of `OUR LOCATION`.
- **Preconditions:** Home is displayed and the action is available.
- **Result:** The Location experience is displayed through ordinary page navigation.
- **Keyboard behavior:** The control is reachable in logical document order and native activation works from the keyboard.
- **Focus behavior:** The control exposes a clearly visible focus indication before activation. No modal/menu-style focus management is introduced.
- **Closing or cancellation behavior:** Not applicable to page navigation.
- **Accessible state and relationships:** The action exposes a programmatic accessible name matching or clearly communicating `OUR LOCATION`.
- **Failure behavior:** No application-specific recovery state is defined; a navigation failure is an implementation defect rather than an approved user-facing state.
- **Acceptance criteria:** `AC-005`, `AC-007`, `AC-008`.

### SPEC-INT-002 — Navigate from Location to Home

- **Source snapshots and evidence:** `SRC-DS-001`; `EVD-035`, `EVD-047`–`EVD-049`.
- **Requirement references:** `REQ-FR-004`, `REQ-AR-002`, `REQ-AR-003`, `REQ-AR-006`.
- **Design references:** `DES-INT-002`.
- **Trigger:** Pointer activation or keyboard activation of `BACK TO HOME`.
- **Preconditions:** Location is displayed and the action is available.
- **Result:** The Home experience is displayed through ordinary page navigation.
- **Keyboard behavior:** The control is reachable in logical document order and native activation works from the keyboard.
- **Focus behavior:** The control exposes a clearly visible focus indication before activation. No modal/menu-style focus management is introduced.
- **Closing or cancellation behavior:** Not applicable to page navigation.
- **Accessible state and relationships:** The action exposes a programmatic accessible name matching or clearly communicating `BACK TO HOME`.
- **Failure behavior:** No application-specific recovery state is defined; a navigation failure is an implementation defect rather than an approved user-facing state.
- **Acceptance criteria:** `AC-006`, `AC-007`, `AC-008`.

### SPEC-INT-003 — Keep social marks non-interactive until destinations are approved

- **Source snapshots and evidence:** `SRC-DS-001`; `AUD-003`, `Q-PROD-001`, `Q-CONT-001`.
- **Requirement references:** `REQ-FR-005`, `REQ-AR-002`, `REQ-AR-004`.
- **Design references:** `DES-007`, `DES-INT-003`.
- **Trigger:** None in the approved scope.
- **Preconditions:** No authoritative social destination has been supplied.
- **Result:** Social-brand artwork remains visually present but does not navigate or behave like a control.
- **Keyboard behavior:** Non-interactive marks are not focusable.
- **Focus behavior:** No focus state is exposed for non-interactive artwork.
- **Accessible state and relationships:** Decorative/redundant icon artwork is excluded from the accessibility tree when it conveys no additional content; implementation must not announce a fake link destination.
- **Failure behavior:** If authoritative destinations are introduced later, this specification must be revised before treating the marks as links.
- **Acceptance criteria:** `AC-013`.

## 6. Responsive specifications

### Home hero

- **Design references:** `DES-RWD-001`, `DES-RWD-006`.
- **At 1440 px evidence anchor:** Preserve the dark-field / hero-image / white-content editorial relationship and title prominence.
- **At 768 px evidence anchor:** Preserve the image-plus-content composition with title in the content region.
- **At 375 px evidence anchor:** Preserve the vertical sequence of image, title, copy, and action.
- **Between anchors:** Widths, crop, wrapping, and whitespace may be fluid. Transition before the current arrangement causes title/copy/control collision, unreadable compression, clipping, or loss of intended image subject.
- **Beyond anchors:** Very wide layouts preserve the editorial hierarchy rather than stretching content into an unrelated composition; narrower layouts preserve content without page-level horizontal scrolling.

### Home gallery content

- **Design references:** `DES-RWD-002`, `DES-RWD-006`.
- **At 1440/768 px evidence anchors:** Preserve the demonstrated horizontal image/text relationships and narrative order.
- **At 375 px evidence anchor:** Preserve the demonstrated vertical stacks and narrative order.
- **Between anchors:** Stack a relationship before text or key image content becomes materially compressed, collides, or clips.
- **Content:** Nothing required is hidden merely to make the layout fit.

### Location details

- **Design references:** `DES-RWD-003`, `DES-RWD-006`.
- **At 1440/768 px evidence anchors:** Preserve the two-column relationship between the page heading and address/visit content.
- **At 375 px evidence anchor:** Preserve the single-column reading sequence.
- **Between anchors:** Stack before either column becomes too narrow to preserve readable heading/body proportions or before columns collide.

### Map hero

- **Design references:** `DES-RWD-004`, `DES-RWD-006`.
- **At each evidence anchor:** Use the source-appropriate crop relationship while keeping the marker and `BACK TO HOME` action visible and unobscured.
- **Between anchors:** Crop/overlay positions may adapt conservatively; the implementation is not required to continuously interpolate exact Figma crops.
- **Failure condition:** Reposition or transition before the marker/action is clipped, obscured, or overlaps in a way that impairs operation/readability.

### Footer

- **Design references:** `DES-004`, `DES-RWD-005`.
- **At 1440/768 px evidence anchors:** Footer content remains horizontal as demonstrated.
- **At 375 px evidence anchor:** Footer content stacks vertically. Preserve the demonstrated page-specific mobile spacing difference rather than normalizing Home and Location without authority.
- **Between anchors:** Stack before logo, descriptive copy, and social artwork can no longer remain readable and adequately separated horizontally.

## 7. State and content specifications

- **Default:** Both pages render complete approved static content.
- **Hover:** Primary navigation actions preserve the supplied hover-state intent for pointer-capable contexts. Hover is not required to reveal otherwise unavailable information.
- **Focus:** Primary navigation actions expose a visible focus treatment comparable in prominence to the supplied Focus variants.
- **Active or selected:** No persistent selected state is required by the approved source.
- **Disabled:** Not applicable to the two primary page-navigation actions.
- **Loading:** No application loading state is defined because required content is static.
- **Empty:** No empty state is defined for the approved static content.
- **Error:** No product-level dynamic error state is defined. Missing required static content/assets or broken navigation fails implementation validation.
- **Success:** Navigation success is observable by reaching the requested page experience.
- **Long content:** Approved copy may wrap naturally; exact source line breaks are not required. Localization or materially different copy lengths remain outside scope.
- **Missing or partial content:** Not an approved product state; required content is mandatory for acceptance.
- **Failed asset or request:** A broken required static asset is an implementation defect; no invented fallback UI is required by this scope.

## 8. Accessibility specifications

### SPEC-ACC-001 — Expose semantic page structure and reading order

- **Source snapshot, requirement, or standard:** `SRC-DS-001`; `REQ-AR-001`, `REQ-AR-005`.
- **Design references:** `DES-001`, `DES-006`, `DES-RWD-006`.
- **Semantic structure:** Each page exposes meaningful page/section headings and appropriate page landmarks using native HTML semantics where available.
- **Accessible name and relationships:** Visible headings and navigation action labels remain programmatically available.
- **Keyboard operation:** Reading order and interactive order follow a coherent document sequence even where wide layouts visually juxtapose content.
- **Focus order and visibility:** Focus does not jump according to decorative visual positioning.
- **Reflow behavior:** Responsive rearrangement does not change the meaning or omit essential content.
- **Requirement reference:** `REQ-AR-001`, `REQ-AR-005`.
- **Acceptance criteria:** `AC-008`, `AC-012`.

### SPEC-ACC-002 — Make primary navigation keyboard-operable and visibly focusable

- **Source snapshot, requirement, or standard:** `SRC-DS-001`; `REQ-AR-002`, `REQ-AR-003`.
- **Design references:** `DES-INT-001`, `DES-INT-002`.
- **Semantic structure:** Use native page-navigation semantics where possible; do not emulate a modal/menu interaction pattern.
- **Accessible name and relationships:** Each action communicates its visible purpose.
- **Keyboard operation:** Each action can be reached and activated without a pointer.
- **Focus order and visibility:** Focus follows document order and is clearly visible against the current surface.
- **Requirement reference:** `REQ-AR-002`, `REQ-AR-003`.
- **Acceptance criteria:** `AC-005`–`AC-008`.

### SPEC-ACC-003 — Assign meaningful image semantics

- **Source snapshot, requirement, or standard:** `SRC-DS-001`; `REQ-AR-004`.
- **Design references:** `DES-002`, `DES-003`, `DES-007`.
- **Semantic structure:** Images that convey content receive an appropriate text alternative; purely decorative/redundant imagery is excluded from assistive technology.
- **Map relationship:** The textual address remains independently available, so map artwork must not be the only accessible carrier of location data.
- **Social marks:** While non-interactive and redundant to no approved destination, they must not masquerade as controls.
- **Requirement reference:** `REQ-AR-004`.
- **Acceptance criteria:** `AC-009`, `AC-013`, `AC-014`.

### SPEC-ACC-004 — Preserve accessible reflow and reduced-motion behavior

- **Source snapshot, requirement, or standard:** `SRC-DS-001`; `REQ-AR-005`, `REQ-AR-006`.
- **Design references:** `DES-RWD-001`–`DES-RWD-006`, `DES-INT-001`, `DES-INT-002`.
- **Reflow:** Required content remains available and operable through responsive transformations without page-level horizontal scrolling caused by the page layout.
- **Reduced motion:** If the supplied non-essential state transition is implemented with animation, a reduced-motion preference removes or materially reduces that animation while preserving state clarity.
- **Requirement reference:** `REQ-AR-005`, `REQ-AR-006`.
- **Acceptance criteria:** `AC-011`, `AC-012`, `AC-017`.

## 9. Data and interface specifications

### SPEC-DATA-001 — Use approved static content and assets

- **Source snapshots:** `SRC-DS-001`, `SRC-REPO-001`.
- **Requirement references:** `REQ-DR-001`, `REQ-FR-007`.
- **Inputs:** Approved Home/Location copy and visual assets represented by the design source.
- **Outputs:** Rendered static editorial content, gallery imagery, logo, social-brand artwork, map artwork, and marker in their approved roles.
- **Required and optional fields:** All content demonstrated as part of the approved two-page compositions is required; no optional/dynamic content model is established.
- **Defaults:** None invented.
- **Validation ownership:** Figma and approved workflow artifacts define source content; implementation validation confirms presence and visual role.
- **Persistence or synchronization:** None required.
- **Error conditions:** Missing required content or assets fails acceptance; no product-level recovery UI is specified.
- **Acceptance criteria:** `AC-001`, `AC-003`, `AC-014`.

## 10. Validation and error specifications

### SPEC-VAL-001 — Treat layout failure as the responsive transition signal

- **Condition:** A current composition begins to collide, clip, create unreadable compression, obscure required controls/subjects, or cause page-level horizontal scrolling.
- **Prevented or permitted action:** The implementation must transition/reflow before the failure becomes user-visible. Exact threshold selection remains an implementation/planning decision derived from testing.
- **User feedback:** None; responsive adaptation is structural rather than an error message.
- **Recovery:** Reflow, stack, resize, or adjust crop/position while preserving content order and required visibility.
- **Acceptance criteria:** `AC-011`, `AC-016`.

### SPEC-VAL-002 — Treat missing required static content or broken navigation as acceptance failures

- **Condition:** Required copy, imagery, map/marker, footer identity, or a primary navigation route is absent/broken.
- **Prevented or permitted action:** The implementation cannot be accepted while the required item is missing or the primary navigation path fails.
- **User feedback:** No new product error UI is invented for this static scope.
- **Recovery:** Correct the implementation/source mapping and rerun the affected acceptance checks.
- **Acceptance criteria:** `AC-001`, `AC-003`, `AC-005`, `AC-006`, `AC-014`.

## 11. Non-functional behavior

- Visual validation compares Home and Location against the approved 1440 px, 768 px, and 375 px Figma anchors, preserving material composition, typography hierarchy, colors, imagery, spacing relationships, component-state intent, and footer themes (`REQ-NFR-001`). No arbitrary pixel-difference threshold is introduced.
- Responsive validation also exercises representative widths between and around the anchors, selected from observed transition/failure points rather than a default device breakpoint (`REQ-NFR-002`).
- No product-specific performance budget, browser matrix, uptime target, analytics requirement, or additional security policy is introduced by this specification.

## 12. Acceptance criteria

### AC-001 — Home contains all required content

- **Given:** Home is loaded.
- **When:** The full document is inspected.
- **Then:** The approved hero/title, intro copy, `OUR LOCATION`, `YOUR DAY AT THE GALLERY`, `COME & BE INSPIRED`, required gallery imagery, and dark footer content are present.
- **References:** `SPEC-BEH-001`, `SPEC-BEH-005`, `REQ-FR-001`, `REQ-DR-001`.
- **Source snapshots:** `SRC-DS-001`.
- **Validation method:** DOM/content inspection plus rendered comparison to the Home source.

### AC-002 — Home matches each responsive evidence anchor

- **Given:** Home is rendered at 1440 px, 768 px, and 375 px viewport widths.
- **When:** Each render is compared with the matching approved Figma frame.
- **Then:** The material layout mode, content hierarchy, image prominence/crop intent, typography hierarchy, action placement, and footer orientation/theme correspond to that anchor without clipped/overlapping required content or page-level horizontal scrolling.
- **References:** `SPEC-BEH-001`, `SPEC-BEH-006`, `REQ-NFR-001`.
- **Source snapshots:** `SRC-DS-001`.
- **Validation method:** Rendered visual comparison and overflow inspection.

### AC-003 — Location contains all required content

- **Given:** Location is loaded.
- **When:** The full document is inspected.
- **Then:** The approved map artwork, marker, `BACK TO HOME`, `OUR LOCATION`, `99 KING STREET`, address lines, visit/opening copy, and gold footer content are present.
- **References:** `SPEC-BEH-002`, `SPEC-BEH-005`, `REQ-FR-002`, `REQ-DR-001`.
- **Source snapshots:** `SRC-DS-001`.
- **Validation method:** DOM/content inspection plus rendered comparison to the Location source.

### AC-004 — Location matches each responsive evidence anchor

- **Given:** Location is rendered at 1440 px, 768 px, and 375 px viewport widths.
- **When:** Each render is compared with the matching approved Figma frame.
- **Then:** The material map crop relationship, marker/action visibility, details layout, typography hierarchy, and footer orientation/theme correspond to that anchor without clipped/overlapping required content or page-level horizontal scrolling.
- **References:** `SPEC-BEH-002`, `SPEC-BEH-006`, `REQ-NFR-001`.
- **Source snapshots:** `SRC-DS-001`.
- **Validation method:** Rendered visual comparison and overflow inspection.

### AC-005 — `OUR LOCATION` navigates to Location

- **Given:** Focus or pointer is on the Home `OUR LOCATION` action.
- **When:** The action is activated by pointer or keyboard.
- **Then:** The Location experience is reached through ordinary page navigation.
- **References:** `SPEC-INT-001`, `REQ-FR-003`, `REQ-AR-002`.
- **Source snapshots:** `SRC-DS-001`.
- **Validation method:** Pointer and keyboard interaction test.

### AC-006 — `BACK TO HOME` navigates to Home

- **Given:** Focus or pointer is on the Location `BACK TO HOME` action.
- **When:** The action is activated by pointer or keyboard.
- **Then:** The Home experience is reached through ordinary page navigation.
- **References:** `SPEC-INT-002`, `REQ-FR-004`, `REQ-AR-002`.
- **Source snapshots:** `SRC-DS-001`.
- **Validation method:** Pointer and keyboard interaction test.

### AC-007 — Primary navigation exposes visible focus

- **Given:** Either primary navigation action is reached using keyboard navigation.
- **When:** It receives focus.
- **Then:** A clearly discernible focus treatment is visible against its current surface and is comparable in prominence to the approved focus-state intent.
- **References:** `SPEC-INT-001`, `SPEC-INT-002`, `SPEC-ACC-002`, `REQ-AR-003`.
- **Source snapshots:** `SRC-DS-001`.
- **Validation method:** Keyboard visual inspection.

### AC-008 — Keyboard order follows meaningful document order

- **Given:** A user navigates each page by keyboard and/or linear assistive-technology reading order.
- **When:** Interactive and structural content is traversed.
- **Then:** The sequence remains coherent with the visible information hierarchy and does not follow decorative absolute positioning.
- **References:** `SPEC-ACC-001`, `SPEC-ACC-002`, `REQ-AR-001`, `REQ-AR-005`.
- **Source snapshots:** `SRC-DS-001`.
- **Validation method:** DOM-order review and keyboard traversal.

### AC-009 — Map is static and address is independently available

- **Given:** Location is loaded.
- **When:** The map region and visit information are inspected.
- **Then:** No map zoom/pan/geolocation controls are exposed, and the textual address is available independently of the map image.
- **References:** `SPEC-BEH-003`, `SPEC-ACC-003`, `REQ-FR-002`.
- **Source snapshots:** `SRC-DS-001`.
- **Validation method:** Interaction/DOM inspection.

### AC-010 — Footer themes and content are page-correct

- **Given:** Home and Location footers are rendered.
- **When:** They are compared with the approved source.
- **Then:** Both contain the gallery identity content and social-brand artwork; Home uses the dark theme and Location the gold theme, including the demonstrated mobile spacing distinction at the 375 px anchor.
- **References:** `SPEC-BEH-004`, `REQ-FR-005`, `DES-004`.
- **Source snapshots:** `SRC-DS-001`.
- **Validation method:** Rendered visual comparison.

### AC-011 — Required content does not clip or overlap across tested widths

- **Given:** Either page is rendered at evidence anchors and representative intermediate/nearby widths chosen around observed layout transitions.
- **When:** The layout is inspected from top to bottom.
- **Then:** Required text, imagery, marker, and controls remain visible and do not collide, clip, or become unreadably compressed because a layout transformation occurred too late.
- **References:** `SPEC-BEH-006`, `SPEC-VAL-001`, `REQ-FR-006`, `REQ-NFR-002`.
- **Source snapshots:** `SRC-DS-001`.
- **Validation method:** Responsive viewport sweep with targeted checks around transition points.

### AC-012 — Reflow preserves reading and focus order

- **Given:** A page transitions between horizontal and stacked compositions.
- **When:** The page is read linearly and traversed by keyboard.
- **Then:** Essential content remains in a meaningful sequence, interactive controls remain reachable, and no required content is hidden solely to satisfy layout width.
- **References:** `SPEC-BEH-006`, `SPEC-ACC-001`, `SPEC-ACC-004`, `REQ-AR-005`.
- **Source snapshots:** `SRC-DS-001`.
- **Validation method:** DOM-order review plus keyboard testing at layouts on each side of a transition.

### AC-013 — Social artwork does not create unsupported controls

- **Given:** No authoritative social destination has been added to the approved source set.
- **When:** Footer social marks are inspected with keyboard and accessibility tooling.
- **Then:** The marks are not focusable links/buttons, do not navigate, and do not expose misleading interactive semantics.
- **References:** `SPEC-BEH-004`, `SPEC-INT-003`, `SPEC-ACC-003`.
- **Source snapshots:** `SRC-DS-001`.
- **Validation method:** Keyboard and accessibility-tree inspection.

### AC-014 — Required imagery and marker retain their intended roles

- **Given:** Home and Location are rendered at each evidence anchor.
- **When:** Required visual assets are compared with the source.
- **Then:** Gallery imagery, map artwork, marker, logo, and social marks are present in the demonstrated roles; responsive crops do not remove the intended key subject or required marker/action relationship.
- **References:** `SPEC-BEH-003`, `SPEC-BEH-005`, `SPEC-DATA-001`, `REQ-FR-007`.
- **Source snapshots:** `SRC-DS-001`.
- **Validation method:** Rendered visual comparison.

### AC-015 — Approved copy may reflow but remains intact

- **Given:** Home or Location is rendered across tested widths.
- **When:** Text wraps differently from the Figma line breaks.
- **Then:** Approved words/content remain intact and readable, with no clipping, overlap, or deliberate truncation introduced by the layout.
- **References:** `SPEC-BEH-001`, `SPEC-BEH-002`, `DES-006`.
- **Source snapshots:** `SRC-DS-001`.
- **Validation method:** Content comparison and responsive visual inspection.

### AC-016 — No arbitrary evidence-anchor breakpoint assumption is required

- **Given:** Responsive behavior is implemented.
- **When:** Transition thresholds are reviewed and layouts are swept between 375 px, 768 px, and 1440 px.
- **Then:** Each transformation occurs in response to maintaining the specified layout/content conditions rather than requiring the implementation threshold to equal a Figma evidence-anchor width.
- **References:** `SPEC-BEH-006`, `SPEC-VAL-001`, `REQ-NFR-002`.
- **Source snapshots:** `SRC-DS-001`.
- **Validation method:** Review chosen thresholds against viewport sweep evidence immediately before/after each transition.

### AC-017 — Reduced motion preserves state clarity

- **Given:** A non-essential hover/focus transition is implemented for a primary action.
- **When:** The user preference indicates reduced motion.
- **Then:** The animation is removed or materially reduced while the resulting hover/focus state remains visually clear.
- **References:** `SPEC-ACC-004`, `REQ-AR-006`, `DES-INT-001`, `DES-INT-002`.
- **Source snapshots:** `SRC-DS-001`.
- **Validation method:** Inspect interaction with reduced-motion preference enabled. If no motion is implemented, this criterion is satisfied by non-applicability.

## 13. Assumptions, risks, and open questions

### Assumptions

- The approved Home/Location copy and visual assets represented by `SRC-DS-001` remain the content authority for this implementation scope.
- The 1440 px, 768 px, and 375 px compositions remain fidelity anchors rather than mandatory implementation breakpoint values.
- Page navigation is ordinary document navigation; no single-page-app transition or focus-management behavior is inferred.

### Risks

- Exact responsive thresholds remain an implementation/planning decision and must be verified through viewport sweeps around actual failure points.
- Image/map crop behavior between supplied anchors is not continuously demonstrated, so implementation must preserve subject/action visibility conservatively.
- The repository baseline does not yet contain the approved gallery-specific visual assets, so later planning/implementation must map/export them from an authoritative source without substituting unrelated imagery.

### Blocking questions

None for Stage 4 specification. The unresolved social destinations remain intentionally non-blocking because this specification keeps the marks non-interactive.

### Preserved open questions

- `Q-PROD-001` / `Q-CONT-001`: authoritative social destinations and whether the footer marks should become links.
- `Q-DES-001`: rationale for the Home/Location mobile footer side-padding difference; current specification preserves the demonstrated output.
- `Q-DES-002`: exact continuous map-crop interpolation between source anchors; current specification defines visibility/failure conditions instead of inventing interpolation rules.

## 14. Traceability

| Specification | Requirement | Design evidence or decision | Acceptance criteria |
|---|---|---|---|
| `SPEC-BEH-001` | `REQ-FR-001`, `REQ-DR-001`, `REQ-NFR-001` | `DES-001`, `DES-002`, `DES-005`, `DES-006` | `AC-001`, `AC-002`, `AC-010`, `AC-011`, `AC-015` |
| `SPEC-BEH-002` | `REQ-FR-002`, `REQ-DR-001`, `REQ-NFR-001` | `DES-003`–`DES-006` | `AC-003`, `AC-004`, `AC-009`–`AC-011`, `AC-015` |
| `SPEC-BEH-003` | `REQ-FR-002`, `REQ-FR-007` | `DES-003`, `DES-RWD-004` | `AC-009`, `AC-014` |
| `SPEC-BEH-004` | `REQ-FR-005`, `REQ-AR-002`, `REQ-AR-004` | `DES-004`, `DES-007`, `DES-INT-003` | `AC-010`, `AC-013` |
| `SPEC-BEH-005` | `REQ-FR-007`, `REQ-DR-001`, `REQ-NFR-001` | `DES-002`, `DES-005`, `DES-006` | `AC-001`, `AC-003`, `AC-011`, `AC-014` |
| `SPEC-BEH-006` | `REQ-FR-006`, `REQ-AR-005`, `REQ-NFR-002` | `DES-RWD-001`–`DES-RWD-006` | `AC-002`, `AC-004`, `AC-011`, `AC-012`, `AC-016` |
| `SPEC-INT-001` | `REQ-FR-003`, `REQ-AR-002`, `REQ-AR-003`, `REQ-AR-006` | `DES-INT-001` | `AC-005`, `AC-007`, `AC-008` |
| `SPEC-INT-002` | `REQ-FR-004`, `REQ-AR-002`, `REQ-AR-003`, `REQ-AR-006` | `DES-INT-002` | `AC-006`, `AC-007`, `AC-008` |
| `SPEC-INT-003` | `REQ-FR-005`, `REQ-AR-002`, `REQ-AR-004` | `DES-007`, `DES-INT-003` | `AC-013` |
| `SPEC-ACC-001` | `REQ-AR-001`, `REQ-AR-005` | `DES-001`, `DES-RWD-006` | `AC-008`, `AC-012` |
| `SPEC-ACC-002` | `REQ-AR-002`, `REQ-AR-003` | `DES-INT-001`, `DES-INT-002` | `AC-005`–`AC-008` |
| `SPEC-ACC-003` | `REQ-AR-004` | `DES-002`, `DES-003`, `DES-007` | `AC-009`, `AC-013`, `AC-014` |
| `SPEC-ACC-004` | `REQ-AR-005`, `REQ-AR-006` | `DES-RWD-001`–`DES-RWD-006` | `AC-011`, `AC-012`, `AC-017` |
| `SPEC-DATA-001` | `REQ-DR-001`, `REQ-FR-007` | `DES-002`, `DES-003`, `DES-006` | `AC-001`, `AC-003`, `AC-014` |
| `SPEC-VAL-001` | `REQ-FR-006`, `REQ-NFR-002` | `DES-RWD-001`–`DES-RWD-006` | `AC-011`, `AC-016` |
| `SPEC-VAL-002` | `REQ-FR-001`–`REQ-FR-004`, `REQ-FR-007` | Approved Stage 3 intent | `AC-001`, `AC-003`, `AC-005`, `AC-006`, `AC-014` |

All specification rows use `SRC-DS-001`; repository constraints additionally use `SRC-REPO-001` where stated.

## 15. Review

### Pass 1 — Completeness and correctness

- [x] Material behavior, interactions, states, responsive behavior, accessibility, static data, validation, errors, and edge cases are covered as applicable.
- [x] Required behavior is objectively testable through `AC-*` criteria.
- [x] The specification does not prescribe implementation paths, task order, unsupported architecture, or arbitrary breakpoint values.
- [x] Snapshot IDs used by the specification exist in `SOURCE-BASELINE.md` and support the described behavior.
- [x] Non-applicable dynamic loading/empty/error/disabled states are explicitly distinguished from missing implementation requirements.

**Pass 1 result:** No blocking completeness/correctness findings remain after review.

### Pass 2 — Consistency, traceability, source integrity, risks, and uncertainty

- [x] Identifiers use the approved `SPEC-*` and `AC-*` namespaces without reusing requirement IDs.
- [x] Material specifications map to approved requirements and relevant design decisions/evidence.
- [x] Fresh Stage 4 inspection of all six approved Figma evidence anchors found no material source change from the Stage 3 approved intent.
- [x] No arbitrary breakpoint, unsupported focus movement, performance threshold, social destination, or map behavior is presented as confirmed.
- [x] Open questions and responsive/crop uncertainty remain visible.
- [x] Social behavior is resolved conservatively for this stage by keeping unapproved destinations non-interactive rather than fabricating links.

**Pass 2 result:** Specification is internally reviewed and ready for the gated Stage 4 approval decision.
