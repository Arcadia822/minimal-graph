# Minimal Graph Style

Use this as the canonical visual system for WeChat article covers, Xiaohongshu cards, and technical editorial infographics.

## Core identity

- Pure white editorial-technical background.
- Maple font for all visible text.
- Mostly black and white; generated illustrations may contain color, but the UI/chart system remains restrained.
- Structure beats decoration. Use layout, scale, distance, and alignment for hierarchy.

## Palette and line system

| Token | Value / rule |
|---|---|
| Background | `#FFFFFF` only |
| Text | `#111111` primary; avoid multiple gray levels |
| Strong block | `rgba(0,0,0,.82)` for title/tag blocks |
| Structural line | one global line tone, usually `rgba(0,0,0,.42)`, `1px` |

Rules:
- Use one structural line color and one line width globally.
- Do not use rounded corners, shadows, glow, gradients, glass, soft edges, full-frame borders, outline-card systems, double lines, or close parallel lines.
- Do not use line weight/color changes to show hierarchy.

## Typography

- Font family: Maple / MapleMono-CN style.
- Title weight: medium, not ultra-bold.
- Body weight: regular.
- Footer metadata: same size, opacity, and weight on both sides; right side may be italic only.
- Minimum safe text margin from any divider/module boundary: 24px.

## Header and thesis

- Title block is the only strong header object.
- Do not add subtitles.
- Do not add a loose right-side date label; integrate dates inside the title block or omit them.
- Put the thesis directly below the title, without headings like “一句话”.
- Let thesis text wrap naturally; avoid manual awkward line breaks.

## Global vertical rhythm

- Balance header/body/footer whitespace optically.
- Avoid a large empty moat after the header.
- Avoid squeezing the footer after a spacious header.
- Treat dividers as rhythm anchors.
- Typical 16:9 rhythm: title top 60–72px; first body divider 280–315px; footer/source baseline 24–36px from bottom.

## Footer

- Left: source/citation only, max one line; leave empty when no source is needed.
- Right: requested author/signature, italic, same size/opacity/weight as source.
- Footer is metadata, not a visual anchor.
- No footer heading or explanatory sentence.

Recommended CSS:
```css
.source,.signature{font-size:15px;opacity:.48;font-weight:400;color:#111}
.signature{font-style:italic}
```

## WeChat cover images

A WeChat cover is illustration-first, not an infographic with an illustration module.

- The generated illustration is the full main visual / background of the image.
- Overlay the article title on top of the illustration with HTML/CSS for exact Chinese typography.
- Do not place the illustration inside a card, frame, chart module, or infographic grid.
- Keep title/UI slightly above center.
- Reserve the bottom 18–22% of the image as a WeChat title-overlay safety zone with no essential text.
- Cover UI must follow the same Maple, translucent black title block, straight-line, no-rounded-corner rules.
- The cover may have emotional color and atmosphere from the illustration; the overlaid title/UI remains disciplined and minimal.
- Use HTML for exact Chinese title text; never rely on image generation for readable Chinese title text.

## Generated illustration modes

Use generated color artwork only in these modes:

1. `frame-contained-generated`
   - Place raster illustration inside a rectangular frame.
   - Frame uses the global 1px line style, no fill, no rounded corners.
   - Inset the image by 1px so the frame remains visible.
   - CSS pattern: `.frame img{left:1px;top:1px;width:calc(100% - 2px);height:calc(100% - 2px);object-fit:cover}`.

2. `transparent-generated-object`
   - Place a generated person/object/thing with white, transparent, or clean background directly on the canvas.
   - No added shadow, outline, or container.
   - Do not overlap text, arrows, labels, divider lines, or footer.

Do not use SVG doodles as a substitute when the user asks for generated illustration insertion.

## Chart rules

### Pie / donut

- Use only for “one part vs the rest”.
- One emphasized slice may be black.
- All other slices stay white/empty with single-line separators.
- No legend.
- No grayscale category fills.
- Do not label the slice directly; put one concise explanation line below the chart.
- If multiple categories matter, use bars, table, or small multiples instead.

### Bar / line / timeline

- Keep axes and guides on the global line style.
- Avoid decorative ticks and dense labels.
- Labels must fit inside the SVG/module safe box.
- Timelines can use black year tags; do not add connector lines unless needed.

## Secondary text frame

- Optional rectangular 1px line frame around less-important text.
- No fill, no rounded corners.
- Max one per page.
- Use for caveats/definitions only.
- Keep at least 24px from divider/footer lines; omit it if it collides.

## Clipping and collision guards

- Chart labels must live inside the SVG/module viewport with at least 24px safe margin.
- Do not rely on `overflow: visible` to rescue labels.
- No module, frame, text block, object, or chart may intersect structural lines.
- Keep footer zone clean.
- Confirm all of this from the screenshot, not only from DOM/CSS inspection.

## Divider Optionality v11

- Header/body/footer divider lines are optional rhythm anchors, not mandatory structure.
- Do not add horizontal dividers by default.
- Use dividers only when they clarify grouping or improve visual rhythm.
- A page may rely entirely on whitespace, alignment, and scale.
- Avoid making every layout look sliced into header/body/footer bands.

## Sequence Diagram Line Rules v11

- Message arrows must not pass through participant lifelines.
- Arrow line endpoints should stop 8–12px before the target lifeline or start 8–12px after the source lifeline.
- Do not use white background masks on labels or arrowheads when they cause visible gaps at line crossings.
- Prefer SVG paths/lines over CSS pseudo-element arrows for sequence diagrams, because SVG can control endpoints precisely.
- If labels need readability, place them above the message line with whitespace, not by masking the line behind them.
- Crossings should not create white breaks.

## WeChat Cover Text Minimalism v12

- Cover images should not include footer text, source text, signature, safety-zone hint, implementation tag, or small explanatory copy.
- Default cover text: main title only.
- Optional: one very short title-internal qualifier only when the article title needs it.
- Do not add metadata to covers; metadata belongs in article body or infographic pages.

## WeChat Cover Title Block Proportion v13

- Title block width must fit the title, not stretch as a generic banner.
- Use intrinsic width (`display:inline-block`, `width:auto`, or measured text width) unless a deliberate full-width editorial block is requested.
- Avoid short four-character lines inside a long horizontal black rectangle.
- Prefer natural title breaks based on meaning, not equal character count.
- Keep internal padding fixed, but let the outside block size follow the longest title line.
- If the title is short, use a compact block. If the title is long, break into meaningful lines and resize the block accordingly.

## Full-page Visualization Centering v14

- Full-page flowcharts, sequence diagrams, architecture diagrams, and major visualizations must be horizontally centered on the canvas.
- Center the visual bounding box, not just an individual node or container.
- Default allowed center deviation: ≤24px from canvas center for 2048px-wide output.
- If a title block or side annotation intentionally offsets the composition, the main visual still needs optical balance.
- Do not align a full-page diagram to the left content margin unless the layout explicitly has a right-side visual counterweight.
