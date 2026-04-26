# Sources and Change Log

## Sources

- Iterative Feishu feedback, 2026-04-25/26: Cover constraints, social card card template, Maple font requirement, footer rules, Markdown Viewer rendering, generated illustration modes, clipping/collision corrections.
- `getsentry/skills/skills/skill-writer` at commit `a2366b1`: used for skill structure, progressive disclosure, description optimization, validation expectations.
- `intellectronica/agent-skills/skills/beautiful-mermaid` at commit `bb17b53`: informed Mermaid SVG rendering workflow and post-processing approach.
- `subframe7536/maple-font` release `v7.9`: MapleMono-CN font family selected as the default text font.
- Local guide `/Users/arcadia/.agents/skills/writing-skills/SKILL.md`: used to drive RED analysis, description cleanup, and the separation between core rendering rules and channel-specific addons.
- `anthropics/claude-code` README and `openai/codex` README: informed the rewritten README information architecture around value proposition, quick start, install paths, and progressive document routing.

## Authoring decisions

- Keep `SKILL.md` short and route task-specific detail to references.
- Consolidate appended v2–v9 rule history into current canonical rules.
- Avoid runtime dependence on another skill by describing Mermaid rendering intent and normalization rather than requiring a named skill invocation.
- Keep generated images as illustration assets only; preserve deterministic HTML text and layout.
- Keep channel prompt addons and posthooks out of the core skill; define them under `references/channel-addons/` and load them only for derivative variants.
