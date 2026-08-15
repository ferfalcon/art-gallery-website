---
artifact: DESIGN
project: Art gallery website
profile: Standard
execution_mode: Gated
created: 2026-08-15
updated: 2026-08-15
---

# Design

## 1. Document information

- Lifecycle state: Draft; canonical lifecycle is owned by `.workflow/workflow-record.json`.
- Version: 0.1
- Last updated: 2026-08-15
- Owner: ChatGPT
- Project: Art gallery website
- Scope: Home and Location experiences on the approved `🤖 Workflow` Figma page.
- Source baseline: `SOURCE-BASELINE.md`
- Evidence baseline: `DESIGN-AUDIT.md`
- Related requirements: `REQUIREMENTS.md`
- Active design snapshot: `SRC-DS-001`
- Repository snapshot used for resource mapping: `SRC-REPO-001`
- Stage 3 source verification: `VER-004`, `VER-005`

This document records visual, responsive, content, interaction, and accessibility intent. It does not choose Astro component structure, CSS file organization, route file names, exact CSS breakpoint values, asset paths, or test procedures; those belong to later specification, architecture, planning, and implementation stages.

## 2. Purpose and intent

The experience should feel editorial, confident, and gallery-led: large condensed display typography, strong black/white/gold contrast, deliberate image cropping, and asymmetric compositions create the identity while the content remains simple to understand and navigate.

The design intent is to:

- make the gallery identity and primary location action immediately legible on Home;
- use gallery imagery as a substantial part of the editorial story rather than decorative filler;
- make the Location experience direct: map artwork first, then address and visit information;
- preserve a clear distinction between the dark Home footer and gold Location footer;
- transform the composition meaningfully as space narrows rather than merely scaling the desktop arrangement;
- preserve content order, operability, and visible focus as visual layouts change;
- use the supplied 1440 px, 768 px, and 375 px designs as fidelity anchors, not automatically as implementation breakpoints.

## 3. Source and scope

### Design source

- `SRC-DS-001` → `🤖 Workflow` page (`2148:2`).
- Home / Desktop (`2148:1957`), Tablet (`2148:2140`), Mobile (`2148:2169`).
- Location / Desktop (`2148:2069`), Tablet (`2148:2196`), Mobile (`2148:2218`).
- Supporting responsive component sets and the page-local style-guide documentation.
- Fresh Stage 3 inspection: `VER-004`.

### Repository context

`SRC-REPO-001` remains the repository implementation baseline. `VER-005` confirms that current `main` differs from that pinned commit only by expected workflow/control documentation; `frontend/` is unchanged.

The current frontend contains the Astro starter structure and starter assets only. No approved gallery logo, gallery photography, map artwork, gallery-specific component implementation, or matching design-system assets are present in the repository baseline. This is a resource-mapping observation, not an implementation plan.

### Excluded

- Figma pages outside `🤖 Workflow`, except read-only usage inspection required to protect global resources.
- New product behavior not supported by requirements or design evidence.
- Interactive map behavior.
- Social destinations or interaction semantics that have not been approved.
- Backend, persistence, authentication, analytics, CMS, commerce, or other application capabilities outside current scope.

## 4. Information architecture and reading order

### Home

The intended content sequence remains:

1. Gallery identity and hero image.
2. Introductory copy.
3. `OUR LOCATION` primary action.
4. `YOUR DAY AT THE GALLERY` heading and supporting copy with gallery imagery.
5. Additional gallery imagery that continues the editorial story.
6. `COME & BE INSPIRED` heading and supporting copy.
7. Dark gallery footer with logo, descriptive copy, and social-brand icons.

Desktop can visually overlap or juxtapose parts of this sequence, but responsive transformation must not make the reading order ambiguous. Tablet and mobile evidence already simplify the hero and gallery composition while preserving this hierarchy.

### Location

The intended content sequence remains:

