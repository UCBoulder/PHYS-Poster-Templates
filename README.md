# CU Boulder Physics — Poster Templates

Templates and guides for creating research posters sized for the department's HP DesignJet Z6dr (36" roll) using CU Boulder Physics branding.

## Quick Start

| Template | Best For | Prerequisites |
|----------|----------|---------------|
| [LaTeX](latex/) | Publication-quality posters with equations and BibTeX references | TeX Live, MiKTeX, or Overleaf (LuaLaTeX) |
| [MARP (Markdown)](marp/) | Quick posters written in Markdown with live preview | VS Code + Marp extension, or Marp CLI |
| [PowerPoint](powerpoint/) | Pre-built editable template with drag-and-drop editing | Microsoft PowerPoint |

All templates produce a **34.82" x 46.43" landscape PDF** ready for printing.

## Getting the Files

**Download (no git required):** Click the green **Code** button at the top of this page, then select **Download ZIP**. Extract the ZIP and open the folder for your chosen template.

**Clone with git:**
```bash
git clone https://github.com/UCBoulder/PHYS-Poster-Templates.git
```

**PowerPoint only:** If you just need the PowerPoint template, you can download `poster.pptx` directly from the [powerpoint](powerpoint/) folder.

## Poster Specifications

- **Size**: 34.82" tall x 46.43" wide (landscape orientation) — fits the department's 36" roll printer without scaling
- **Format**: Export to PDF before printing
- **Color space**: RGB (the print shop handles conversion)
- **Image resolution**: Use vector formats (PDF, SVG) for plots and diagrams — they print sharp at any size. For raster images (photographs, microscopy), target 300 DPI at the printed size (minimum 150 DPI). See [best practices](best-practices.md#figures-and-images) for details.

## CU Boulder Color Palette

| Color | Hex | Usage |
|-------|-----|-------|
| CU Gold | `#CFB87C` | Primary accent, header bars, borders |
| Black | `#000000` | Body text, headings |
| Dark Gray | `#565A5C` | Secondary text |
| Light Gray | `#A2A4A3` | Subtle backgrounds, dividers |
| Sky Blue | `#096FAE` | Links, secondary accent |
| Dark Blue | `#0A3758` | Alternate header backgrounds |
| Light Gold | `#F3F0E9` | Section backgrounds |
| Accessible Gold | `#8D7334` | Gold text on white backgrounds (meets WCAG AA) |

## Printing on the Department HP DesignJet (36" Roll)

These templates are sized at 34.82" x 46.43" to fit within the printable area of the HP DesignJet Z6dr with a 36" roll. Print at **100% scale** (no scaling needed). Roll-fed plotters cannot print edge-to-edge, so the templates account for the printer margins.

1. Export your poster to PDF from whichever tool you use.
2. Open the PDF and check the document properties to confirm the page size is 46.43" x 34.82".
3. View at **100% zoom** to verify fonts, images, and layout — any pixelation or blurriness visible at 100% will show on the print.
4. Submit the PDF to the [Physics Undergraduate Poster Printing Request form](https://forms.office.com/r/B2FXGzebZn) (requires login with your CU email) or other printing service.

## Resources

- [Poster Design Best Practices](best-practices.md) — layout, typography, and content guidance
- [LaTeX Template](latex/) — LuaLaTeX with CU branding
- [MARP Template](marp/) — Markdown-based poster with CSS theme
- [PowerPoint Template](powerpoint/) — pre-built editable poster with CU branding

## Contact

For questions, bug reports, or suggestions, email [physicslabs@colorado.edu](mailto:physicslabs@colorado.edu).

## Credits

The LaTeX template is based on the [Gemini](https://github.com/anishathalye/gemini) beamer poster theme by Anish Athalye (MIT License).
