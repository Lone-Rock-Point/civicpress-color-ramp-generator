# CivicPress Color Ramp Generator

A single-file browser tool for building and exporting a complete color system based on the [USWDS (U.S. Web Design System)](https://designsystem.digital.gov/) color token scale, tailored for use with WordPress theme.json (version 3).

## What it does

The generator lets you pick color families from the full USWDS token palette and automatically builds 7-step ramps for your primary, secondary, and tertiary brand colors, plus 5-step extended palettes and semantic/gray scales. Every color choice is reflected live on the page itself — backgrounds, text, buttons, borders, and shadows all update as you work.

### Color sections

- **Primary, Secondary, Tertiary Colors** — Each section has a USWDS/Custom mode selector. In USWDS mode, choose any USWDS color family (e.g. "Blue vivid", "Red vivid", "Mint cool") and the tool generates a 7-step ramp at the standard scale steps. The **CivicPress Default** option loads the exact token values used in the CivicPress theme.json. In Custom mode, a "Generate Ramp" option builds a ramp from a seed hex using smart anchor placement, or you can set each swatch manually.
- **Extended Colors** — Up to 3 additional 5-step palettes. Each can be sourced from a USWDS family, a hue-shifted version of one of the main colors, or a custom hex. Defaults to Yellow vivid, Magenta, and Violet per the CivicPress theme.
- **Semantic Colors** — Background, Foreground, and Reverse colors sourced from the gray scale (or custom), plus four fixed translucent overlay values.
- **Base Grays** — A 7-step gray ramp mapped to the `base-minus-3` through `base-plus-3` WordPress palette slugs.

### Per-swatch controls

- **USWDS mode** — each swatch shows a step-select dropdown listing every token in that color family (e.g. `blue-10`, `blue-warm-60v`). Changing the step updates the swatch immediately.
- **Custom mode** — each swatch shows a hex/rgba input. Supports 6-digit hex, 8-digit hex with alpha, and `rgba()` values. Invalid input shows an error state and reverts on blur.
- **WCAG contrast badges** — each swatch automatically shows AA or AAA badges (colored in the current Foreground or Background color) based on contrast ratios against the active semantic colors. Updates live when semantic colors change.
- **Reset buttons** — every section has a Reset button that restores its CivicPress Default values. A global Reset All button in the header restores the entire system.

### Dark mode

The Dark Mode checkbox inverts the semantic Background/Foreground defaults and reverses the gray scale slug mapping (`base-plus-3` becomes the lightest value, `base-minus-3` the darkest). The page theme, swatch label backgrounds, and shadows all update accordingly.

## Exports

- **Export theme.json** — exports a WordPress version 3 theme.json containing the full color palette. USWDS colors are referenced as `var(--token--color--blue-10)` style token variables; custom colors use their hex value. Respects dark mode gray slug reversal.
- **Export SVG** — exports a visual color sheet matching the current page appearance: page and section background colors, swatch name and value labels (token name or hex), and AA/AAA contrast badges.
- **Export CSS Variables** — exports a `:root {}` block with all palette values as CSS custom properties, using the same naming convention as the WordPress palette slugs.

## Usage

Open `colorGenerator.html` in any modern browser — no build step or server required.