1. Map artwork with marker and `BACK TO HOME` action.
2. `OUR LOCATION` heading.
3. `99 KING STREET` address heading.
4. Newport / Rhode Island / United States address.
5. Gallery visit/opening information.
6. Gold gallery footer with logo, descriptive copy, and social-brand icons.

The map is visually prominent but must not become the only carrier of location information; the visible textual address remains the durable content source.

## 5. Screen and layout structure

### Home

**Wide composition — observed at 1440 px**

- The hero uses a three-part editorial relationship: dark field, hero artwork, and white information area.
- The oversized `MODERN ART GALLERY` title bridges the dark/image portion and carries the strongest visual weight.
- Intro copy and `OUR LOCATION` sit in the white region.
- Gallery content is centered within a narrower editorial canvas and uses asymmetrical image/text groupings rather than a uniform card grid.
- The dark footer spans the viewport and stays visually separate from the white gallery content.

**Medium composition — observed at 768 px**

- The hero becomes a simpler image-plus-content horizontal composition.
- The title moves into the content side instead of retaining the desktop title-over-dark-field treatment.
- Gallery modules still use side-by-side relationships, but with tighter proportions and less empty space.
- The footer remains horizontal.

**Narrow composition — observed at 375 px**

- Hero image, title, copy, and action form a vertical reading sequence.
- Gallery modules become stacked and preserve editorial image prominence.
- `COME & BE INSPIRED` remains a dark visual block within the white page.
- The footer becomes a vertical composition.

### Location

**Wide and medium compositions — observed at 1440 px and 768 px**

- Map artwork leads the page.
- `BACK TO HOME` overlays the map region near the leading edge.
- Marker remains prominent within the intended map crop.
- Location details use a two-column relationship: page heading on one side; address and descriptive copy on the other.
- The gold footer is horizontal.

**Narrow composition — observed at 375 px**

- Map remains first and keeps the overlaid return action.
- Location details stack into a single reading column.
- The gold footer becomes vertical and uses the tighter mobile side padding observed in its own source variant.

## 6. Design decisions

### DES-001 — Preserve the editorial hierarchy rather than flattening the design into generic sections

- **Classification:** Confirmed from approved design evidence and requirements.
- **Intent:** Keep the hero, gallery imagery, black editorial panels, and asymmetric image/text relationships as the defining visual structure of Home.
- **Evidence:** `EVD-007`, `EVD-009`–`EVD-016`; fresh visual verification `VER-004`.
- **Requirement references:** `REQ-FR-001`, `REQ-FR-007`, `REQ-NFR-001`.
- **Implications:** Responsive adaptation may rearrange modules, but it should not convert the experience into an unrelated generic stacked-card layout.

### DES-002 — Keep gallery imagery content-bearing and compositionally important

- **Classification:** Confirmed.
- **Intent:** The approved photographs should retain their relative visual prominence and subject/crop emphasis at each evidence anchor.
- **Evidence:** `EVD-016`, `EVD-044`, `EVD-051`–`EVD-058`, `AUD-006`.
- **Requirement references:** `REQ-FR-001`, `REQ-FR-007`, `REQ-DR-001`, `REQ-NFR-001`.
- **Implications:** Image containers may crop responsively where the source demonstrates cropping, but essential editorial subjects should remain visible.

### DES-003 — Treat the Location map as artwork, not a map application

- **Classification:** Confirmed.
- **Intent:** Preserve the grayscale map composition, fixed visual marker, and overlaid return action as shown, while the textual address below remains the authoritative visit information.
- **Evidence:** `EVD-008`, `EVD-012`–`EVD-014`, `EVD-018`, `AUD-006`.
- **Requirement references:** `REQ-FR-002`, `REQ-FR-007`, `REQ-DR-001`.
- **Implications:** No zooming, panning, geolocation, map controls, or external map service is part of the approved design intent.

### DES-004 — Preserve page-specific footer themes and demonstrated spacing differences

