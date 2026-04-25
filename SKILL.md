---
name: minimal-graph
description: Create minimal, deterministic information graphics and flow diagrams. Use when the user asks for clean technical diagrams, phone-readable Chinese charts, HTML/CSS/SVG visual assets, Markdown Viewer diagrams, process maps, architecture diagrams, or reusable minimal graph templates.
---

# Minimal Graph

Create deterministic, phone-readable information graphics with a restrained visual system. Use generated images only as illustration assets; put all text, layout, charts, labels, and page chrome in HTML/CSS/SVG or Markdown Viewer-derived diagrams.

## Load by task

| Task | Read |
|---|---|
| Any visual / infographic / cover | `references/editorial-minimal-style.md` and `references/html-infographic-checklist.md` |
| Markdown Viewer flowchart / UML / BPMN / Graphviz / architecture diagram | `references/markdown-viewer-flowcharts.md` |
| Mermaid/process diagram | `references/mermaid-normalization.md` |

## Core rules

- Use a consistent font system for every visible label; prefer Maple for Chinese when available.
- Prefer white background, dark text, one global 1px line tone, and layout hierarchy over decoration.
- Keep the reading order obvious: title → core structure → supporting labels → quiet metadata.
- Reduce density before reducing font size.
- If text or labels clip, overlap, or require zooming on mobile, the graphic is not done.

## Workflow

1. Define the graph's single purpose and reading order.
2. Remove information that does not support that purpose.
3. Choose the structure: nodes/edges, swimlanes, layers, timeline, comparison, or chart.
4. Build a deterministic source: HTML/CSS/SVG, Markdown Viewer grammar, Mermaid, or native SVG.
5. Render to SVG/PNG.
6. Inspect the final image for font consistency, clipping, overlap, alignment, and mobile readability.
7. Keep sources and outputs together.

## Engineering patterns

### HTML/CSS/SVG -> PNG

- Create a self-contained HTML page with a fixed viewport.
- Load the chosen font with `@font-face`.
- Use HTML/CSS/SVG for exact text, arrows, labels, charts, and layout.
- Screenshot with browser automation after checking the rendered image, not just DOM/CSS.

### Markdown Viewer -> SVG -> PNG

- Use Markdown Viewer grammar for diagram structure: Graphviz DOT, UML, BPMN, architecture, Vega, etc.
- Save the source grammar next to the output (`.dot`, `.mmd`, `.puml`, etc.).
- Render to SVG first.
- Convert SVG to PNG with a real vector renderer: preferred `rsvg-convert`; fallback Chromium screenshot; fallback CairoSVG/ImageMagick if available.
- If the renderer's native style conflicts with this system, use the SVG as layout reference and redraw in HTML/SVG using the minimal rules.

## Deliverables

For each visual set, keep source and outputs together:

```text
<project>/
├── page.html / diagram.dot / diagram.svg
├── output.png
└── assets/
```
