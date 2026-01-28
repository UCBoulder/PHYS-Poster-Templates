# LaTeX Poster Template

A `beamerposter` template for 35.61" x 47.48" landscape research posters with CU Boulder Physics branding. This size fits the department's HP DesignJet Z6dr (36" roll) without scaling.

## Prerequisites

You need a LaTeX distribution with the `beamerposter` package:

- **Overleaf** (recommended for beginners): No local install required. Upload the files and compile in the browser.
- **TeX Live** (Linux/macOS): `sudo apt install texlive-full` or install from [tug.org/texlive](https://tug.org/texlive/)
- **MiKTeX** (Windows): Install from [miktex.org](https://miktex.org/)

## Overleaf Quickstart

1. Create a new blank project on [Overleaf](https://www.overleaf.com/).
2. Upload `poster.tex`, `references.bib`, and the logo from `assets/Physics_rev_left.png`.
3. Set the compiler to **pdfLaTeX** (Menu > Compiler).
4. Click **Recompile**. The poster PDF appears in the preview pane.

## VS Code with LaTeX Workshop

VS Code provides a full LaTeX editing environment with live preview, syntax highlighting, and automatic compilation.

### Setup

1. Install a TeX distribution (TeX Live or MiKTeX — see Prerequisites above).
2. Install [Visual Studio Code](https://code.visualstudio.com/).
3. Install the **LaTeX Workshop** extension (search "LaTeX Workshop" by James Yu in the Extensions panel).

### Editing and Compiling

**Important**: Open the **project root folder** (`poster/`) as your VS Code workspace — not just the `latex/` subfolder. The build recipe in `.vscode/settings.json` only loads if VS Code opens the folder that contains `.vscode/`.

1. **File > Open Folder** and select the `poster/` directory.
2. LaTeX Workshop compiles automatically when you save. The output PDF appears in the built-in PDF viewer.
3. To manually trigger a build: **Ctrl+Alt+B** (or **Cmd+Option+B** on macOS), or open the Command Palette and run **LaTeX Workshop: Build LaTeX project**.
4. To open the PDF preview: **Ctrl+Alt+V** (or **Cmd+Option+V**), or click the magnifying glass icon in the top right of the editor.

### Build Configuration

LaTeX Workshop's default recipe uses `latexmk`, which requires Perl. **MiKTeX on Windows does not include Perl**, so the repo's `.vscode/settings.json` configures a direct `pdflatex + bibtex` recipe instead. If you open this project as your VS Code workspace, the build should work automatically.

If you're working outside this workspace and need to set it up manually, add this to your `.vscode/settings.json`:

```json
{
  "latex-workshop.latex.tools": [
    { "name": "pdflatex", "command": "pdflatex", "args": ["-synctex=1", "-interaction=nonstopmode", "%DOC%"] },
    { "name": "bibtex",   "command": "bibtex",   "args": ["%DOCFILE%"] }
  ],
  "latex-workshop.latex.recipes": [
    {
      "name": "pdflatex + bibtex",
      "tools": ["pdflatex", "bibtex", "pdflatex", "pdflatex"]
    }
  ]
}
```

### Useful Features

- **SyncTeX**: Ctrl+click in the PDF to jump to the corresponding source line (and vice versa).
- **Autocomplete**: Type `\cite{` or `\ref{` to get suggestions from your `.bib` file and labels.
- **Error highlighting**: Compilation errors and warnings appear inline in the editor and in the Problems panel.
- **Snippet shortcuts**: Type `BEQ` + Tab to insert an equation environment, `BFI` + Tab for a figure, etc.

## Command-Line Compilation

```bash
pdflatex poster
bibtex poster
pdflatex poster
pdflatex poster
```

Run `pdflatex` twice after `bibtex` to resolve all references and citations.

## Customization

All user-configurable settings are in the **Configuration** section at the top of `poster.tex`:

```latex
% === CONFIGURATION ===
\newcommand{\postertitle}{Your Poster Title Here}
\newcommand{\posterauthor}{Author One, Author Two, Author Three}
\newcommand{\posteraffiliation}{Department of Physics, University of Colorado Boulder}
\newcommand{\posteremail}{author@colorado.edu}

% Column width: use 0.31\textwidth for 3 columns, 0.47\textwidth for 2 columns
\newlength{\colwidth}
\setlength{\colwidth}{0.31\textwidth}
```

### Changing Colors

The CU color definitions are below the configuration block. You can adjust them, but the defaults match CU Boulder's visual identity:

```latex
\definecolor{CUGold}{HTML}{CFB87C}
\definecolor{CUBlack}{HTML}{000000}
\definecolor{CUDarkGray}{HTML}{565A5C}
```

### Changing the Number of Columns

The template defaults to 3 columns. To switch to 2 columns:

1. Change `\colwidth` in the configuration block to `0.47\textwidth`.
2. Move the Column 3 content (Discussion, References, Acknowledgments) into Column 1 or 2.
3. Delete the Column 3 section (marked with `% === COLUMN 3 ===` through `% END COLUMN 3`).

### Adding Figures

```latex
\begin{figure}
  \centering
  \includegraphics[width=\columnwidth]{your-figure.pdf}
  \caption{Description of the figure.}
  \label{fig:yourlabel}
\end{figure}
```

Place figure files in the same directory as `poster.tex`, or in a `figures/` subfolder and use `\graphicspath{{figures/}}`.

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

### "Empty bibliography" warning

This is normal if you haven't added any `\cite{key}` commands to your poster yet. Once you cite at least one reference from `references.bib`, the bibliography will populate after a full build cycle (pdflatex → bibtex → pdflatex → pdflatex).

### Build hangs or MiKTeX prompts for package installation

MiKTeX may try to install missing packages during compilation. If the build seems stuck:

1. Open **MiKTeX Console** (search for it in the Start menu).
2. Go to **Settings** and set "Install missing packages" to **Always**.
3. Run **Updates > Check for updates** while you're there (clears a recurring warning).
4. Try building again.

### "Cannot find LaTeX root file"

Make sure you have `poster.tex` open as the active editor tab when you trigger the build. LaTeX Workshop uses the active file to find the root `.tex` file.

### "Script engine 'perl' not found" (latexmk error)

This means the `.vscode/settings.json` build recipe isn't loading. Make sure you opened the **project root** (`poster/`) as your workspace, not a subfolder. See [Editing and Compiling](#editing-and-compiling) above.

## File Overview

| File | Purpose |
|------|---------|
| `poster.tex` | Main poster source — edit this |
| `references.bib` | BibTeX bibliography entries |
| `../assets/Physics_rev_left.png` | CU Physics department logo |