- **Classification:** Confirmed for visual output; intent behind the padding difference remains open.
- **Intent:** Home uses the dark footer theme and Location uses the gold footer theme. Preserve the supplied mobile side-padding difference rather than normalizing it without authority.
- **Evidence:** `EVD-019`, `EVD-037`, `AUD-005`.
- **Requirement references:** `REQ-FR-005`, `REQ-NFR-001`.
- **Implications:** Dark mobile remains visually roomier at the sides than Gold mobile unless `Q-DES-001` is later resolved differently.

### DES-005 — Use the approved local visual foundations without inventing a new source design system

- **Classification:** Confirmed.
- **Intent:** Preserve the supplied typography hierarchy and the four foundation colors as the visual source of truth for this scope.
- **Evidence:** `EVD-020`–`EVD-033`, `AUD-004`.
- **Requirement references:** `REQ-NFR-001`.
- **Implications:** Later implementation may create semantic code tokens, but Stage 3 does not claim those semantics already exist in Figma.

### DES-006 — Preserve source copy and allow natural text reflow

- **Classification:** Confirmed content plus recommended resilience.
- **Intent:** Initial implementation should reproduce approved copy exactly while letting text wrap naturally when space changes, without overlap or clipping.
- **Evidence:** `EVD-007`, `EVD-008`, `AUD-007`.
- **Requirement references:** `REQ-FR-001`, `REQ-FR-002`, `REQ-DR-001`, `REQ-AR-005`, `REQ-NFR-002`.
- **Implications:** No localization or alternate-copy system is designed here. Layout resilience must not depend on text remaining on the exact source line breaks.

### DES-007 — Keep social icons visually present without inventing link behavior

- **Classification:** Confirmed visual intent; interaction remains open.
- **Intent:** Preserve Facebook, Instagram, and Twitter icon artwork in both footers. Their destination and interactive semantics remain unresolved.
- **Evidence:** `EVD-051`–`EVD-054`, `AUD-003`, `Q-PROD-001`, `Q-CONT-001`.
- **Requirement references:** `REQ-FR-005`, `REQ-AR-002`, `REQ-AR-004`.
- **Implications:** Stage 4 must make the footer behavior observable without fabricating URLs. If the icons become links later, the interaction needs accessible names, keyboard operation, focus treatment, and a usable target area.

## 7. Visual system

### Typography

| Role | Approved style | Intended usage | Evidence |
|---|---|---|---|
| Hero display / Large | Big Shoulders Display Black, 96 px, 90% line height | Home desktop hero title | `EVD-020` |
| Hero display / Medium | Big Shoulders Display Black, 70 px, 90% line height | Home tablet hero title | `EVD-021` |
| Hero display / Small | Big Shoulders Display Black, 60 px, 90% line height | Home mobile hero title | `EVD-022` |
| Page heading / Large | Big Shoulders Display Black, 70 px, 100% line height | Location desktop page heading | `EVD-023` |
| Page heading / Compact | Big Shoulders Display Black, 55 px, 90% line height | Location tablet/mobile page heading | `EVD-024` |
| Section heading / Large | Big Shoulders Display Black, 60 px, 100% line height | Home desktop editorial headings | `EVD-025` |
| Section heading / Compact | Big Shoulders Display Black, 50 px, 90% line height | Home tablet/mobile editorial headings | `EVD-026` |
| Address heading | Big Shoulders Display Black, 36 px, 100% line height | `99 KING STREET` | `EVD-027` |
| Body / Large | Outfit Light, 22 px, 140% line height | Desktop body copy | `EVD-028` |
| Body / Medium | Outfit Light, 18 px, 140% line height | Tablet/mobile body and footer copy | `EVD-029` |
| Body / Footer | Outfit Light, 18 px, 28 px line height | Footer evidence where specifically applied | `EVD-030` |
| Action label | Big Shoulders Display ExtraBold, 20 px, uppercase, ~3.64 px tracking | Primary navigation actions | `EVD-031` |

