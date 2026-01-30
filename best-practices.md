# Poster Design Best Practices

Guidelines for creating effective research posters for the CU Boulder Physics Department. The default template size is 34.82" x 46.43" (landscape), which fits the department's 36" roll printer without scaling.

## Layout Principles

- **Visual hierarchy**: The title and key result should be readable from 10 feet away. Details are for close-up reading.
- **Flow**: Use a column layout (typically 3 columns) that reads left-to-right, top-to-bottom.
- **White space**: Don't fill every inch. Generous margins and spacing between sections improve readability.
- **Alignment**: Keep elements aligned to a grid. 

## Typography at Print Scale

At 36" x 48", fonts need to be much larger than on screen. Target sizes:

| Element | Size Range |
|---------|-----------|
| Title | 72–96 pt |
| Author names | 36–48 pt |
| Affiliations | 28–36 pt |
| Section headings | 36–48 pt |
| Body text | 24–28 pt |
| Captions and footnotes | 20–24 pt |
| References | 18–20 pt |

**Font choices**: Helvetica Neue is CU's primary brand font; Arial is a widely available substitute. The LaTeX template uses Raleway and Lato (part of the Gemini theme), which are also fine. Stick to one or two font families.

## CU Color Palette Usage

- Use **CU Gold (`#CFB87C`)** for accent bars, borders, and highlights — not for body text on white (poor contrast).
- For gold-colored text on white backgrounds, use **Accessible Gold (`#8D7334`)** which meets WCAG AA contrast requirements.
- Use **Black (`#000000`)** or **Dark Gray (`#565A5C`)** for body text.
- Use **Light Gold (`#F3F0E9`)** as a section background for visual grouping.
- **Sky Blue (`#096FAE`)** and **Dark Blue (`#0A3758`)** work well for secondary accents, links, or alternate header styles.

**Accessibility**: Ensure all text/background combinations have a contrast ratio of at least 4.5:1 (WCAG AA). Test with a contrast checker if unsure.

## Figures and Images

### Use vector formats first

Export plots, charts, diagrams, and schematics as **PDF or SVG** whenever possible. Vector graphics are resolution-independent and will always print perfectly sharp, regardless of size. This is the single most effective way to avoid blurry figures.

- **matplotlib**: `plt.savefig('figure.pdf')` or `plt.savefig('figure.svg')`
- **R / ggplot2**: `ggsave('figure.pdf')` or `ggsave('figure.svg')`
- **MATLAB**: `exportgraphics(gcf, 'figure.pdf', 'ContentType', 'vector')`
- **Inkscape / Illustrator / draw.io**: Export as PDF or SVG

Reserve raster formats (PNG, TIFF) for content that cannot be vectorized — photographs, microscopy images, and complex rendered visualizations. Avoid JPEG for figures with sharp edges or text; its lossy compression introduces artifacts.

### Raster image resolution

For raster images, target **300 DPI at the printed size**. The absolute minimum is 150 DPI, but quality loss is noticeable when viewers lean in to 2–3 feet — which they will at a poster session. Going above 300 DPI provides no visible benefit on inkjet plotters and only increases file size.

What matters is **pixel count relative to printed size**, not the DPI metadata tag in the file. Use this formula:

> **Required pixels = printed width (inches) x DPI**

| Figure width on poster | 150 DPI (minimum pixels) | 300 DPI (target pixels) |
|---|---|---|
| 4 inches | 600 px | 1,200 px |
| 6 inches | 900 px | 1,800 px |
| 8 inches | 1,200 px | 2,400 px |
| 10 inches | 1,500 px | 3,000 px |
| 14 inches (full column) | 2,100 px | 4,200 px |

When exporting raster images from code, set the DPI explicitly:

- **matplotlib**: `plt.savefig('figure.png', dpi=300)`
- **R / ggplot2**: `ggsave('figure.png', dpi= 300)`
- **MATLAB**: `exportgraphics(gcf, 'figure.png', 'Resolution', 300)`

**Do not upscale low-resolution images.** Enlarging a 72 DPI screenshot to 300 DPI in an image editor just produces a larger blurry image — no detail is added. If an image doesn't have enough pixels, re-export it from the source at a higher resolution, or use a vector format instead.

### Labels and captions

- Make axis labels, tick marks, and legends large enough to read at arm's length (~18–24 pt equivalent minimum).
- Place a short caption below each figure. Number figures for easy reference.

## Content Structure

A typical physics poster includes these sections:

1. **Title banner** — Title, authors, affiliations, department logo, funding logos
2. **Introduction / Motivation** — What problem are you addressing and why does it matter?
3. **Methods / Experimental Setup** — How did you approach the problem?
4. **Results** — Key findings with figures, plots, or tables
5. **Discussion / Conclusions** — What do the results mean? What's next?
6. **References** — Cite key sources (keep this short — 5–10 references max)
7. **Acknowledgments** — Funding sources, collaborators, advisors

Not every poster needs all sections. Adapt to your content.

## Physics-Specific Tips

### Equations
- Keep equations to a minimum. Include only the ones essential to understanding your work.
- Number and label every equation you reference in the text.
- Define all variables when they first appear.
- Use large font sizes for displayed equations — they should be readable from 3–4 feet away.

### Plots and Data
- Use large axis labels and tick labels (18–24 pt equivalent).
- Include units on all axes.
- Use colorblind-friendly color maps (e.g., viridis, cividis — avoid red/green only). In matplotlib: `plt.set_cmap('viridis')`. To check your figures, upload them to [COBLIS](https://www.color-blindness.com/coblis-color-blindness-simulator/) or use the [Sim Daltonism](https://michelf.ca/projects/sim-daltonism/) app (macOS). See the [matplotlib colormaps reference](https://matplotlib.org/stable/gallery/color/colormap_reference.html) for accessible options.
- Add legends directly to plots rather than relying on figure captions alone.
- Error bars should be clearly visible.

### Data Tables
- Keep tables small — if the table has more than ~15 entries, consider a plot instead.
- Use clean horizontal rules (booktabs style) or alternating row shading to distinguish rows. Avoid heavy grid lines.
- Bold the header row and include units in column headers.

## Common Mistakes

- **Too much text**: A poster is not a paper. Use bullet points and short sentences. Aim for ~800 words total (excluding references).
- **Low-resolution images**: Screen-resolution images (72 DPI) look pixelated when printed at poster size. Check pixel dimensions against the printed size (see [Figures and Images](#figures-and-images) above). Export plots as PDF/SVG to avoid the problem entirely.
- **Poor contrast**: Light text on light backgrounds or small text in low-contrast colors. Test by viewing your poster at 50% zoom — if you can't read it, neither can your audience.
- **Tiny references**: References should still be readable. 18–20 pt minimum.
- **No visual focus**: Every poster should have one figure or result that immediately draws the eye.
- **Missing logo**: Include at least one CU logo in the title banner. See the `assets/` folder for available logos and the template READMEs for how to configure them.
