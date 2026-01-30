# MARP Poster Template

A Markdown-based poster template using [MARP](https://marp.app/) (Markdown Presentation Ecosystem) with CU Boulder branding. See [poster.pdf](poster.pdf) for a rendered example, and the [Poster Design Best Practices](../best-practices.md) guide for layout, typography, and image guidelines.

## What is MARP?

MARP converts Markdown files into presentations (or, in this case, a poster) rendered as HTML, PDF, or PPTX. You write content in Markdown with a few HTML `<div>` tags for layout, and MARP handles the rest.

## Installation

### Option A: VS Code Extension (Recommended)

1. Install [Visual Studio Code](https://code.visualstudio.com/).
2. Install the **Marp for VS Code** extension (search "Marp" in the Extensions panel).
3. **Required**: Add the following to your workspace `.vscode/settings.json` (create the file if it doesn't exist):

```json
{
  "markdown.marp.themes": [
    "./marp/cu-physics-poster.css"
  ],
  "markdown.marp.enableHtml": true
}
```

`themes` registers the custom poster CSS so MARP can find it. `enableHtml` allows the `<div>` column layout to render in the preview.

**Important**: Open the **project root folder** (`PHYS-Poster-Templates/`) as your VS Code workspace — not just the `marp/` subfolder. The settings in `.vscode/settings.json` only load if VS Code opens the folder that contains `.vscode/`.

4. **File > Open Folder** and select the `PHYS-Poster-Templates/` directory. Then open `marp/poster.md` and click the preview icon.

### Option B: Marp CLI

```bash
npm install -g @marp-team/marp-cli
```

Requires [Node.js](https://nodejs.org/) (v16 or later).

## Preview

In VS Code with the Marp extension, open `poster.md` and use **Ctrl+Shift+V** (or **Cmd+Shift+V** on macOS) to open the Markdown preview. The Marp extension renders the poster with the custom theme.

Make sure you have the `.vscode/settings.json` configured as described in the Installation section above (theme registration and HTML enabled).

## Export

### PDF

Using VS Code: With `poster.md` open, click the **Marp icon** (double triangle) in the top-right corner of the editor toolbar, then select **Export Slide Deck** and choose PDF.

Using Marp CLI:

```bash
marp --html --allow-local-files marp/poster.md -o poster.pdf
```

- `--html` is **required** for the multi-column `<div>` layout to render.
- `--allow-local-files` is **required** to load the local CSS theme and logo image.

### Powerpoint (experimental)

Marp can also export to an editable PowerPoint file. This is experimental and requires:

1. [LibreOffice](https://www.libreoffice.org/) installed on your system.
2. In VS Code, enable the setting: **Marp > PPTX > Editable** (or add `"markdown.marp.pptx.editable": true` to your `settings.json`).

Using VS Code: Click the **Marp icon** > **Export Slide Deck** > choose PPTX.

Using Marp CLI:

```bash
marp --html --allow-local-files marp/poster.md -o poster.pptx
```

Note that PPTX export may not preserve all CSS styling perfectly. Use PDF for final print output.

## Customization

### Quick Configuration

Edit the poster content directly in `poster.md`:

- **Title**: Edit the `<h1>` inside `<div class="header-title-row">`.
- **Authors and affiliations**: Edit the `<div class="author-block">` section. Use `<sup>` tags for numbered affiliations.
- **Logos**: The title banner supports a logo on the left, right, or both sides. The `assets/` folder includes two options:
  - `Boulder_left_lockup_rev_2025.png` — CU Boulder institutional logo
  - `Physics_rev_left.png` — CU Physics department logo

  The template defaults to CU Boulder on the left (`.logo-left`) and Physics on the right (`.logo-right`). You can use one or both, in either position — replace the `src` paths to swap logos, or delete one of the `<img>` tags to use only one. Both provided logos are white/reversed and designed for dark backgrounds. If your work is funded by a grant, you can replace one with a funding agency logo.
- **Footer**: Edit the three `<span>` elements inside `<div class="poster-footer">` (email, conference, URL).
- **Colors**: Override CSS variables in the `<style>` block at the top of `poster.md`:

```html
<style>
:root {
  --cu-gold: #CFB87C;
  --cu-black: #000000;
  /* See cu-physics-poster.css for all available variables */
}
</style>
```

### Theme Colors

Color variables are defined in `cu-physics-poster.css`. Override them in the `<style>` block in `poster.md`, or edit the CSS file directly.

### Column Layout

The template uses CSS grid for column layouts. Three options:

**Three columns** (default):
```html
<div class="columns-3">
  <div class="column">...</div>
  <div class="column">...</div>
  <div class="column">...</div>
</div>
```

**Two columns** — change `columns-3` to `columns-2` and use two `column` divs:
```html
<div class="columns-2">
  <div class="column">...</div>
  <div class="column">...</div>
</div>
```

**Full-width span** — use `class="full-span"` on any element inside a column grid to make it stretch across all columns (useful for a wide figure or a shared section):
```html
<div class="columns-3">
  <div class="column">...</div>
  <div class="column">...</div>
  <div class="column">...</div>
  <div class="full-span">
    <p>This content spans all three columns.</p>
  </div>
</div>
```

**Mixed layouts** — stack multiple grid sections vertically inside `<div class="content">` to combine different column counts. For example, a two-column section on top and a three-column section below:
```html
<div class="content">
  <div class="columns-2">
    <div class="column">...</div>
    <div class="column">...</div>
  </div>
  <div class="columns-3">
    <div class="column">...</div>
    <div class="column">...</div>
    <div class="column">...</div>
  </div>
</div>
```

### Units and Dimensions

The CSS uses **inches** for structural/layout dimensions and **pixels** for fine details (borders, font sizes). Marp renders via Chromium at a fixed 96 DPI, so `1in = 96px` exactly. Key layout variables in `:root`:

| Variable | Default | Description |
|----------|---------|-------------|
| `--header-height` | `4in` | Height of the black header bar |
| `--footer-height` | `1in` | Height of the footer bar |
| `--content-padding` | `0.75in` | Padding around the content area |

## Troubleshooting

### No styling in preview (no black header, no columns, plain text)

The custom theme isn't loading. Check:

1. You opened the **project root** (`PHYS-Poster-Templates/`) as your VS Code workspace, not the `marp/` subfolder. The `.vscode/settings.json` must be in the workspace root.
2. The `.vscode/settings.json` file contains both `"markdown.marp.themes"` and `"markdown.marp.enableHtml": true`.
3. Try closing and reopening VS Code after changing settings — theme registration sometimes requires a restart.

### HTML tags showing as literal text (e.g., `<div class="poster-header">` visible)

HTML rendering is not enabled. Make sure `"markdown.marp.enableHtml": true` is set in `.vscode/settings.json`. For CLI export, the `--html` flag is required.

### Poster looks like a small slide, not a large poster

The custom page size (`poster`) is defined in `cu-physics-poster.css`. If the theme isn't loaded (see first issue above), MARP falls back to its default 16:9 slide size. Fix the theme loading and the poster dimensions will apply.

## Equations

The template uses MathJax (Marp's default) for math rendering. Use standard LaTeX math syntax:

- **Inline math**: `$E = mc^2$`
- **Display math**: `$$E = mc^2$$`

### Numbered Equations

Use `\tag{n}` inside a display math block to number an equation:

```markdown
$$E^2 = (pc)^2 + (m_0 c^2)^2 \tag{1}$$
```

Reference it in text as `Eq. (1)`. Note that automatic cross-referencing (`\label`/`\eqref`) is not supported in Marp's MathJax integration, so equation numbers and references must be managed manually.

## File Overview

| File | Purpose |
|------|---------|
| `poster.md` | Full example poster — edit this |
| `poster-skeleton.md` | Minimal skeleton with empty columns (also used for PPTX export) |
| `cu-physics-poster.css` | Custom CSS theme for poster layout |
| `../assets/Boulder_left_lockup_rev_2025.png` | CU Boulder logo (header left) |
| `../assets/Physics_rev_left.png` | CU Physics department logo (header right) |
| `../assets/example-plot.svg` | Example scatter plot figure |
| `../assets/example-diagram.svg` | Example experimental setup diagram |
