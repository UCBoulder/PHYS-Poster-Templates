---
marp: true
theme: cu-physics-poster
size: poster
paginate: false
math: katex
---

<!--
  CU Boulder Physics — MARP Poster Template

  Export with:
    marp --html --allow-local-files poster.md -o poster.pdf

  The --html flag is REQUIRED for the <div> column layout to render.
-->

<!-- ============================================================
     CONFIGURATION — Edit the style variables and header below
     ============================================================ -->

<style>
:root {
  /* Override colors here if needed */
  /* --cu-gold: #CFB87C; */
  /* --cu-black: #000000; */
}
</style>

<!-- ============================================================
     HEADER — Title, authors, affiliations, logo
     ============================================================ -->

<div class="poster-header">
  <img src="../assets/Physics_rev_left.png" alt="CU Physics">
  <div class="title-block">
    <h1>Your Poster Title Goes Here</h1>
    <div class="authors">Author One, Author Two, Author Three</div>
    <div class="affiliations">Department of Physics, University of Colorado Boulder</div>
  </div>
</div>

<!-- ============================================================
     CONTENT — Three-column layout
     Change columns-3 to columns-2 for a two-column layout
     ============================================================ -->

<div class="content">
<div class="columns-3">

<!-- ======================== COLUMN 1 ======================== -->
<div class="column">

## Introduction

Provide the scientific context and motivation for your work. What problem are you addressing, and why does it matter?

- Background on the topic
- Key open question or hypothesis
- Brief statement of your approach

> **Key Insight:** Use blockquotes like this to highlight important takeaways.

## Methods / Experimental Setup

Describe your experimental apparatus, simulation framework, or analytical methods.

The relativistic energy–momentum relation:

$$E^2 = (pc)^2 + (m_0 c^2)^2$$

- Equipment and measurement techniques
- Data collection procedures
- Analysis methods

</div>

<!-- ======================== COLUMN 2 ======================== -->
<div class="column">

## Results

Present your key findings with figures, plots, and tables.

<div class="figure">

![Placeholder for your figure](https://via.placeholder.com/800x500?text=Your+Figure+Here)

<div class="caption">Figure 1: Description of your figure. Use 300 DPI images for best print quality.</div>
</div>

| Parameter | Value | Uncertainty |
|-----------|-------|-------------|
| Mass (kg) | 1.674 | ±0.003 |
| Velocity (m/s) | 2.998 × 10⁸ | ±0.001 × 10⁸ |
| Energy (J) | 1.503 × 10¹⁷ | ±0.005 × 10¹⁷ |

The measured values are consistent with the theoretical prediction from $E = mc^2$.

</div>

<!-- ======================== COLUMN 3 ======================== -->
<div class="column">

## Discussion / Conclusions

Interpret your results and discuss their significance.

- Summary of key findings
- Comparison with theory or prior results
- Implications and future directions

<div class="highlight-box">

**Main Result:** State your single most important finding here in one or two sentences.

</div>

<div class="references">

## References

1. Einstein, A. "Does the Inertia of a Body Depend Upon Its Energy Content?" *Annalen der Physik* **323**, 639–641 (1905).
2. Aad, G. et al. "Observation of a New Particle in the Search for the Standard Model Higgs Boson." *Phys. Lett. B* **716**, 1–29 (2012).
3. Griffiths, D. J. & Schroeter, D. F. *Introduction to Quantum Mechanics*, 3rd ed. (Cambridge, 2018).

</div>

<div class="acknowledgments">

**Acknowledgments**

This work was supported by [funding agency / grant number]. We thank [advisor, collaborators, lab group] for valuable discussions and support.

</div>

</div>

</div><!-- end columns-3 -->
</div><!-- end content -->
