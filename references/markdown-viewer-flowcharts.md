# Markdown Viewer Flowchart Routing

Use Markdown Viewer diagram skills as the structure generator for flowcharts and related diagrams. The minimal editorial style remains the final visual authority.

## Routing

| Need | Prefer |
|---|---|
| Controlled article flow / product loop / business process | BPMN / PlantUML syntax |
| Software sequence / class / component / deployment | UML / PlantUML syntax |
| Dependency graph / call graph / package hierarchy | Graphviz DOT |
| Layered system architecture / pipeline layout | Architecture HTML templates |
| Cloud/security/data/IoT domain architecture | Domain-specific Markdown Viewer skill, then restyle |
| Simple editorial flow | Native HTML/SVG fallback when renderer style is hard to control |

## Minimal style override

Regardless of source diagram syntax:

- Use Maple for final visible text when rendered inside the requested signature visuals.
- Use pure white background.
- Use black text and one global 1px line tone.
- Remove or avoid semantic color palettes unless the user explicitly requests them.
- Avoid rounded corners where the renderer allows it.
- Prefer hollow/simple arrowheads.
- Keep labels inside safe bounds; no clipping.
- Do not embed implementation notes in the final graphic.

## Practical workflow

1. Use the Markdown Viewer skill to choose the right diagram grammar and draft the diagram structure.
2. Render/export or translate the structure into the the requested signature HTML page.
3. If renderer output is hard to restyle, use it as layout reference and redraw in HTML/SVG with the requested signature theme.
4. Screenshot the final the requested signature page and run `references/html-infographic-checklist.md`.

## Rule of thumb

Markdown Viewer skills define the diagram's logic. `minimal-graph` defines the finished visual style.
