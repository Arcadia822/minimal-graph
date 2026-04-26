---
name: minimal-graph
description: Use when the user needs deterministic diagrams, infographics, covers, or reusable visual assets with strict readability, layout control, SVG or PNG rendering, or disciplined source and output organization.
---

# Minimal Graph

Create deterministic visual assets with explicit structure and restrained styling. The core skill owns graphic structure, layout, typography, rendering checks, and source/output organization; channel-specific publishing requirements belong in channel addons, not in the core rules.

## When to use

- The user needs a clean diagram, infographic, card, or cover that remains readable on mobile.
- The layout, labels, arrows, or chart geometry must be controllable in HTML/CSS/SVG or source grammar.
- The output must be reproducible as SVG/PNG with source files kept alongside exports.
- One core visual may later need channel-specific overlays or packaging without rewriting the core visual logic.
- Do not use this skill as a publishing SOP for a specific platform.

## Load by task

| Task | Read |
|---|---|
| Any deterministic visual asset | `references/editorial-minimal-style.md` and `references/html-infographic-checklist.md` |
| Markdown Viewer flowchart / UML / BPMN / Graphviz / architecture diagram | `references/markdown-viewer-flowcharts.md` |
| Mermaid/process diagram | `references/mermaid-normalization.md` |
| Channel-specific prompt addons or post-render packaging | `references/skill-red-review.md`, `references/channel-addons.md`, and the matching file under `references/channel-addons/` |

## Core rules

- Use a consistent font system for every visible label; prefer Maple for Chinese when available.
- Prefer white background, dark text, one global 1px line tone, and layout hierarchy over decoration.
- Keep the reading order obvious: title → core structure → supporting labels → quiet metadata.
- Reduce density before reducing font size.
- If text or labels clip, overlap, or require zooming on mobile, the graphic is not done.

## Channel boundary

1. Finish the core visual plan first: purpose, reading order, structure, and rendering path.
2. Load at most one channel addon per output variant. Its `prompt_addon` is appended after the core visual requirements.
3. Channel addons may narrow format, crop, packaging, or delivery expectations, but they must not rewrite the core visual system.
4. Run a channel `posthook` only after the rendered output passes readability and clipping checks.
5. Posthooks may create derivative exports, manifests, or delivery folders; they must not silently mutate the canonical source files or replace the validated core output.

## Workflow

1. Define the graph's single purpose and reading order.
2. Remove information that does not support that purpose.
3. Choose the structure: nodes/edges, swimlanes, layers, timeline, comparison, or chart.
4. Build a deterministic source: HTML/CSS/SVG, Markdown Viewer grammar, Mermaid, or native SVG.
5. Render to SVG/PNG.
6. Inspect the final image for font consistency, clipping, overlap, alignment, and mobile readability.
7. If needed, apply one channel addon for derivative packaging.
8. Keep sources and outputs together.

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
├── outputs/
│   └── <variant>.png
└── channels/
    └── <channel>/
```

## Common mistakes

- Mixing xhs / wx / channel packaging requirements into the core visual rules.
- Letting generated-image text replace deterministic HTML/SVG text for titles, labels, or annotations.
- Shipping only the final PNG without the source grammar, HTML, or SVG used to produce it.
