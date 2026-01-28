# MARP Poster Template

A Markdown-based poster template using [MARP](https://marp.app/) (Markdown Presentation Ecosystem) with CU Boulder Physics branding.

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

**Important**: Open the **project root folder** (`poster/`) as your VS Code workspace — not just the `marp/` subfolder. The settings in `.vscode/settings.json` only load if VS Code opens the folder that contains `.vscode/`.

4. **File > Open Folder** and select the `poster/` directory. Then open `marp/poster.md` and click the preview icon.

### Option B: Marp CLI

```bash
npm install -g @marp-team/marp-cli
```

Requires [Node.js](https://nodejs.org/) (v16 or later).

## Preview

In VS Code with the Marp extension, open `poster.md` and use **Ctrl+Shift+V** (or **Cmd+Shift+V** on macOS) to open the Markdown preview. The Marp extension renders the poster with the custom theme.

Make sure you have the `.vscode/settings.json` configured as described in the Installation section above (theme registration and HTML enabled).

## Export to PDF

Using Marp CLI:

```bash
marp --html --allow-local-files marp/poster.md -o poster.pdf
```

- `--html` is **required** for the multi-column `<div>` layout to render.
- `--allow-local-files` is **required** to load the local CSS theme and logo image.

Using VS Code: Open the Command Palette > **Marp: Export Slide Deck** > choose PDF.

## Customization

### Quick Configuration

Edit the poster content directly in `poster.md`:

- **Title, authors, affiliations**: Edit the HTML text inside the `<div class="poster-header">` block near the top of the file.
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

The template uses CSS grid with `<div class="columns-3">` for three columns. Switch to `<div class="columns-2">` for a two-column layout. The CSS classes are defined in the theme.

## Troubleshooting

### No styling in preview (no black header, no columns, plain text)

The custom theme isn't loading. Check:

1. You opened the **project root** (`poster/`) as your VS Code workspace, not the `marp/` subfolder. The `.vscode/settings.json` must be in the workspace root.
2. The `.vscode/settings.json` file contains both `"markdown.marp.themes"` and `"markdown.marp.enableHtml": true`.
3. Try closing and reopening VS Code after changing settings — theme registration sometimes requires a restart.

### HTML tags showing as literal text (e.g., `<div class="poster-header">` visible)

HTML rendering is not enabled. Make sure `"markdown.marp.enableHtml": true` is set in `.vscode/settings.json`. For CLI export, the `--html` flag is required.

### Poster looks like a small slide, not a large poster

The custom page size (`poster`) is defined in `cu-physics-poster.css`. If the theme isn't loaded (see first issue above), MARP falls back to its default 16:9 slide size. Fix the theme loading and the poster dimensions will apply.

## File Overview

| File | Purpose |
|------|---------|
| `poster.md` | Poster content — edit this |
| `cu-physics-poster.css` | Custom CSS theme for poster layout |
| `../assets/Physics_rev_left.png` | CU Physics department logo |
