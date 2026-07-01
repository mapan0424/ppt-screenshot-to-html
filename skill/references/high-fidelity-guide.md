# High-Fidelity Reconstruction Guide

## Coordinate System

Use the target screenshot as a measurement plane. Convert coordinates proportionally when its native size differs from 1600x900:

```text
x_html = x_image * 1600 / image_width
y_html = y_image * 900 / image_height
```

Measure major regions first: title baseline, content top, content left/right bounds, card or table dimensions, and footer exclusion zone. Then measure internal padding and typography.

## Master and Content Separation

The base/master image commonly contains:

- logo;
- top-left colored dots;
- top-right slogan and underline;
- bottom copyright and color strip;
- fixed pale background or decoration.

Do not reproduce these in HTML. The target screenshot is reference-only. Reconstruct only page-specific title, subtitle, body text, cards, tables, diagrams, and icons.

## Title Anchor

Treat the colored dots as the global anchor. A typical title starts near `left: 105px; top: 68px`. Adjust based on the actual base image, not habit.

Keep:

- title left edge close to the dots without overlap;
- title optical vertical center aligned to the complete dot group;
- `white-space: nowrap`;
- enough right clearance from the master slogan.

Reduce font size for long titles instead of moving the title downward or wrapping it.

## Typography

Prefer installed Chinese UI fonts in this order:

```css
font-family: "Microsoft YaHei", "PingFang SC", "Noto Sans CJK SC",
  "Source Han Sans SC", Arial, sans-serif;
```

Match line breaks deliberately with fixed widths or `<br>` only when the screenshot uses them. Avoid browser-dependent auto wrapping for dense PPT copy.

Typical ranges:

- title: 39-52px, weight 700-800;
- subtitle: 22-26px, weight 400;
- card heading: 24-32px, weight 700-800;
- body: 17-24px, weight 400;
- table text: 18-25px depending on density.

## Color and Shape Defaults

Use these as starting points, then sample the actual page visually:

```css
:root {
  --primary-orange: #f05a1a;
  --hot-orange: #ff5a10;
  --deep-orange: #f03b12;
  --text-main: #080c12;
  --text-body: #2b2e35;
  --text-sub: #4d5157;
  --border-orange: rgba(240, 90, 26, 0.36);
  --border-soft: rgba(166, 170, 178, 0.44);
  --dash: rgba(190, 190, 190, 0.6);
}
```

Keep business-PPT styling restrained. Use light borders, small radii, subtle fills, and little or no shadow. Avoid generic web cards and decorative gradients unless clearly present in the reference.

## Icons

Use recognizable paths from an established line-icon library. Place symbols once and reuse them:

```html
<svg class="icon-sprite" aria-hidden="true">
  <symbol id="icon-shield-check" viewBox="0 0 24 24">
    <path d="M20 13c0 5-3.5 7.5-7.66 8.95a1 1 0 0 1-.67 0C7.5 20.5 4 18 4 13V6a1 1 0 0 1 1-1c2 0 4.5-1.2 6.24-2.72a1.17 1.17 0 0 1 1.52 0C14.51 3.81 17 5 19 5a1 1 0 0 1 1 1z" />
    <path d="m9 12 2 2 4-4" />
  </symbol>
</svg>
```

Render with `<use href="#icon-shield-check">`. Standardize `fill: none`, round caps/joins, and `stroke-width` near 2. Use `currentColor` for orange inheritance.

## Browser Fit

The outer frame must participate in layout. Do not center a transformed 1600px slide directly in the viewport; that often creates overflow at 100% browser zoom.

The frame determines the displayed 16:9 footprint, and JavaScript scales the internal slide from its top-left origin.

## Correction Order

Correct discrepancies in this order:

1. Canvas and base image.
2. Title anchor and main content bounding box.
3. Column/row/card geometry.
4. Font size, weight, line breaks, and line height.
5. Icons, borders, fills, separators, and subtle opacity.

Do not polish small icon details while the overall composition is still misaligned.