These are source roles, not a mandate to hard-code every viewport-specific value directly. Intermediate-width behavior must preserve hierarchy and legibility.

### Color foundations

| Source token | Value | Intended use | Evidence |
|---|---:|---|---|
| `colors/grey/900` | `#151515` | Primary dark surfaces and dark text | `EVD-032` |
| `colors/grey/700` | `#444444` | Supporting text tone where demonstrated | `EVD-032` |
| `colors/white` | `#FFFFFF` | White surfaces and inverse text | `EVD-032` |
| `colors/gold/500` | `#D5966C` | Accent/action detail and Location footer | `EVD-032` |

No extra semantic palette is asserted by Stage 3. Contrast intent should be preserved and measured later in implementation validation rather than assumed from appearance.

### Spacing and radius foundations

- Available spacing values: 0, 2, 4, 6, 8, 12, 16, 20, 24, 32, 40, 48, 64, 80 px (`EVD-033`).
- Available radii: 0, 4, 6, 8, 10, 12, 16, 20, 24, 999 px (`EVD-033`).
- The design is predominantly square-edged; do not introduce rounded-card styling merely because radius tokens exist.
- No local effect or grid styles are part of the approved evidence.

### Imagery and icons

- Hero and gallery photography should preserve demonstrated subject emphasis and aspect behavior.
- The map artwork is grayscale and page-defining.
- The marker is a consistent 66 × 88 visual element across supplied map variants.
- Logo and social marks are vector identity assets.
- Decorative crops may change between responsive states, but meaningful content must not be accidentally removed.

## 8. Components and patterns

| Component | Purpose | Anatomy | Variants | States | Reuse evidence |
|---|---|---|---|---|---|
| Navigation / Our Location | Primary Home-to-Location action | Label plus directional gold segment | One action pattern | Default, Hover, Focus | Home at all three viewports, `EVD-034` |
| Navigation / Back Home | Return action from Location | Gold directional segment plus label | One action pattern | Default, Hover, Focus | Location at all three viewports, `EVD-035` |
| Hero | Gallery introduction | Image, title, description, primary action, desktop dark field | Desktop, Tablet, Mobile | Responsive variants | `EVD-036` |
| Footer | Gallery identity and supporting content | Logo, description, social icons | Dark/Gold × Desktop/Tablet/Mobile | Responsive/theme variants | `EVD-037`, `EVD-019` |
| Gallery Content | Home editorial story | Text modules plus three gallery-image roles | Desktop, Tablet, Mobile | Responsive variants | `EVD-038`, `EVD-016` |
| Location / Details | Visit information | Page heading, address heading/address, descriptive copy | Desktop, Tablet, Mobile | Responsive variants | `EVD-039`, `EVD-017` |
| Map / Hero | Location visual lead | Map crop, marker, Back Home action | Desktop, Tablet, Mobile | Responsive variants | `EVD-040`, `EVD-018` |

The source demonstrates responsive component variants, but Stage 3 does not prescribe whether the Astro implementation mirrors these Figma component boundaries one-to-one.

## 9. Interaction intent

### DES-INT-001 — `OUR LOCATION` is the primary Home navigation action

- **Trigger:** User activates the `OUR LOCATION` control.
- **Intended result:** Navigate from Home to the Location experience.
- **Pattern:** Standard page-navigation action.
- **Motion:** Source hover evidence uses a 0.2-second dissolve. Motion is non-essential and may be removed/reduced for reduced-motion preference.
- **Focus or keyboard implication:** The control must be keyboard reachable and preserve a clearly visible focus treatment equivalent in prominence to the supplied Focus variant.
- **Evidence and snapshot:** `EVD-034`, `EVD-046`, `EVD-048`, `EVD-049`, `AUD-002`, `SRC-DS-001`.
- **Requirement references:** `REQ-FR-003`, `REQ-AR-002`, `REQ-AR-003`, `REQ-AR-006`.

### DES-INT-002 — `BACK TO HOME` is the primary Location return action

