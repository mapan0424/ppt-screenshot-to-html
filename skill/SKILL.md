---
name: ppt-screenshot-to-html
description: Convert PPT slide screenshots or reference images into high-fidelity, fixed-layout static HTML pages. Use when the user provides a PPT screenshot, slide image, shared base/master image, or a ZIP containing slide assets and asks to reproduce, restore, recreate, or batch-convert the visual into HTML. Preserve a 1600x900 PPT canvas, reuse the supplied base image, reconstruct only editable title/content layers, inline library-quality SVG icons, and verify the result visually in a browser.
---

# PPT Screenshot to HTML

Rebuild the supplied PPT screenshot as a self-contained static HTML slide. Treat HTML as a programmable PPT canvas, not as a responsive website.

## Inputs

Identify these inputs from the request and nearby project files:

- Target slide screenshot used only as visual reference.
- Shared base/master image containing fixed branding elements.
- Output directory or existing page series naming pattern.
- Any ZIP archive that may contain the base image or prior HTML pages.

If the user says the base is the same as previous pages, reuse that exact base asset. Ask only when no usable base can be found safely.

## Required Workflow

1. Inspect the target screenshot and base image at original resolution.
2. Separate master elements from page-specific content.
3. Read [references/high-fidelity-guide.md](references/high-fidelity-guide.md).
4. Inspect neighboring completed pages to inherit paths, colors, typography, and naming.
5. Create one output folder per page with `index.html` and `assets/slide-bg.png`.
6. Start from [assets/slide-template.html](assets/slide-template.html), then replace the example content.
7. Reconstruct the title and body with HTML, CSS, and inline SVG.
8. Open the page in a real browser at 100% zoom and capture a 1600x900 screenshot.
9. Compare screenshot and target, then complete at least two correction rounds.
10. Return the clickable absolute path to `index.html` and briefly state verification status.

## Non-Negotiable Rules

- Use a fixed internal canvas of exactly `1600px x 900px`.
- Use `viewport > slide-frame > slide` with layout-aware JavaScript scaling.
- Use the base image as `.slide` background at exactly `1600px 900px`.
- Never crop, stretch, redraw, or duplicate master elements.
- Never use the target screenshot as a background, hidden overlay, canvas texture, or embedded image.
- Reconstruct page-specific text and shapes as editable HTML/CSS.
- Keep the title on one line, to the right of the top-left colored dots, vertically centered to them.
- Do not add navigation, controls, buttons, marketing sections, or web-app styling.
- Keep all content inside the canvas and eliminate page scrollbars.
- Preserve the supplied wording exactly. Do not summarize or rewrite copy.
- Use the master orange palette unless the reference clearly requires another existing master color.
- Prefer mature icon-library geometry such as Lucide. Inline the selected SVG paths in HTML so the result works offline.
- Do not improvise crude SVG icons when an established icon exists.

## Reconstruction Strategy

Classify the page before coding:

- Card page: absolute-positioned card group with consistent internal spacing.
- Table page: semantic `table` or CSS Grid with explicit tracks and row heights.
- Process page: numbered nodes, connectors, and step cards positioned on the 1600x900 grid.
- Comparison page: structured rows with one visually emphasized column.
- Summary page: feature cards, metric strip, and closing statement.

Use absolute positioning for the main composition. Use Flexbox or Grid only inside local groups where it improves alignment without changing measured geometry.

## Visual Verification

Check each round for:

- full base visibility and no duplicated branding;
- title/dot alignment and no title wrapping;
- matching content bounds, proportions, and visual center;
- matching font size, weight, line height, and line breaks;
- matching card borders, corner radius, fills, and spacing;
- consistent orange line icons with correct optical size;
- no clipping, scrollbars, or browser-zoom dependency.

In round one, correct large geometry. In round two, correct typography, spacing, borders, icon scale, and opacity. Continue when the discrepancy remains obvious.

## Output

Keep the final response concise. Link the generated `index.html`; do not paste analysis unless the user explicitly asks for it.
