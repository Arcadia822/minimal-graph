# WeChat Article Visual Workflow

Use this workflow when producing a full visual package for a WeChat article.

## Article-first sequence

1. Define topic, reader, and article thesis.
2. Draft article structure before making visuals.
3. Extract visual opportunities: cover, core explainer infographic, chart page, process/Mermaid page, timeline, or generated illustration.
4. Decide which facts require live verification.
5. Produce visuals only after the story modules are stable.

## Skill/tool roles

- Use writing/research tools for article structure and factual grounding.
- Use image generation for cover backgrounds, framed illustrations, and white/transparent objects.
- Use HTML/CSS/SVG for exact Chinese text, layout, charts, and footer.
- Use Mermaid rendering for complex flows, then normalize the SVG.
- Use browser screenshot for final PNG output.

## Cover image pattern

1. Generate or choose one full-canvas illustration as the main visual.
2. Treat the illustration as the image, not as a module inside an infographic.
3. Compose title/UI overlay in HTML.
4. Place title above center and reserve bottom WeChat safety zone.
5. Screenshot final cover; do not rely on generated text.

## Infographic page pattern

1. Choose one main visual argument per page.
2. Use 3–6 modules only when there is enough space.
3. Prefer one strong chart plus supporting text over many weak charts.
4. Keep footer metadata quiet and consistent.
5. Run checklist after screenshot.

## Failure prevention

- If text clips, increase the SVG/module viewport or move the label below the chart.
- If a secondary frame collides with a divider/footer, move it or remove it.
- If Mermaid looks too large, split it into its own page.
- If generated illustration distracts from the chart, shrink it or move it into a frame.