- **Trigger:** User activates the `BACK TO HOME` control.
- **Intended result:** Navigate from Location back to Home.
- **Pattern:** Standard page-navigation action.
- **Motion:** Match the visual state-transition intent of the paired navigation component; any retained non-essential transition must respect reduced motion.
- **Focus or keyboard implication:** Keyboard operation and a visible focus state are required.
- **Evidence and snapshot:** `EVD-035`, `EVD-047`–`EVD-049`, `AUD-002`, `SRC-DS-001`.
- **Requirement references:** `REQ-FR-004`, `REQ-AR-002`, `REQ-AR-003`, `REQ-AR-006`.

### DES-INT-003 — Social interaction remains intentionally unresolved

- **Trigger:** Not approved.
- **Intended result:** The source proves social-brand presence, not a destination or behavior.
- **Pattern:** Undecided until `Q-PROD-001` is resolved.
- **Motion:** No social hover/focus motion is demonstrated.
- **Focus or keyboard implication:** If Stage 4 defines these items as links, they must become keyboard operable and visibly focusable; if they remain non-interactive artwork, they must not create false interactive affordance.
- **Evidence and snapshot:** `AUD-003`, `Q-PROD-001`, `Q-CONT-001`, `SRC-DS-001`.
- **Requirement references:** `REQ-FR-005`, `REQ-AR-002`, `REQ-AR-004`.

## 10. Responsive intent

### DES-RWD-001 — Transform the Home hero when the horizontal composition no longer supports its hierarchy

- **What remains stable:** Hero image, gallery title, intro copy, and `OUR LOCATION` action all remain present.
- **What becomes fluid:** Image width/crop, content width, title line wrapping, and surrounding whitespace.
- **What changes:** Wide uses the dark-field/image/white-content editorial composition; medium uses image plus content; narrow stacks image before text/action.
- **Content-driven transition condition:** Change composition when the wide arrangement can no longer keep the title, copy, CTA, and intended image subject legible without collision, excessive compression, or clipping.
- **Evidence, snapshot, uncertainty:** `EVD-015`, `AUD-001`, `SRC-DS-001`. Exact implementation thresholds are intentionally deferred.

### DES-RWD-002 — Preserve gallery narrative order while changing from interleaved to stacked modules

- **What remains stable:** All approved headings, copy, and three gallery-image roles remain present and in a coherent story sequence.
- **What becomes fluid:** Module widths, image proportions/crops, gaps, and line wrapping.
- **What changes:** Desktop/tablet use horizontal image/text relationships; mobile uses vertical stacks.
- **Content-driven transition condition:** Stack when side-by-side modules would make text or key image content too compressed or cause collision.
- **Evidence, snapshot, uncertainty:** `EVD-016`, `AUD-001`, `SRC-DS-001`.
- **Requirement references:** `REQ-FR-006`, `REQ-AR-005`, `REQ-NFR-002`.

### DES-RWD-003 — Stack Location details when the two-column relationship no longer fits comfortably

- **What remains stable:** Page heading, address heading, address lines, and descriptive copy.
- **What becomes fluid:** Column widths, gap, and text wrapping.
- **What changes:** Wide/medium are side-by-side; narrow becomes one vertical reading column.
- **Content-driven transition condition:** Stack before either column becomes too narrow to preserve readable heading/body proportions or before the columns collide.
- **Evidence, snapshot, uncertainty:** `EVD-017`, `AUD-001`, `SRC-DS-001`.
- **Requirement references:** `REQ-FR-006`, `REQ-AR-005`, `REQ-NFR-002`.

### DES-RWD-004 — Preserve map composition and action visibility across crop changes

