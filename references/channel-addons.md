# Channel Addons

Channel addons are optional overlays for delivery variants. They let `minimal-graph` stay focused on deterministic image generation while still supporting channel-specific prompt tweaks and post-render packaging.

## Placement

- Core skill: `SKILL.md`
- Shared contract: `references/channel-addons.md`
- Concrete channel modules: `references/channel-addons/<channel>.md`

## Contract

Each channel module should define these fields:

| Field | Required | Meaning |
|---|---|---|
| `channel` | yes | Stable channel identifier, used by the caller such as `xhs` or `wx-official-account`. |
| `aliases` | no | Search aliases or legacy names. |
| `intent` | yes | One-sentence description of the delivery surface. |
| `prompt_addon` | yes | Extra constraints appended after the core visual spec. |
| `output_variant` | yes | The derivative format, crop, packaging, or naming expectation created for this channel. |
| `posthook` | yes | Actions that run after the visual passes core checks. |
| `forbidden` | yes | Guardrails that stop channel logic from mutating the core skill. |

## Stacking model

1. Build the channel-neutral visual spec first.
2. Render or prepare the canonical source using the core skill rules.
3. Load one channel module.
4. Append the module's `prompt_addon` after the core requirements under a dedicated "channel overlay" section.
5. Resolve conflicts in favor of the core deterministic rules unless the caller explicitly requests a separate derivative variant.
6. After the rendered output passes clipping, overlap, and readability checks, run the module's `posthook`.

## What prompt addons may do

- Ask for a derivative crop ratio, safe area, or thumbnail emphasis.
- Change packaging language for filenames, folders, or manifest labels.
- Add channel-facing reminders that do not alter the validated core layout.

## What prompt addons may not do

- Replace the canonical typography, line system, or layout rules.
- Inject publishing copy, CTA text, or workflow steps into the core graphic by default.
- Force the agent to skip the base readability inspection.

## Posthook timing

Run the `posthook` only after:

1. The canonical output exists.
2. The output already passes the core checklist.
3. The addon is being applied to a named derivative variant.

## What posthooks may do

- Copy validated outputs into a channel-specific directory.
- Generate derivative exports, manifests, or delivery notes.
- Rename files or assemble a minimal delivery package around the approved image assets.

## What posthooks may not do

- Rewrite the canonical HTML / SVG / grammar source in place.
- Patch clipping, typography, or layout issues that should have been fixed in the core render.
- Trigger publishing, uploading, or external platform operations from inside the core skill.

## Initial modules

| Channel | File | Purpose |
|---|---|---|
| `xhs` | `references/channel-addons/xhs.md` | Feed-first derivative packaging for XiaoHongShu style distribution. |
| `wx-official-account` | `references/channel-addons/wx-official-account.md` | Article-cover derivative packaging for WeChat official-account style distribution. |

## Future expansion

Add new files under `references/channel-addons/` for channels such as:

- `x`
- `x-article`
- `medium`

The core skill should not change unless the addon seam itself changes.
