# Mermaid Normalization

Use Mermaid for layout, not for final visual style. Raw Mermaid output must be normalized before embedding.

## When to use Mermaid

- Use Mermaid for process flows, dependency chains, decision trees, feedback loops, and multi-step timelines.
- Give Mermaid a full-width page/section when it has more than five nodes.
- Do not squeeze Mermaid into a three-column layout unless the graph is tiny.
- Handwritten SVG is acceptable only for simple 2–4 step flows.

## Render flow

1. Write Mermaid code with explicit direction (`graph LR` for process chains, `graph TD` for hierarchy).
2. Increase Mermaid spacing where possible (`nodeSpacing`, `rankSpacing`, linear curves).
3. Render Mermaid to SVG using an available Mermaid renderer.
4. Post-process/wrap the SVG so it matches the Arcadia theme.
5. Embed the normalized SVG in the final HTML page.

## Required normalized style

- Font: Maple for SVG text and `foreignObject` labels.
- Background: transparent or white.
- Nodes: white fill, rectangular, 1px global line stroke, no shadows, no rounded corners, no colored fills.
- Text: `#111111`, consistent 20–24px, no clipping.
- Edges: same global line tone and 1px stroke; simple arrowheads using the same tone.
- Layout: enough spacing that labels, arrows, and any generated object do not collide.

## Generated object with Mermaid

- Prefer placing one white-background or transparent generated object beside/near the Mermaid graph as a visual anchor.
- Only overlay an object inside a Mermaid node when SVG coordinates are stable and manually checked.
- The object must not touch arrows or labels.
- If overlay becomes fragile, keep the object outside the SVG and align it in HTML.

## Normalization CSS pattern

```css
.mermaid svg{background:transparent!important;font-family:Maple,monospace!important}
.mermaid *{font-family:Maple,monospace!important}
.node rect,.node polygon,.node circle,.node ellipse{fill:#fff!important;stroke:rgba(0,0,0,.42)!important;stroke-width:1px!important;rx:0!important;ry:0!important;filter:none!important}
.nodeLabel,.label,.edgeLabel{font-family:Maple,monospace!important;color:#111!important;fill:#111!important;font-size:22px!important;font-weight:400!important}
.edgePath .path,.flowchart-link{stroke:rgba(0,0,0,.42)!important;stroke-width:1px!important}
.arrowheadPath,marker path{fill:rgba(0,0,0,.42)!important;stroke:rgba(0,0,0,.42)!important}
```

After screenshot, check: Mermaid looks native to the page, not like an imported plugin.

## v10 corrections

- Never allow black-fill nodes with black text. If a node is dark, text must be white; preferred default is white node + black text.
- Preferred arrows are hollow arrowheads to match the single-line theme.
- Do not rely only on Mermaid CSS variables; post-process SVG markers when needed.
- Remove implementation-explanation text from the final graphic, e.g. “Mermaid used for layout”. Keep such notes in `prompt.md` or docs, not on canvas.
- Final screenshot must show:
  - no black-on-black or low-contrast labels
  - arrows are crisp 1px single-line style
  - arrowheads are hollow or outline-style
  - no explanatory text collides with dividers