- **What remains stable:** Map artwork, marker, and `BACK TO HOME` action remain visible; map is not interactive.
- **What becomes fluid:** Map crop and overlay positions.
- **What changes:** Desktop uses the standalone map-image composition; tablet/mobile use distinct source crops and repositioned overlays.
- **Content-driven transition condition:** Adjust crop/position as needed to keep the supplied visual relationship readable and prevent the marker or return action from being clipped or obscured.
- **Evidence, snapshot, uncertainty:** `EVD-018`, `AUD-006`, `Q-DES-002`, `SRC-DS-001`. Continuous crop interpolation is not demonstrated and must be specified conservatively later.
- **Requirement references:** `REQ-FR-002`, `REQ-FR-006`, `REQ-FR-007`, `REQ-NFR-002`.

### DES-RWD-005 — Footer changes orientation while retaining page-specific theme

- **What remains stable:** Logo, descriptive copy, and social-brand icons.
- **What becomes fluid:** Internal spacing and content widths.
- **What changes:** Desktop/tablet are horizontal; mobile is vertical.
- **Content-driven transition condition:** Stack when the horizontal grouping cannot preserve readable copy and adequate separation.
- **Evidence, snapshot, uncertainty:** `EVD-019`, `AUD-001`, `AUD-005`, `SRC-DS-001`.
- **Requirement references:** `REQ-FR-005`, `REQ-FR-006`, `REQ-NFR-001`, `REQ-NFR-002`.

### DES-RWD-006 — Intermediate and extreme widths must reflow without page-level horizontal scrolling

- **What remains stable:** Essential content, navigation, hierarchy, and accessible reading order.
- **What becomes fluid:** Section widths, whitespace, typography wrapping, image crops, and arrangement before/after each content-driven transition.
- **What changes:** Nothing may depend on the viewport equaling exactly 375, 768, or 1440 px.
- **Content-driven transition condition:** Layout failure—not a familiar device number—triggers transformation.
- **Evidence, snapshot, uncertainty:** `AUD-001`, `REQ-FR-006`, `REQ-AR-005`, `REQ-NFR-002`.
- **Requirement references:** `REQ-FR-006`, `REQ-AR-005`, `REQ-NFR-002`.

## 11. States and edge cases

### Supplied states

- Primary navigation controls: Default, Hover, Focus.
- Page/footer themes: Home Dark and Location Gold.
- Responsive variants: Desktop, Tablet, Mobile for major page patterns.

### Not supplied or not applicable to current static scope

- Active/selected navigation state: not demonstrated.
- Disabled state: not demonstrated and not required for the two page-navigation actions.
- Loading, empty, error, and success states: no dynamic data behavior exists in the approved scope.
- Form validation: not applicable.
- Map loading/error state: not applicable because the map is approved as static artwork.

### Content and asset edges

- Approved copy is the initial source of truth.
- Text should reflow naturally without layout collision at intermediate widths or browser zoom.
- Long-copy/localization variants are not evidenced; no alternate editorial layout is invented.
- Missing/failed-image presentation is not designed by the source. Stage 4 can define implementation-safe behavior where needed, but it must not fabricate a visual error UI.
- Intentional image cropping is acceptable; accidental loss of the principal subject or page-level horizontal overflow is not.
- Footer padding asymmetry on mobile remains deliberate output until resolved by design authority.

## 12. Accessibility intent

### Semantic hierarchy and reading order

The DOM implementation should express the same meaningful page sequence documented in Section 4. Visual positioning must not create a contradictory assistive-technology order. Stage 4 owns the exact semantic elements and page titles; Stage 3 establishes the hierarchy they must express.

### Keyboard and focus

- `OUR LOCATION` and `BACK TO HOME` must be keyboard operable as page-navigation controls.
- Their focus state must remain clearly visible and at least as intentional as the supplied Figma focus variants.
- Focus order should follow the meaningful reading/action order rather than visual coordinates created by asymmetric layout.
- Social icons must not become keyboard stops unless they receive approved interactive behavior.

### Images and alternative text

