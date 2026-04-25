# Sources and Change Log

## Sources

- Iterative Feishu feedback, 2026-04-25/26: WeChat cover constraints, Xiaohongshu card template, Maple font requirement, footer rules, Markdown Viewer rendering, generated illustration modes, clipping/collision corrections.
- `getsentry/skills/skills/skill-writer` at commit `a2366b1`: used for skill structure, progressive disclosure, description optimization, validation expectations.
- `intellectronica/agent-skills/skills/beautiful-mermaid` at commit `bb17b53`: informed Mermaid SVG rendering workflow and post-processing approach.
- `subframe7536/maple-font` release `v7.9`: MapleMono-CN font family selected as the default text font.

## Authoring decisions

- Keep `SKILL.md` short and route task-specific detail to references.
- Consolidate appended v2–v9 rule history into current canonical rules.
- Avoid runtime dependence on another skill by describing Mermaid rendering intent and normalization rather than requiring a named skill invocation.
- Keep generated images as illustration assets only; preserve deterministic HTML text and layout.
