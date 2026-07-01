# PPT Screenshot to HTML

> 将 PPT 页面截图或参考图复刻为高保真、固定画布的静态 HTML。

这是一个 Codex skill。它把 HTML 当成“可编程的 PPT 画布”来使用：固定 `1600 x 900` 页面尺寸，使用母版/背景图承载固定元素，再用可编辑的 HTML/CSS/SVG 重建标题、正文、卡片、表格、流程图和图标。

[English](#english)

## 能做什么

- 将 PPT 页面截图复刻为自包含的静态 HTML 页面。
- 保持固定 `1600 x 900` PPT 画布。
- 使用提供的 base/master image 作为页面母版背景。
- 只重建页面专属内容，例如标题、正文、表格、卡片、图表和图标。
- 指导在浏览器中做视觉验证，并至少完成两轮修正。

## 不是什么

- 不是 PPTX 解析器。
- 不是 OCR 引擎。
- 不是一键自动转码工具。
- 不是 HTML 转 PPTX 工具。
- 不应该把目标截图直接嵌入为背景图来“伪复刻”。

## 仓库结构

```text
.
├── skill/
│   ├── SKILL.md
│   ├── agents/
│   │   └── openai.yaml
│   ├── assets/
│   │   └── slide-template.html
│   └── references/
│       └── high-fidelity-guide.md
├── examples/
│   └── README.md
├── CONTRIBUTING.md
├── PRIVACY.md
├── RELEASE_CHECKLIST.md
├── LICENSE
└── README.md
```

真正可安装的 Codex skill 是 `skill/` 目录。仓库根目录的 README、隐私说明、贡献指南和发布清单主要服务于开源维护。

## 快速开始

1. 将 `skill/` 目录复制到你的 Codex skills 目录中。
2. 如果需要，将目录重命名为 `ppt-screenshot-to-html`。
3. 准备目标 PPT 截图；如果有母版图，也一起提供。
4. 让 Codex 使用 `$ppt-screenshot-to-html` 复刻页面。
5. 在浏览器 100% 缩放下检查生成的 `index.html`。
6. 对照原截图进行修正，直到视觉匹配度可接受。

示例提示词：

```text
Use $ppt-screenshot-to-html to reproduce this PPT screenshot as a high-fidelity static HTML page using the provided base image.
```

## 输出约定

每一页建议放在独立目录中：

```text
page-name/
├── index.html
└── assets/
    └── slide-bg.png
```

HTML 页面应基于 `skill/assets/slide-template.html` 的结构：

```text
viewport > slide-frame > slide
```

内部画布必须保持为 `1600px x 900px`。

## 隐私和素材安全

不要提交真实客户 PPT、公司模板、保密截图、真实 logo、邮箱、姓名、内部链接、API key，或任何包含私有信息的生成结果。

示例素材必须使用完全虚构的品牌和内容。添加示例前请阅读 `PRIVACY.md`。

## 许可证

MIT License。详见 `LICENSE`。

---

## English

A Codex skill for reconstructing PowerPoint slide screenshots or reference images as high-fidelity, fixed-layout static HTML pages.

This project treats HTML as a programmable PPT canvas: a fixed `1600 x 900` slide, a reusable master/background image, and editable HTML/CSS/SVG content layers.

## What It Does

- Rebuilds PPT slide screenshots as self-contained static HTML.
- Preserves a `1600 x 900` slide canvas.
- Reuses a provided base/master image for fixed branding and layout elements.
- Reconstructs page-specific titles, text, cards, tables, diagrams, and icons as editable HTML/CSS/SVG.
- Guides visual verification in a browser with at least two correction rounds.

## What It Is Not

- Not a PPTX parser.
- Not an OCR engine.
- Not a one-click automatic slide converter.
- Not an HTML-to-PPTX exporter.
- Not intended to embed the target screenshot as a background.

## Quick Start

1. Copy the `skill/` directory into your Codex skills directory and rename it to `ppt-screenshot-to-html` if needed.
2. Provide a target PPT screenshot and, when available, a base/master image.
3. Ask Codex to use `$ppt-screenshot-to-html` to reconstruct the slide.
4. Review the generated `index.html` in a browser at 100% zoom.
5. Compare against the target screenshot and run correction rounds until the visual match is acceptable.

## Output Convention

Each generated page should be placed in its own folder:

```text
page-name/
├── index.html
└── assets/
    └── slide-bg.png
```

The HTML page should use the bundled `skill/assets/slide-template.html` structure:

```text
viewport > slide-frame > slide
```

The internal slide must remain exactly `1600px x 900px`.

## Privacy And Source Material

Do not commit real client slides, company templates, confidential screenshots, logos, email addresses, names, internal URLs, API keys, or generated outputs containing private information.

Use synthetic examples only. See `PRIVACY.md` before adding sample assets.
