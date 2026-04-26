# Channel Addon: wx-official-account

```yaml
channel: wx-official-account
aliases:
  - wx
  - wechat-official-account
intent: Article-cover or article-asset delivery for WeChat official-account style distribution.
prompt_addon:
  - Preserve a stable headline focus area for article-cover style reuse.
  - Keep derivative metadata minimal so the image still reads as a clean visual asset.
  - If channel packaging needs a different aspect ratio, export a dedicated variant instead of modifying the canonical source.
output_variant:
  - Store derivatives under `channels/wx-official-account/`.
  - Keep channel manifests or file naming guidance next to the derivative export only.
posthook:
  - Copy validated outputs into `channels/wx-official-account/`.
  - Optionally emit a delivery manifest for article-cover selection or packaging.
forbidden:
  - Do not turn the core skill into a WeChat publishing checklist.
  - Do not patch layout issues in posthook; fix them in the canonical render first.
```

## Minimal usage

```text
channel=wx-official-account
variant=article-cover
```

Use this addon when a validated core visual needs a wx-oriented derivative package. The addon may constrain packaging, but the core rendering rules still decide typography, structure, readability, and source organization.
