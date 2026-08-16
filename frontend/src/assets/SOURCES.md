# Visual asset sources

Production visual assets are committed locally; runtime rendering does not depend on the source URLs below.

## Typography
- Big Shoulders Display variable font: Google Fonts repository commit `352f6b7d9d6cc4fa9e242b931291d31b21a6dc84`, `ofl/bigshouldersdisplay/BigShouldersDisplay[wght].ttf`.
- Outfit variable font: Google Fonts repository commit `352f6b7d9d6cc4fa9e242b931291d31b21a6dc84`, `ofl/outfit/Outfit[wght].ttf`.
- Corresponding SIL Open Font License files are committed beside each font.
- Approved roles use Big Shoulders Display 800/900 and Outfit 300.

## Gallery, map, and brand artwork
- Local raster/SVG copies come from the Modern Art Gallery challenge asset snapshot `vanzasetia/art-gallery-website` at commit `66ee33fc04ff3789e227c1f5fc388ca11860b29b`, cross-checked against the approved Figma `🤖 Workflow` resources.
- Gallery raster assets retain desktop, tablet, and mobile art-direction variants.
- Location map artwork retains the pinned `images/{desktop,tablet,mobile}/image-map@2x.jpg` variants under `src/assets/map/` so the approved crops do not depend on a live map service.
- Brand artwork includes the approved logo, navigation arrows, marker, and social SVGs.

## Image semantics
- Informative images must receive concise purpose-based alternative text where rendered.
- Decorative images must use an empty `alt` value and must not duplicate nearby text.
- Static map artwork is decorative when the same location information is present semantically in the adjacent `<address>` content.
- Prefer Astro's local image pipeline so intrinsic dimensions and optimized output remain explicit.
