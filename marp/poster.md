---
marp: true
theme: cu-physics-poster
size: poster
paginate: false
math: mathjax
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
     HEADER — Title row + logo/author row
     ============================================================ -->

<div class="poster-header">
  <div class="header-title-row">
    <h1>Your Poster Title Goes Here</h1>
  </div>
  <div class="header-info-row">
    <img class="logo-left" src="../assets/Boulder_left_lockup_rev_2025.png" alt="CU Boulder">
    <div class="author-block">
      <div class="authors">Author One<sup>1</sup>, Author Two<sup>1,2</sup>, Author Three<sup>2</sup></div>
      <div class="affiliations"><sup>1</sup>Department of Physics, University of Colorado Boulder &nbsp;&nbsp; <sup>2</sup>JILA, University of Colorado Boulder</div>
    </div>
    <img class="logo-right" src="../assets/Physics_rev_left.png" alt="CU Physics">
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

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Morbi accumsan fermentum magna, vel pretium arcu fermentum ac. Nunc pellentesque eros sed ligula ultrices varius. Integer vel nunc et mi porta eleifend [3].

- Lorem ipsum dolor sit amet, consectetur adipiscing elit
- Pellentesque ultricies velit in fermentum vestibulum
- Nunc a lectus et eros facilisis hendrerit eu non urna

> **Key Insight:** Lorem ipsum dolor sit amet, consectetur adipiscing elit. Morbi accumsan fermentum magna, vel pretium arcu fermentum ac.

## Theoretical Framework

The spectral energy density $u(\nu, T)$ is given by:

$$u(\nu, T) = \frac{8\pi h\nu^3}{c^3} \frac{1}{e^{h\nu/k_B T} - 1} \tag{1}$$

where $h$ is Planck's constant, $\nu$ is frequency, $c$ is the speed of light, and $k_B$ is Boltzmann's constant. In the low-frequency limit ($h\nu \ll k_B T$), this reduces to the Rayleigh--Jeans approximation $u(\nu, T) \approx 8\pi\nu^2 k_B T / c^3$.

- In the high-frequency regime, the exponential cutoff dominates
- At low frequencies, the classical approximation holds
- The peak frequency $\nu_{\max}$ shifts linearly with temperature

## Methods

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur condimentum sem id semper vulputate. Nam lobortis ultrices iaculis. Maecenas bibendum, sem vel vehicula tempus, nisi tortor eleifend tellus.

- Duis finibus finibus sapien, ut mollis odio malesuada
- Aenean ut ex augue, quisque vulputate scelerisque eros
- Proin ultrices sodales nulla eu molestie nullam

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Morbi accumsan fermentum magna, vel pretium arcu fermentum ac [1]. Nunc pellentesque eros sed ligula ultrices varius. Integer vel nunc et mi porta eleifend. Praesent eget felis a ante facilisis viverra non ut lacus.

</div>

<!-- ======================== COLUMN 2 ======================== -->
<div class="column">

## Experimental Setup

<div class="figure">

![Experimental setup diagram](../assets/example-diagram.svg)

<div class="caption">Figure 1: Schematic of the experimental apparatus.</div>
</div>

<div class="section-highlight">

## Results

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed non risus. Suspendisse lectus tortor, dignissim sit amet, adipiscing nec, ultricies sed, dolor. See Fig. 1 and Table 1.

<div class="table-wrap">

| Parameter | Value | Uncertainty |
|---|---|---|
| Sample temperature (K) | 4.21 | ±0.05 |
| Applied field (T) | 1.50 | ±0.01 |
| Resonance frequency (GHz) | 9.38 | ±0.02 |
| Linewidth (MHz) | 12.7 | ±0.3 |
| Signal-to-noise ratio | 42.0 | ±1.5 |

<div class="caption">Table 1: Summary of measured experimental parameters.</div>
</div>

The measured spectral distribution is consistent with the theoretical prediction from Eq. (1), confirming the validity of the model across the full frequency range examined.

</div>

## Data Analysis

Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Fusce aliquet pede non pede. Suspendisse dapibus lorem pellentesque magna [5].

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Morbi accumsan fermentum magna, vel pretium arcu fermentum ac. Nunc pellentesque eros sed ligula ultrices varius. Integer vel nunc et mi porta eleifend.
</div>

<!-- ======================== COLUMN 3 ======================== -->
<div class="column">

## Data Analysis (continued)

<div class="figure">

![Example scatter plot](../assets/example-plot.svg)

<div class="caption">Figure 2: Measured values as a function of the control parameter. The gold line shows the theoretical prediction from Eq. (1); blue points are experimental data with error bars.</div>
</div>

<div class="block-highlight">
<h3>Central Result</h3>

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus congue volutpat elit non semper. Phasellus mauris felis, molestie ac pharetra quis, tempus nec ante.

</div>

## Discussion

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras imperdiet vel elit dignissim cursus. As shown in Eq. (1) and Fig. 2, the results are consistent with our initial hypothesis [4].

- Sed luctus elit sit amet dictum maximus
- Pellentesque facilisis dolor in leo bibendum congue

<div class="highlight-box">

**Main Conclusion:** Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec finibus ante vel purus mollis fermentum [2].

</div>

<div class="references">

## References

1. ATLAS Collaboration. "Observation of a New Particle in the Search for the Standard Model Higgs Boson." *Phys. Lett. B* **716**, 1–29 (2012).
2. Doe, J. & Roe, R. "Precision Measurements of Lorem Ipsum Parameters." *Proc. Int. Conf. Placeholder Phys.* 112–118 (2023).
3. Einstein, A. "On the Electrodynamics of Moving Bodies." *Ann. Phys.* **322**, 891–921 (1905).
4. Griffiths, D. J. *Introduction to Quantum Mechanics*, 3rd ed. Cambridge University Press (2018).
5. Smith, A. B. & Jones, C. D. "Lorem Ipsum Dolor Sit Amet." arXiv:2401.00001 (2024).

</div>

<div class="acknowledgments">

**Acknowledgments:** This work was supported by the National Science Foundation (Grant No. PHY-XXXXXXX). We thank Prof. A. B. Smith for valuable discussions, the CU Boulder Department of Physics machine shop for technical support, and Dr. C. D. Jones for assistance with data analysis. Additional thanks to the CU Boulder Department of Physics for poster printing resources.

</div>

</div>

</div><!-- end columns-3 -->
</div><!-- end content -->

<!-- ============================================================
     FOOTER
     ============================================================ -->

<div class="poster-footer">
  <span>author@colorado.edu</span>
  <span>ABC Conference 2026, City</span>
  <span>https://www.colorado.edu</span>
</div>
