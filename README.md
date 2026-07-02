# PPT Screenshot to HTML

> 将 PPT 页面截图或参考图复刻为高保真、固定画布的静态 HTML。

这是一个 Codex skill。它把 HTML 当成“可编程的 PPT 画布”来使用：固定 `1600 x 900` 页面尺寸，使用母版/背景图承载固定元素，再用可编辑的 HTML/CSS/SVG 重建标题、正文、卡片、表格、流程图和图标。

[English](README.en.md)

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
├── README.en.md
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

Apache License 2.0。详见 `LICENSE`。
