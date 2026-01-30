# LaTeX Poster Template

A [Gemini](https://github.com/anishathalye/gemini)-based `beamerposter` template for 34.82" x 46.43" landscape research posters with CU Boulder Physics branding. Uses a clean, minimal style with thin separator lines and white/light backgrounds, well-suited for information-dense conference posters. See [poster.pdf](poster.pdf) for a rendered example.

## Prerequisites

You need a LaTeX distribution with LuaLaTeX support:

- **Overleaf** (recommended for beginners): No local install required. Upload the files and set the compiler to **LuaLaTeX** (Menu > Compiler).
- **TeX Live** (Linux/macOS): `sudo apt install texlive-full` or install from [tug.org/texlive](https://tug.org/texlive/). Includes `lualatex`.
- **MiKTeX** (Windows): Install from [miktex.org](https://miktex.org/). Includes `lualatex`.

### Font Requirements

Gemini uses the **Raleway** and **Lato** fonts via `fontspec`. These are available as system fonts or through TeX packages:

- **Overleaf**: Both fonts are pre-installed. No action needed.
- **TeX Live**: Install `texlive-fonts-extra` (includes both fonts as OpenType files).
- **MiKTeX**: The fonts will be installed automatically on first compile if "Install missing packages" is enabled.

## Overleaf Quickstart

1. Create a new blank project on [Overleaf](https://www.overleaf.com/).
2. Upload all `.sty` files, `poster.tex`, `references.bib`, and the contents of `assets/` (logos and example figure PDFs).
3. Set the compiler to **LuaLaTeX** (Menu > Compiler). This is required — pdfLaTeX will not work.
4. Click **Recompile**. The poster PDF appears in the preview pane.

## VS Code with LaTeX Workshop

VS Code provides a full LaTeX editing environment with live preview, syntax highlighting, and automatic compilation.

### Setup

1. Install a TeX distribution (TeX Live or MiKTeX — see Prerequisites above).
2. Install [Visual Studio Code](https://code.visualstudio.com/).
3. Install the **LaTeX Workshop** extension (search "LaTeX Workshop" by James Yu in the Extensions panel).

### Editing and Compiling

**Important**: Open the **project root folder** (`PHYS-Poster-Templates/`) as your VS Code workspace — not just the `latex/` subfolder. The build recipe in `.vscode/settings.json` only loads if VS Code opens the folder that contains `.vscode/`.

1. **File > Open Folder** and select the `PHYS-Poster-Templates/` directory.
2. LaTeX Workshop compiles automatically when you save. The output PDF appears in the built-in PDF viewer.
3. To manually trigger a build: **Ctrl+Alt+B** (or **Cmd+Option+B** on macOS), or open the Command Palette and run **LaTeX Workshop: Build LaTeX project**.
4. To open the PDF preview: **Ctrl+Alt+V** (or **Cmd+Option+V**), or click the magnifying glass icon in the top right of the editor.

### Build Configuration

The repo's `.vscode/settings.json` includes a `lualatex + bibtex` recipe for this template. LaTeX Workshop will use this recipe automatically when compiling files in the `latex/` directory.

If you're working outside this workspace, add this to your `.vscode/settings.json`:

```json
{
  "latex-workshop.latex.tools": [
    { "name": "lualatex", "command": "lualatex", "args": ["-synctex=1", "-interaction=nonstopmode", "%DOC%"] },
    { "name": "bibtex",   "command": "bibtex",   "args": ["%DOCFILE%"] }
  ],
  "latex-workshop.latex.recipes": [
    {
      "name": "lualatex + bibtex",
      "tools": ["lualatex", "bibtex", "lualatex", "lualatex"]
    }
  ]
}
```

## Command-Line Compilation

```bash
lualatex poster
bibtex poster
lualatex poster
lualatex poster
```

Run `lualatex` twice after `bibtex` to resolve all references and citations.

**Note**: You must use `lualatex` (or `xelatex`), not `pdflatex`. The Gemini theme uses `fontspec` for font loading, which requires a Unicode-aware TeX engine.

## Customization

All user-configurable settings are in the **Configuration** section at the top of `poster.tex`:

```latex
% Poster metadata
\title{Your Poster Title Goes Here}
\author{Author One \inst{1} \samelineand Author Two \inst{2}}
\institute[shortinst]{
  \inst{1} Department of Physics, University of Colorado Boulder \samelineand
  \inst{2} JILA, University of Colorado Boulder
}
```

### Logos

The title banner supports a logo on the left, right, or both sides. The `assets/` folder includes two options:

- `Boulder_left_lockup_rev_2025.png` — CU Boulder institutional logo
- `Physics_rev_left.png` — CU Physics department logo

You can use one or both, in either position. The template defaults to CU Boulder on the left and Physics on the right. To use only one logo, comment out the other line in the Configuration section of `poster.tex`:

```latex
\logoleft{\includegraphics[height=3.5cm]{../assets/Boulder_left_lockup_rev_2025.png}}
% \logoright{\includegraphics[height=3.5cm]{../assets/Physics_rev_left.png}}
```

Both provided logos are white/reversed and designed for dark backgrounds. Keep logos at their original aspect ratio. If your work is funded by a grant, you can replace one of the logos with a funding agency logo.

### Block Types

Gemini provides three visually distinct block types:

- `\begin{block}{Title}` — Standard block with gold separator line
- `\begin{alertblock}{Title}` — Gold-tinted background for key findings
- `\begin{exampleblock}{Title}` — Light gray background for supplementary info

### Subsection Headings

Use `\heading{Text}` inside a block to create a bold subsection heading without starting a new block.

### Changing the Number of Columns

The template defaults to 3 columns. To switch to 2 columns:

1. Change `\colwidth` to `0.45\textwidth`.
2. Move Column 3 content into Column 1 or 2.
3. Delete the Column 3 section (marked with `% === COLUMN 3 ===`).

### Changing Colors

To use the default Gemini color scheme instead of CU Boulder colors, change this line in `poster.tex`:

```latex
\usecolortheme{gemini}  % instead of \usecolortheme{cuboulder}
```

The CU Boulder colors are defined in `beamercolorthemecuboulder.sty` and can be adjusted there.

### Adding Figures

```latex
\begin{figure}
  \centering
  \includegraphics[width=\columnwidth]{your-figure.pdf}
  \caption{Description of the figure.}
  \label{fig:yourlabel}
\end{figure}
```

### Adding Equations

```latex
\begin{equation}
  E = mc^2
  \label{eq:einstein}
\end{equation}
```

Reference with `Eq.~\eqref{eq:einstein}`.

### Citations

Add entries to `references.bib` and cite with `\cite{key}`. The template uses a numeric citation style.

## Troubleshooting

### First-time MiKTeX setup

If this is a fresh MiKTeX installation you may see `lualatex: major issue: So far, you have not checked for MiKTeX updates` and compilation will refuse to start. Fix this before anything else:

1. Open **MiKTeX Console** (search for it in the Start menu).
2. When prompted, check for updates and install any that are available.

Alternatively, from the command line:

```bash
miktex packages check-update
miktex packages update
```

### "Fatal fontspec error: The font Raleway cannot be found"

The Gemini theme requires the **Raleway** and **Lato** font families. If either is missing, LuaLaTeX will fail with `metric data not found or bad` errors and every character will appear as `Missing character: There is no X in font nullfont!`.

**Overleaf**: Both fonts are pre-installed. No action needed.

**TeX Live** (Linux/macOS): Install `texlive-fonts-extra`, which includes both fonts as OpenType files.

**MiKTeX** (Windows): MiKTeX may not install these fonts automatically on a fresh install. Install them manually:

1. Open **MiKTeX Console** > **Packages**, search for `raleway` and `lato`, and install both. Or from the command line:

```bash
miktex packages install raleway
miktex packages install lato
```

2. If you prefer automatic installation for all future packages, open **MiKTeX Console** > **Settings** and set "Install missing packages" to **Always**.

### "! Fatal error occurred, no output PDF file produced" with pdflatex

You're using the wrong compiler. This template requires `lualatex` or `xelatex`, not `pdflatex`. In Overleaf, change the compiler under Menu > Compiler. In VS Code, make sure the `lualatex + bibtex` recipe is selected.

### "(pdf inclusion): reading image failed"

LuaLaTeX failed to include a PDF image. This can happen if a PDF file is corrupted or uses structures that LuaTeX's parser cannot handle. The example figures in `assets/` are provided as both SVG and PDF. If the PDF versions fail, regenerate them from the SVGs:

```bash
pip install svglib
python -c "
from svglib.svglib import svg2rlg
from reportlab.graphics import renderPDF
for name in ['example-diagram', 'example-plot']:
    drawing = svg2rlg(f'assets/{name}.svg')
    renderPDF.drawToFile(drawing, f'assets/{name}.pdf', fmt='PDF')
"
```

For your own figures, vector formats (PDF, SVG) are preferred. If a PDF figure fails to include, try re-exporting it from its source application, or convert it with a tool like Inkscape (`inkscape input.svg --export-filename=output.pdf`).

### "Empty bibliography" warning

This is normal if you haven't added any `\cite{key}` commands yet. Once you cite at least one reference, the bibliography will populate after a full build cycle.

### Build hangs or MiKTeX prompts for package installation

MiKTeX may try to install missing packages during compilation. Open **MiKTeX Console** > **Settings** and set "Install missing packages" to **Always**.

### "Cannot find LaTeX root file"

Make sure you have `poster.tex` open as the active editor tab when you trigger the build.

### "Script engine 'perl' not found" (latexmk error)

LaTeX Workshop uses `latexmk` to clean auxiliary files after a failed build. On MiKTeX, `latexmk` requires Perl, which is not installed by default on Windows.

This error does not affect compilation — it only appears when LaTeX Workshop tries to auto-clean after a build failure. The repo's `.vscode/settings.json` disables `latexmk`-based cleaning to avoid this issue. If you still see this error, make sure you opened the **project root** (`PHYS-Poster-Templates/`) as your VS Code workspace so the settings file loads.

If you want `latexmk` to work for other projects, install [Strawberry Perl](https://strawberryperl.com/) and restart VS Code.

## File Overview

| File | Purpose |
|------|---------|
| `poster.tex` | Main poster source — edit this |
| `references.bib` | BibTeX bibliography entries |
| `beamerthemegemini.sty` | Gemini main theme (layout, fonts, block templates) |
| `beamercolorthemegemini.sty` | Gemini default color theme (kept as fallback) |
| `beamercolorthemecuboulder.sty` | CU Boulder color theme for Gemini |
| `../assets/Boulder_left_lockup_rev_2025.png` | CU Boulder logo (header left) |
| `../assets/Physics_rev_left.png` | CU Physics department logo (header right) |
| `../assets/example-diagram.pdf` | Example experimental setup diagram |
| `../assets/example-plot.pdf` | Example scatter plot with theory curve |
