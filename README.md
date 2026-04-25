# Minimal Graph

一个用于生成极简编辑视觉图的 Agent Skill。

适用场景：

- 微信公众号题图与正文配图
- 小红书多页卡片
- HTML / CSS / SVG 信息图
- Markdown Viewer 图表工作流
- 使用 Maple 字体的中文技术图、流程图、信息卡

这个 skill 沉淀自一次真实的公众号文章生产流程：从技术文章写作、配图、公众号草稿，到小红书复盘卡片。重点不是“做一张好看的图”，而是把图像生产变成可复用、可检查的流程。

## 预览

### 微信题图

![微信题图预览](assets/previews/wechat-cover.png)

### 微信正文信息图

![微信信息图预览](assets/previews/wechat-feedback-flow.png)

### 小红书三页卡片

| 封面 | 流程页 | Skills 页 |
|---|---|---|
| ![小红书封面](assets/previews/xhs-cover.png) | ![小红书流程页](assets/previews/xhs-workflow.png) | ![小红书 Skills 页](assets/previews/xhs-skills.png) |

## 这个 skill 解决什么问题

- 固定一套极简黑白编辑视觉规范。
- 强制使用 Maple font，避免中文图里字体混乱。
- 让微信公众号题图考虑裁切、安全区和白色标题叠加。
- 让小红书图先审文字分镜，再做图，再审图，最后发布。
- 规范 HTML/CSS/SVG 到 PNG 的工程流程。
- 规范 Markdown Viewer 到 SVG 再到 PNG 的图表流程。
- 避免公开图里暴露私有 skill、本地路径、草稿 ID 或凭证。

## 核心规则

### 微信题图

- 题图默认不放文章标题，标题由公众号标题字段承载。
- 禁止白色或浅色大面积遮罩，因为微信标题是白字。
- 题图必须考虑微信裁切安全区。
- 发布前必须生成裁切预览图。
- 题图可以放品牌、产品名或短关键词，但不能变成信息图。

### 微信正文信息图

- 手机可读优先。
- 少用小字、图例和密集说明。
- 标题不要挡副标题；如果拥挤，直接去掉副标题。
- 同一篇文章里的信息图必须风格统一。
- 中文文字用 HTML/CSS/SVG 叠加，避免让生图模型生成中文。

### 小红书卡片

默认流程：

1. 先发文字分镜给用户审。
2. 用户确认后再制图。
3. 图做好后通过消息附件发给用户审。
4. 用户确认后才发布。

默认三页结构：

1. 封面页：只放核心标题。
2. 流程页：讲阶段逻辑，不堆工具名。
3. Skills 页：只列公开来源和 GitHub 地址。

页脚规则：

- 封面页：保留页脚占位，但不显示作者和页码。
- 内容页：右下角显示 `Arcadia & Luna | 页码`。
- 左下角默认留空。

## 工程实现

### HTML/CSS/SVG → PNG

推荐流程：

1. 写一个固定尺寸的 HTML 页面。
2. 用 `@font-face` 加载 Maple 字体。
3. 所有文字、边框、图表都用 HTML/CSS/SVG 精确控制。
4. 用浏览器截图生成 PNG。
5. 对最终截图做检查，而不是只检查代码。

### Markdown Viewer → SVG → PNG

推荐流程：

1. 使用 Markdown Viewer 语法作为图表结构源，例如 Graphviz DOT、UML、BPMN、Vega。
2. 保存源文件，例如 `.dot`、`.puml`、`.mmd`。
3. 先渲染成 SVG。
4. 再用真实矢量渲染器转成 PNG。
5. 如果原生样式不符合极简规范，就把 SVG 当布局参考，用 HTML/SVG 重绘。

优先转换工具：

- `rsvg-convert`
- Chromium screenshot
- CairoSVG
- ImageMagick

## 文件结构

```text
minimal-graph/
├── SKILL.md
├── SOURCES.md
├── assets/
│   └── previews/
└── references/
    ├── editorial-minimal-style.md
    ├── html-infographic-checklist.md
    ├── markdown-viewer-flowcharts.md
    ├── mermaid-normalization.md
    ├── wechat-article-workflow.md
    └── xhs-card-template.md
```

## 安装

复制到你的 agent skills 目录：

```bash
cp -r minimal-graph ~/workspace/skills/
```

之后在需要制作微信题图、公众号信息图、小红书卡片或极简技术图时，让 agent 使用 `minimal-graph`。

## 许可证

MIT。来源和变更记录见 `SOURCES.md`。
