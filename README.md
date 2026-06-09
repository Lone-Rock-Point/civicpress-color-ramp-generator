# CivicPress Token Generator

A single-file browser tool for building and exporting a complete design token system — colors, typography, and utility tokens — tailored for use with WordPress theme.json (version 3). No build step or server required: open `colorGenerator.html` in any modern browser and start designing.

[![Launch Token Generator](https://img.shields.io/badge/Launch%20Token%20Generator-0050d8?style=for-the-badge)](https://lone-rock-point.github.io/civicpress-color-ramp-generator/colorGenerator.html)

## Shareable URLs

Every change you make — color choices, typography settings, utility token assignments — is automatically saved to the URL hash. Copy the URL at any time to share your exact configuration with a teammate or bookmark it for later. Loading the URL restores the full state instantly.

## Color

The Color tab lets you build a complete multi-scale color system grounded in the [USWDS (U.S. Web Design System)](https://designsystem.digital.gov/) token palette.

### Color ramps

- **Primary, Secondary, Tertiary** — Each section has a USWDS/Custom mode selector. In USWDS mode, choose any USWDS color family (e.g. "Blue vivid", "Red vivid", "Mint cool") and the tool generates a 7-step ramp at the standard scale steps. The **CivicPress Default** option loads the exact token values used in the CivicPress theme. In Custom mode, a "Generate Ramp" option builds a ramp from a seed hex using smart anchor placement, or you can set each swatch manually.
- **Extended Colors** — Up to 3 additional 5-step palettes. Each can be sourced from a USWDS family, a hue-shifted version of one of the main colors, or a custom hex. Defaults to Yellow vivid, Magenta, and Violet per the CivicPress theme.
- **Semantic Colors** — Background, Foreground, and Reverse colors sourced from the gray scale (or custom), plus four fixed translucent overlay values.
- **Base Grays** — A 7-step gray ramp mapped to the `base-minus-3` through `base-plus-3` WordPress palette slugs.

### Per-swatch controls

- **USWDS mode** — each swatch shows a step-select dropdown listing every token in that color family (e.g. `blue-10`, `blue-warm-60v`). Changing the step updates the swatch immediately.
- **Custom mode** — each swatch shows a hex/rgba input. Supports 6-digit hex, 8-digit hex with alpha, and `rgba()` values. Invalid input shows an error state and reverts on blur.
- **WCAG contrast badges** — each swatch automatically shows AA or AAA badges based on contrast ratios against the active semantic colors. Updates live when semantic colors change.
- **Brand color markers** — toggle a star on any swatch to mark it as a brand anchor color. Marked swatches are flagged in SVG exports.
- **Reset buttons** — every section has a Reset button that restores CivicPress Default values. A global Reset All button in the header restores the entire system.

### Dark mode

The Dark Mode toggle inverts the semantic Background/Foreground defaults and reverses the gray scale slug mapping (`base-plus-3` becomes the lightest value, `base-minus-3` the darkest). The page theme, swatch labels, buttons, and shadows all update accordingly.

## Typography

The Typography tab lets you define font roles and a fluid type scale, then preview how they render together.

### Font roles

Assign a Google Font (or any web font) and weight to each of four roles: **Body**, **Heading**, **Subheading**, and **Interactive**. Fonts are loaded live from Google Fonts as you type. Each role card also has a color picker so you can assign a semantic or palette color to headings, body text, links, and interactive elements.

### Fluid type scale

Define named size steps (e.g. `small`, `normal`, `large`, `xx-large`) with a minimum and maximum pixel size. The tool generates a CSS `clamp()` formula for each step and previews the rendered size at an adjustable viewport width (default 1400px, range 320–1400px).

### Typography preview

A live preview renders H1–H6 headings, a lede paragraph, and body text with an inline link — all using your chosen fonts, weights, sizes, and colors. The preview updates instantly as you adjust any setting.

## Utilities

The Utilities tab lets you map semantic UI colors to specific palette values, then preview them in context.

### Interactive colors

Assign colors for button states across two button variants: filled (interactive) and reverse (for use on dark/colored backgrounds). Each variant has Default, Hover, Active, and Outline Background states.

### UI borders

Set colors for general UI borders and table-specific borders.

### Table colors

Assign colors for the table header background, striped row background, and the foreground text color used throughout tables.

### Live preview

A live mockup renders buttons (filled and outline, in both interactive and reverse variants), a form input field, and a data table — all using your chosen utility colors. The preview updates immediately when you change any assignment.

## Exports

All three tabs can be exported individually or together. The export modal lets you select which sections to include.

- **Export theme.json** — exports a WordPress version 3 theme.json. Color palette entries go in `settings.color.palette`; utility/semantic token references go in `settings.custom.color` as `var(--wp--preset--color--)` references. Typography roles go in `settings.custom` and fluid size steps go in `settings.custom.typography`. The `styles` block wires body typography to the correct custom property references.
- **Export SVG** — exports visual reference sheets. The color sheet shows all palette swatches with token names, hex values, and contrast badges. The typography sheet shows a full type preview (H1–H6, lede, paragraph) and a type scale specimen at 1400px. The utilities sheet shows rendered mockups of buttons, a form input, and a table.
- **Export CSS Variables** — exports a `:root {}` block with all values as CSS custom properties, using the same naming convention as the WordPress palette slugs.

## Usage

Open `colorGenerator.html` in any modern browser — no install, no build step, no server required.
