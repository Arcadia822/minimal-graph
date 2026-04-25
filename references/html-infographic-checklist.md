# HTML Infographic Checklist

Run this against the final screenshot.

## P0 must pass

- [ ] Maple font is visible for all text.
- [ ] Pure white background; no full-frame border.
- [ ] No subtitle.
- [ ] No rounded corners, shadows, gradients, glow, glass, or soft edges.
- [ ] All structural lines use one color and one 1px width.
- [ ] No double lines or close parallel lines.
- [ ] Title fits inside its block with safe padding.
- [ ] Thesis has no awkward manual line break.
- [ ] Header/body/footer whitespace is optically balanced.
- [ ] No text, chart label, or Mermaid label is clipped.
- [ ] No object/frame/text overlaps divider lines or footer.
- [ ] Footer left is source/citation only, max one line or empty.
- [ ] Footer right uses the requested signature with same size/opacity/weight as source.

## Chart checks

- [ ] Pie/donut has one black emphasized slice, white/empty remainder, no legend, no slice-side label.
- [ ] Pie/donut explanation appears below the chart.
- [ ] Bar/line labels are inside the SVG/module safe box.
- [ ] Timeline labels do not collide with tags or dividers.

## Illustration checks

- [ ] Generated illustration is raster/color artwork when requested, not an SVG placeholder.
- [ ] Framed illustration uses a 1px image inset so the frame is visible.
- [ ] Transparent/white object does not overlap text, arrows, labels, or footer.
- [ ] Color exists only in illustration assets unless explicitly requested.

## Mermaid checks

- [ ] Mermaid is full-width/single-page unless tiny.
- [ ] Mermaid SVG has been theme-normalized, not embedded raw.
- [ ] Mermaid nodes are white, rectangular, single-stroke, no shadows.
- [ ] Mermaid arrows use the same line tone and 1px weight.
- [ ] Mermaid visually belongs to the page.

## WeChat cover checks

- [ ] Bottom 18–22% safety zone contains no essential title/UI text.
- [ ] Title overlay uses HTML text, not generated-image text.
- [ ] Cover UI style matches infographic style.

## P0 v10 Mermaid correction

- [ ] No Mermaid node has black/dark fill with black text.
- [ ] Mermaid arrows are crisp and match the global 1px line tone.
- [ ] Mermaid arrowheads are hollow/outline-style when possible.
- [ ] Final graphic contains no implementation-note text such as “Mermaid used for layout”.

## P0 v11 Sequence/Layout Addendum

- [ ] Horizontal header/body/footer dividers are used only when they improve the layout, not by default.
- [ ] Sequence arrows do not cross through lifelines.
- [ ] Sequence arrowheads do not use white masks that create visible gaps.
- [ ] Labels do not erase lines behind them.

## P0 v12 Cover Addendum

- [ ] Cover has no footer/source/signature text.
- [ ] Cover has no implementation tag or safety-zone hint.
- [ ] Cover has no small explanatory copy outside the main title block.

## P0 v13 Cover Title Proportion

- [ ] Cover title block width matches the title text; it is not an oversized banner by accident.
- [ ] Title line breaks are semantic/natural, not arbitrary four-character chunks.
- [ ] Black block does not contain large empty horizontal space beside short lines.

## P0 v14 Full-page Centering

- [ ] Full-page diagram / major visualization is horizontally centered optically.
- [ ] Main visual bounding box center is within ~24px of canvas center unless intentionally counterbalanced.
- [ ] No large flowchart appears accidentally left- or right-biased.
