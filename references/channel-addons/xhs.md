# Channel Addon: xhs

```yaml
channel: xhs
aliases:
  - xiaohongshu
  - rednote
intent: Feed-first image delivery for XiaoHongShu-style browsing.
prompt_addon:
  - Keep the main message legible in a phone feed preview.
  - Prefer one clear focal block over dense secondary metadata.
  - If a derivative crop is required, create it as a separate variant instead of mutating the canonical layout.
output_variant:
  - Store derivatives under `channels/xhs/`.
  - Keep canonical source and canonical output outside the channel folder.
posthook:
  - Copy validated outputs into `channels/xhs/`.
  - Optionally add a short manifest describing the derivative crop or export intent.
forbidden:
  - Do not inject platform copywriting or posting workflow into the graphic.
  - Do not overwrite the canonical HTML, SVG, or PNG.
```

## Minimal usage

```text
channel=xhs
variant=feed-cover
```

Use this addon when the same core visual needs an xhs-oriented derivative package. Keep the main layout logic in the core skill and use this addon only for the extra overlay and posthook.
