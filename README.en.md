# PPT Screenshot to HTML

> Reconstruct PowerPoint slide screenshots or reference images as high-fidelity, fixed-layout static HTML.

[中文](README.md)

This is a Codex skill. It treats HTML as a programmable PPT canvas: a fixed `1600 x 900` slide, a reusable master/background image, and editable HTML/CSS/SVG content layers.

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

## Repository Layout

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

The installable Codex skill is the `skill/` directory. Repository-level files are for open-source users and contributors.

## Quick Start

1. Copy the `skill/` directory into your Codex skills directory and rename it to `ppt-screenshot-to-html` if needed.
2. Provide a target PPT screenshot and, when available, a base/master image.
3. Ask Codex to use `$ppt-screenshot-to-html` to reconstruct the slide.
4. Review the generated `index.html` in a browser at 100% zoom.
5. Compare against the target screenshot and run correction rounds until the visual match is acceptable.

Example prompt:

```text
Use $ppt-screenshot-to-html to reproduce this PPT screenshot as a high-fidelity static HTML page using the provided base image.
```

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

## License

Apache License 2.0. See `LICENSE`.