- Gallery imagery, logo, map artwork, marker, and social icons require implementation-time semantic classification.
- No essential visit information should exist only inside the map image; the textual address and visit details remain visible content.
- Decorative image fragments or redundant marks should be hidden from assistive technology when they add no independent meaning.
- Meaningful images should receive concise alternatives based on their content/purpose, not filenames.
- Stage 4 must decide individual asset semantics rather than applying one alt-text rule to every image.

### Reflow and zoom

The layout should remain readable and operable as available inline space decreases, including widths between the three source examples. Content may wrap and modules may stack; it should not be clipped, overlap, or require page-level horizontal scrolling because of layout choices.

### Contrast

Preserve the approved black/white/gold visual relationships. Actual contrast compliance must be measured during implementation validation; Stage 3 does not claim a pass from visual inspection alone.

### Motion

The only evidenced motion is a short primary-action hover dissolve. It is non-essential. If reproduced, it should be reduced or removed under a reduced-motion preference while keeping the state change clear.

### Target size and icon-only controls

The primary navigation controls are large in the source (260 × 72). Social glyphs are visually small; if they later become links, the clickable/focusable area should be made comfortably operable without visually enlarging the glyph unnecessarily. Exact test criteria belong in Stage 4.

## 13. Assets and design-system mapping

| Asset or pattern | Source evidence | Existing project resource at `SRC-REPO-001` | Required later action | Risk |
|---|---|---|---|---|
| Gallery logo | `4:905`, `EVD-051` | No matching gallery asset observed | Obtain/export approved vector asset during implementation preparation | Incorrect substitute branding |
| Hero image | `16:1601`, `EVD-055` | No matching gallery image observed | Obtain approved source image and preserve responsive crop intent | Wrong crop/subject emphasis |
| Gallery images | `16:1610`, `16:1609`, `16:1605`, `EVD-056`–`EVD-058` | No matching gallery images observed | Obtain approved source images | Fidelity loss |
| Map artwork | `16:1655`, `EVD-018`, `AUD-006` | No matching map asset observed | Obtain approved artwork/crops; retain static-map intent | Replacing with interactive map or wrong crop |
| Marker | `16:959` | No matching asset observed | Obtain/export approved vector | Scale/position drift |
| Social icons | `16:372`, `16:371`, `16:370` | No matching gallery social assets observed | Obtain/export vectors; interaction stays unresolved until specified | Invented links/states |
| Navigation patterns | `8:200`, `16:264` | No gallery-specific component implementation observed | Map to implementation only after Stage 4 behavior is approved | Overfitting code to Figma structure |
| Typography | `EVD-020`–`EVD-031` | No project-local gallery font resources observed | Implementation must source approved font files/service legally and reproducibly | Fallback metrics alter composition |
| Foundation tokens | `EVD-032`, `EVD-033` | No matching gallery token layer observed | Later implementation may map values to code tokens without claiming Figma semantic roles | Unnecessary token invention |

The current repository's `astro.svg`, `background.svg`, `Welcome.astro`, and starter page/layout are scaffold resources, not approved gallery design assets.

## 14. Inferences, recommendations, and open questions

### Inferred

- The site is intended to remain a focused two-page editorial experience with no dynamic application state.
- The responsive variants represent meaningful composition changes rather than three independently fixed canvases.
- The map is primarily a visual orientation device because the textual address carries the necessary visit information.

### Recommended

- Use source viewports as fidelity-comparison anchors while selecting actual implementation transitions from content/layout failure.
- Preserve primary-action Default/Hover/Focus states and treat their motion as optional/non-essential.
- Keep approved source imagery and map crop intent rather than substituting generic stock imagery or an interactive map.
- Preserve the Dark-mobile versus Gold-mobile padding difference until the design owner resolves it.
- Delay social-link behavior until approved destinations and labels exist.
- Validate intermediate widths and zoom/reflow before implementation acceptance.

### Open questions

