---
name: minimal-graph
description: Create strict minimal editorial visuals for WeChat articles, Xiaohongshu cards, covers, and technical infographics. Use whenever the user asks for WeChat article images, Xiaohongshu multi-page cards, HTML/CSS/SVG infographics, Markdown Viewer diagrams, cover images, phone-readable Chinese diagrams, or wants a reusable visual template with Maple font and black-white editorial rules.
---

# Minimal Graph

Create deterministic, phone-readable editorial visuals with a restrained black-white system. Use generated images only as illustration assets; put all Chinese text, layout, charts, labels, and page chrome in HTML/CSS/SVG or Markdown Viewer-derived diagrams.

## Load by task

| Task | Read |
|---|---|
| Any visual / infographic / cover | `references/editorial-minimal-style.md` and `references/html-infographic-checklist.md` |
| Full WeChat article visual package | `references/wechat-article-workflow.md` |
| Xiaohongshu multi-page cards | `references/xhs-card-template.md` |
| Markdown Viewer flowchart / UML / BPMN / Graphviz / architecture diagram | `references/markdown-viewer-flowcharts.md` |
| Mermaid/process diagram | `references/mermaid-normalization.md` |

## Core rules

- Use Maple font for every visible Chinese/English label unless the user explicitly asks otherwise.
- Prefer pure white background, black text, one global 1px line tone, and layout hierarchy over decoration.
- Do not claim an image/file is ready for review unless it has been sent as an attachment to the user. Local paths are not delivery.
- For public social images, do not expose private/local skill names, internal paths, credentials, or drafts.
- If the user says a page is OK, do not redraw it. Only change the requested page or element.

## WeChat article visuals

1. Write or stabilize article structure before making the full visual package.
2. Extract visual opportunities: cover, core explainer, architecture, workflow, comparison, original-blog remake, and ending illustration.
3. Build precise infographics as self-contained HTML/CSS/SVG and screenshot them.
4. Use Markdown Viewer grammar as structure source for diagrams when useful; restyle to this minimal system before final PNG.
5. For WeChat covers, account for title overlay and crop safety before publishing.

### WeChat cover constraints

- The cover is illustration-first. Do not turn it into a dense infographic.
- Do not add white/light overlays; WeChat title text is white and must remain readable.
- Do not put article title text on the cover by default; the platform title field carries it.
- Optional cover text is limited to brand/keyword tags such as product name or short concept.
- Keep essential UI away from the top crop danger zone and bottom title-overlay zone.
- Always generate a WeChat cover crop preview before final delivery.

## Xiaohongshu card workflow

1. Send the text storyboard first: title, note body, and each page’s content. Do not make images yet.
2. After user approval, generate image pages.
3. Send every page as an attachment for review.
4. Publish only after explicit confirmation.

Default 3-page structure:

1. Cover: title only, little or no supporting copy.
2. Workflow/logic: explain the process, not a pile of tool names.
3. Skills/resources: list only public/external skills or approved tools; include GitHub/source links when relevant.

## Engineering patterns

### HTML/CSS/SVG -> PNG

- Create a self-contained HTML page with fixed viewport (for example 2048×1152 for WeChat, 1242×1660 for Xiaohongshu).
- Load Maple from the local workspace with `@font-face`.
- Screenshot with browser automation after checking the rendered image, not just DOM/CSS.
- For Xiaohongshu, use a 3:4 canvas and large mobile-readable text.

### Markdown Viewer -> SVG -> PNG

- Use Markdown Viewer skills for diagram structure: Graphviz DOT, UML, BPMN, architecture, Vega, etc.
- Save the source grammar next to the output (`.dot`, `.mmd`, `.puml`, etc.) so the claim is auditable.
- Render to SVG first.
- Convert SVG to PNG with a real vector renderer: preferred `rsvg-convert`; fallback Chromium screenshot; fallback CairoSVG/ImageMagick if available.
- If the renderer’s native style conflicts with this system, use the SVG as layout reference and redraw in HTML/SVG using Maple and the minimal rules.

## Deliverables

For each visual set, keep source and outputs together:

```text
<project>/
├── page.html / diagram.dot / diagram.svg
├── output.png
├── crop-preview.png        # covers only
└── assets/
```

Then send the actual PNG/SVG files to the user.
