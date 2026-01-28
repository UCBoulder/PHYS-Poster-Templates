# Poster Design Best Practices

Guidelines for creating effective research posters for the CU Boulder Physics Department. The default template size is 35.61" x 47.48" (landscape), which fits the department's 36" roll printer without scaling.

## Layout Principles

- **Visual hierarchy**: The title and key result should be readable from 10 feet away. Details are for close-up reading.
- **Flow**: Use a column layout (typically 3 columns) that reads left-to-right, top-to-bottom.
- **White space**: Don't fill every inch. Generous margins and spacing between sections improve readability.
- **Alignment**: Keep elements aligned to a grid. Ragged layouts look unprofessional at poster scale.

## Typography at Print Scale

At 36" x 48", fonts need to be much larger than on screen. Target sizes:

| Element | Size Range |
|---------|-----------|
| Title | 72–96 pt |
| Author names / affiliations | 36–48 pt |
| Section headings | 36–48 pt |
| Body text | 24–28 pt |
| Captions and footnotes | 20–24 pt |
| References | 18–20 pt |

**Font choices**: Use Helvetica Neue (CU's primary font) or Arial as a substitute. Noto Serif works well for body text if you prefer a serif font. Stick to one or two font families.

## CU Color Palette Usage

- Use **CU Gold (`#CFB87C`)** for accent bars, borders, and highlights — not for body text on white (poor contrast).
- For gold-colored text on white backgrounds, use **Accessible Gold (`#8D7334`)** which meets WCAG AA contrast requirements.
- Use **Black (`#000000`)** or **Dark Gray (`#565A5C`)** for body text.
- Use **Light Gold (`#F3F0E9`)** as a section background for visual grouping.
- **Sky Blue (`#096FAE`)** and **Dark Blue (`#0A3758`)** work well for secondary accents, links, or alternate header styles.

**Accessibility**: Ensure all text/background combinations have a contrast ratio of at least 4.5:1 (WCAG AA). Test with a contrast checker if unsure.

## Figures and Images

- **Resolution**: Minimum 150 DPI at the printed size, 300 DPI preferred. A figure that appears 8" wide on the poster needs to be at least 1200 x 900 pixels (at 150 DPI).
- **Vector graphics**: Use PDF, SVG, or EPS for plots and diagrams whenever possible — they scale without quality loss.
- **Labels**: Make axis labels, tick marks, and legends large enough to read at arm's length (~18–24 pt equivalent).
- **Captions**: Place a short caption below each figure. Number figures for easy reference.

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
- Use colorblind-friendly color maps (e.g., viridis, cividis — avoid red/green only).
- Add legends directly to plots rather than relying on figure captions alone.
- Error bars should be clearly visible.

### Data Tables
- Keep tables small — if the table has more than ~15 entries, consider a plot instead.
- Use alternating row shading for readability.
- Bold the header row and include units in column headers.

## Common Mistakes

- **Too much text**: A poster is not a paper. Use bullet points and short sentences. Aim for ~800 words total (excluding references).
- **Low-resolution images**: Screen-resolution images (72 DPI) look pixelated when printed at poster size. Always check DPI.
- **Poor contrast**: Light text on light backgrounds or small text in low-contrast colors. Test by viewing your poster at 50% zoom — if you can't read it, neither can your audience.
- **Tiny references**: References should still be readable. 18–20 pt minimum.
- **No visual focus**: Every poster should have one figure or result that immediately draws the eye.
- **Missing logo**: Include the CU Physics logo in the title banner. See the `assets/` folder for the department logo.

## Department Branding Placement

- Place the **CU Physics logo** (`assets/Physics_rev_left.png`) in the top-left or top-right of the title banner.
- The logo works best on a dark (black or dark blue) background. The provided logo is white/reversed.
- If your work is funded by a grant, include the funding agency logo near the acknowledgments section.
- Leave the CU logo at its original aspect ratio — do not stretch or distort it.