- `Q-PROD-001` — Are Facebook, Instagram, and Twitter intended to be links, and what are the approved destinations?
- `Q-DES-001` — Is the Dark-mobile 40 px vs Gold-mobile 16 px footer padding difference intentionally page-specific?
- `Q-DES-002` — What is the preferred continuous map-crop behavior between supplied viewport examples?
- `Q-CONT-001` — If social icons become links, are the brand names the approved accessible labels?
- `Q-TECH-001` — Exact heading levels, landmarks, and page titles belong to Stage 4 specification.
- `Q-TECH-002` — Exact responsive transition thresholds belong to later specification/planning and must be justified by layout failure.

None of these questions blocks Stage 3 design intent. `Q-PROD-001` and `Q-CONT-001` must be resolved or safely constrained before interactive footer behavior can be accepted.

## 15. Risks and inconsistencies

| Finding | Evidence | Impact | Resolution owner |
|---|---|---|---|
| Only three supplied viewport anchors | `AUD-001` | Intermediate-width behavior can be overfit if anchors are treated as breakpoints | Stage 4 specification / implementation planning |
| Focus visuals exist without source keyboard mechanics | `AUD-002` | Accessible behavior must be explicitly specified | Stage 4 |
| Social destinations/states are missing | `AUD-003` | Cannot safely invent links or focus states | Product owner / Stage 4 |
| Figma tokens are foundational rather than semantic | `AUD-004` | Code-token mapping could overclaim source semantics | Implementation planning |
| Mobile footer padding differs by page theme | `AUD-005` | Silent normalization would reduce fidelity | Design owner; preserve meanwhile |
| Map crops differ structurally by viewport | `AUD-006` | Intermediate crops require deliberate handling | Stage 4 / implementation planning |
| Long-copy and missing-asset states are not supplied | `AUD-007` | Edge behavior requires conservative resilience rather than invented UI | Stage 4 |
| Reduced-motion behavior is not supplied | `AUD-008` | Retained transitions need an accessibility rule | Stage 4 |
| Approved gallery assets/fonts are absent from repository baseline | `VER-005`, repository resource inspection | Implementation cannot achieve fidelity using starter assets alone | Planning / implementation |

## 16. Review

### Pass 1 — Completeness and correctness

- [x] Purpose, hierarchy, structure, visual roles, components, interactions, responsive behavior, states, content, accessibility intent, and assets are covered.
- [x] The document records design intent and relationships rather than copying the Figma property tree.
- [x] `SRC-DS-001` and `SRC-REPO-001` are the actual active inputs and were freshly checked at Stage 3 entry.
- [x] Home and Location are covered at all six supplied screen variants.
- [x] Open social, footer-padding, map-crop, semantic, and transition questions remain explicit instead of being silently resolved.

Pass 1 result: Passed on 2026-08-15. No blocking omission was found.

### Pass 2 — Consistency, traceability, source integrity, risks, and uncertainty

- [x] `DES-*`, `DES-RWD-*`, and `DES-INT-*` identifiers follow the workflow naming convention.
- [x] Decisions reference approved evidence and relevant `REQ-*` requirements.
- [x] Fresh source verification is recorded as `VER-004` and `VER-005`.
- [x] No arbitrary CSS breakpoint is presented as confirmed.
- [x] No social destination, interactive map behavior, backend behavior, or unsupported application state is invented.
- [x] Observed/confirmed design output is separated from recommendations and open questions.
- [x] The repository starter state is described as observed context without prescribing implementation architecture.
- [x] Accessibility intent is documented without claiming implementation compliance before implementation exists.

Pass 2 result: Passed on 2026-08-15. Stage 3 is ready for project-owner gate review.

## 17. Completion summary

- Artifact: `DESIGN.md`
- Workflow artifact: `ART-DESIGN`
- Baseline: `SRC-DS-001`, `SRC-REPO-001`
- Stage 3 source checks: `VER-004`, `VER-005`
- Review status: both required review passes completed
- Blocking questions: none for Stage 3
- Next action in Gated mode: project-owner approval of the Stage 3 gate; do not advance to Stage 4 without explicit approval.
