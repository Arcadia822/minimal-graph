# Minimal Graph RED Review

This review follows the local `writing-skills` guidance: capture failure pressure first, then tighten the core skill around reusable behavior instead of narrative residue.

## Current leakage to watch

- The canonical style and checklist already contain cover-oriented constraints and social-card residue, so future edits are likely to append more channel-specific rules into the core references.
- The original `SKILL.md` did not define where channel prompt tweaks or delivery hooks should live, which encourages agents to inline platform details into the core skill body.

## Pressure scenario 1: One request asks for both xhs and wx variants

**Prompt pressure**

> 用同一套内容，顺手出一版小红书首图和一版公众号头图，最好把后续交付步骤也一起做掉。

**Likely failure without a boundary**

- The agent hardcodes both channel constraints into the core layout rules.
- The core skill stops being a deterministic graphics skill and turns into a mixed publishing SOP.

**What the refactor must enforce**

- Core visual logic stays channel-agnostic.
- xhs / wx differences become optional addons with narrow overlays and posthooks.

## Pressure scenario 2: Diagram generation gets polluted by delivery concerns

**Prompt pressure**

> 先画流程图，再按某个平台要求补安全区、封面字数、导出目录和后处理。

**Likely failure without a boundary**

- Safety zones, export naming, and packaging rules leak into the source diagram spec.
- The agent edits the main SVG/HTML just to satisfy one channel's derivative output.

**What the refactor must enforce**

- The canonical source remains the channel-neutral visual.
- Channel logic runs after the core output exists and passes readability checks.

## Pressure scenario 3: New channels keep growing the main skill

**Prompt pressure**

> 之后再支持 x、x article、medium，先把这些预留写到主 skill 里吧。

**Likely failure without a boundary**

- The core skill accumulates platform-by-platform exceptions.
- Discovery quality drops because the skill looks like a platform handbook instead of a rendering reference.

**What the refactor must enforce**

- The core skill names only the addon seam.
- New channels are added as separate modules under `references/channel-addons/`, not as new inline sections in `SKILL.md`.
