# Visual asset sources

Production visual assets are committed locally; runtime rendering does not depend on the source URLs below.

## Typography
- Big Shoulders Display variable font: Google Fonts commit , .
- Outfit variable font: Google Fonts commit , .
- Corresponding SIL Open Font License files are committed beside each font.
- Approved roles use Big Shoulders Display 800/900 and Outfit 300.

## Gallery and brand artwork
- Local raster/SVG copies come from the Modern Art Gallery challenge asset snapshot at  commit , cross-checked against the approved Figma  resources.
- Desktop, tablet, and mobile raster variants are retained for later route-level art direction.

## Image semantics
- Informative images must receive concise purpose-based alternative text where rendered.
- Decorative images must use an empty  value and must not duplicate nearby text.
- Prefer Astro's local image pipeline so intrinsic dimensions and optimized output remain explicit.
