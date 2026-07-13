# MATH 21100 — Lecture Demos

Interactive demos for showcasing numerical methods during lecture. The sequence
follows the finalized seven-module course order (plus a reserve Module 8), one
lead demo per lectured topic, with reading-linked and reserve demos placed after
the core sequence.

## Conventions

- **Runtime:** Google Colab. Single Python kernel, zero setup — open from a link and run.
  All libraries used (numpy, matplotlib, sympy, mpmath, ipywidgets) are preinstalled in
  Colab. No Mathematica / Wolfram kernel anywhere, to keep one uniform runtime.
- **Language:** Python throughout. Symbolic work uses **SymPy** where the mathematics
  calls for it (demos 05, 07); flagged below.
- **Precision:** high-precision arithmetic via `mpmath` wherever precision is part of the
  lesson (differentiation step size, cancellation, quadrature nodes, conditioning).
- **Interactivity:** `ipywidgets` (`interact` / `interactive`) for all sliders — NOT
  `matplotlib.widgets.Slider`, which needs an interactive backend Colab lacks. Enable once
  per notebook with `from google.colab import output; output.enable_custom_widget_manager()`.
  Animations via `matplotlib.animation.FuncAnimation` rendered to HTML5 video.
- **Files:** each demo folder holds one `.ipynb` (the Colab demo).
- **Code level:** beginner-to-intermediate, extensively commented — every function
  documented with what it does, its inputs/outputs, and the idea behind it. Students may
  use Python, MATLAB, or Julia on homework; these demos are the reference implementations.

## Numbering

Folder numbers are a stable teaching-order index, not a topic identifier: demos
01–11 are the core lectured sequence in module order, and 12–15 are the
reading-linked, cut, and reserve demos. Numbers were realigned from an earlier
topic ordering; the mapping from the previous layout is recorded at the bottom
of this file.

## Status legend

`[ ]` not started · `[~]` drafted · `[x]` finalized

## Demo list

| # | Demo | Module / § | Role | Libraries | Symbolic? | Status |
|---|------|-----------|------|-----------|-----------|--------|
| 01 | Interpolation: Runge's phenomenon & Chebyshev nodes | M1 §1.3 (lab) | core | numpy, matplotlib, ipywidgets | no | [~] |
| 02 | Newton form & divided-difference table | M1 §1.1.2 | core | numpy, sympy (display) | optional | [~] |
| 03 | Cubic splines & boundary conditions | M1 §1.4.2 | core | numpy, matplotlib, ipywidgets | no | [~] |
| 04 | Numerical differentiation: the optimal-h U-curve | M2 §2.4 (lab) | core | mpmath, numpy, matplotlib, ipywidgets | no | [~] |
| 05 | Least squares & orthogonal polynomials | M3 §3.6 (lab) | core | numpy, matplotlib, sympy | yes (orthogonal polys) | [~] |
| 06 | Quadrature: Newton–Cotes, composite, adaptive Simpson | M4 §4.1, §4.4 | core | numpy, matplotlib, ipywidgets | no | [~] |
| 07 | Gaussian quadrature from orthogonal polynomials | M4 §4.3 | core | sympy, mpmath, numpy, matplotlib | yes (poly construction) | [~] |
| 08 | Euler & Runge–Kutta: convergence order | M5 §5.1–5.4 | core | numpy, matplotlib, ipywidgets | no | [~] |
| 09 | Conditioning: unit ball → ellipse, κ(A) geometry | M6 §6.1 | core | numpy, matplotlib, ipywidgets | no | [~] |
| 10 | Jacobi & Gauss–Seidel convergence, spectral radius | M6 §6.2 | core | numpy, matplotlib | no | [~] |
| 11 | Root-finding: bisection, Newton, secant, cobweb | M7 §7.1–7.2 (lab) | core | numpy, matplotlib, ipywidgets | no | [~] |
| 12 | Gaussian elimination / LU with partial pivoting | M6 [Reading] | reading-linked | numpy | no | [~] |
| 13 | Floating point & catastrophic cancellation | M2 §2.2.1 [Reading] | reading-linked | mpmath, numpy | no | [~] |
| 14 | Power & inverse iteration → dominant eigenvector | — (eigenvalue material cut from M6) | optional | numpy, matplotlib, ipywidgets | no | [~] |
| 15 | Absolute stability regions & stiffness | M8 §8.1–8.2 | reserve | numpy, matplotlib, ipywidgets | no | [~] |

Core lectured sequence: 01–11, in module order. Demos 12 and 13 support topics
delegated to reading (Gaussian-elimination mechanics; roundoff and machine
arithmetic). Demo 14 covers eigenvalue material cut from the iterative-primary
Module 6 and is retained as optional enrichment. Demo 15 belongs to the reserve
Module 8 and is authored only if the term reaches it.

## Per-demo detail

Template: learning goal · what the student sees · interactive controls ·
the theorem it confronts · key parameters/functions.

### 01 — Interpolation: Runge's phenomenon & Chebyshev nodes  (M1 §1.3)
- **Goal:** show that higher-degree polynomial interpolation on equispaced nodes can
  *diverge* (Runge), and that Chebyshev nodes restore convergence.
- **Student sees:** side-by-side plots — left: f, its interpolant, and the nodes;
  right: pointwise error on a log scale with the running max-error printed.
- **Controls:** degree slider (2–40), node-type dropdown (equispaced / Chebyshev),
  function dropdown (Runge / sin πx), interval a,b sliders.
- **Theorem confronted:** interpolation error formula
  f−pₙ = f⁽ⁿ⁺¹⁾(ξ)/(n+1)! · ∏(x−xₖ); the node polynomial ω(x) is the culprit,
  and Chebyshev nodes minimize max|ω|.
- **Verified:** equispaced max-error 1.9 → 60 → 2388 (deg 10/20/30); Chebyshev
  0.11 → 0.015 → 0.002.
- **File:** `01_interpolation_runge_chebyshev/interpolation_runge_chebyshev.ipynb`

### 02 — Newton form & divided-difference table  (M1 §1.1.2)
_TBD_

### 03 — Cubic splines & boundary conditions  (M1 §1.4.2)
_TBD_

### 04 — Numerical differentiation: the optimal-h U-curve  (M2 §2.4, lab)
- **Goal:** confront the roundoff-versus-truncation tradeoff, the course's clearest
  instance, and locate the finite optimal step size.
- **Student sees:** total error vs step size on log-log axes for the forward and
  central differences, with the truncation and rounding branches meeting at a U;
  a second panel compares the central difference against its Richardson extrapolation.
- **Controls:** function dropdown (exp, sin, rational), x₀ slider, and a log₁₀(h) slider
  reading the error at a chosen step.
- **Theorem confronted:** E₊(h) ≈ (h/2)|f″| + 2u|f|/h with minimum near h∗∼√u; central
  E₀(h) ≈ (h²/6)|f‴| + u|f|/h with minimum near h∗∼u^(1/3). Richardson combines
  central differences at h and h/2 to cancel the O(h²) term, giving O(h⁴).
- **Verified against a 50-digit mpmath reference:** forward min error 3.3e-9 at h≈1.1e-8
  (predicted √u≈1.5e-8); central min error 1.0e-13 at h≈2.9e-6 (predicted u^(1/3)≈6.1e-6);
  Richardson cuts the central error at h=1e-2 from 4.5e-5 to 5.7e-11.
- **File:** `04_numerical_differentiation_optimal_h/numerical_differentiation_optimal_h.ipynb`

### 05 — Least squares & orthogonal polynomials  (M3 §3.6, lab)
_TBD_

### 06 — Quadrature: Newton–Cotes, composite, adaptive Simpson  (M4 §4.1, §4.4)
- **Goal:** establish the composite convergence orders and motivate adaptivity on a
  localized-feature integrand.
- **Student sees:** composite error vs panel count on log-log axes (slopes recovered
  per rule); a degree-of-exactness check; and the panel boundaries adaptive Simpson
  chooses, clustering around a narrow spike.
- **Controls:** log₁₀(tolerance) slider driving the adaptive refinement, reporting the
  panel count and error.
- **Theorem confronted:** composite trapezoid and midpoint are O(h²), composite Simpson
  is O(h⁴) with degree of exactness 3; adaptive Simpson uses an interval-halving
  (Richardson) error estimate with a recursion-depth cap.
- **Verified:** fitted slopes 2.00 (trapezoid, midpoint) and 4.00 (Simpson); Simpson exact
  through cubics; adaptive Simpson resolves a Gaussian spike to 7.4e-8 with 30 panels.
- **File:** `06_quadrature_newton_cotes_adaptive/quadrature_newton_cotes_adaptive.ipynb`

### 07 — Gaussian quadrature from orthogonal polynomials  (M4 §4.3)
- **Goal:** derive the Gauss nodes as orthogonal-polynomial roots and demonstrate the
  degree-of-exactness 2n−1.
- **Student sees:** the constructed Legendre nodes and weights; a check against numpy's
  built-in; a monomial-by-monomial exactness table; and a per-evaluation accuracy race
  against composite Simpson.
- **Controls:** integrand dropdown; the construction runs at n = 2…5.
- **Theorem confronted:** n-point Gauss-Legendre integrates every polynomial of degree
  ≤ 2n−1 exactly, via p = qPₙ + r and orthogonality; weights wᵢ = 2/((1−xᵢ²)Pₙ′(xᵢ)²).
- **Verified:** constructed nodes/weights match numpy to 1.1e-16; exactness confirmed
  through degree 2n−1 for n = 2…5; on cos 3x over [0,2] Gauss reaches 1e-16 by ~12
  evaluations while Simpson sits at 3e-5.
- **Symbolic:** Legendre polynomials built with SymPy; roots and weights refined with mpmath.
- **File:** `07_gaussian_quadrature_orthogonal_polys/gaussian_quadrature_orthogonal_polys.ipynb`

### 08 — Euler & Runge–Kutta: convergence order  (M5 §5.1–5.4)
- **Goal:** measure the global order of explicit one-step methods and separate order
  (accuracy) from stability (demo 15).
- **Student sees:** global error at the final time vs step size on log-log axes for
  Euler, RK2, and RK4 (slopes recovered); and the three numerical solutions overlaid on
  the exact curve at a coarse step.
- **Controls:** problem dropdown (y′=y; y′=−2ty) and a step-size slider.
- **Theorem confronted:** a method of order p has global error O(hᵖ); forward Euler p=1,
  explicit midpoint p=2, classical RK4 p=4.
- **Verified:** fitted orders 0.97 (Euler), 1.98 (RK2), 3.97 (RK4) on y′=y over [0,1].
- **File:** `08_euler_rungekutta_convergence_order/euler_rungekutta_convergence_order.ipynb`

### 09 — Conditioning: unit ball → ellipse  (M6 §6.1)
_TBD_

### 10 — Jacobi & Gauss–Seidel convergence  (M6 §6.2)
_TBD_

### 11 — Root-finding & cobweb diagrams  (M7 §7.1–7.2, lab)
_TBD_

### 12 — Gaussian elimination / LU with partial pivoting  (M6, reading)
_TBD — supports the delegated Gaussian-elimination reading._

### 13 — Floating point & catastrophic cancellation  (M2 §2.2.1, reading)
- **Goal:** the roundoff reading behind the numerical-differentiation lab; measures
  cancellation against a 50-digit reference and shows an equivalent formula that removes it.
- **Verified:** naive (1−cos x)/x² relative error climbs to 100% as x→0; the stable form
  2 sin²(x/2)/x² stays exact.
- **File:** `13_floating_point_cancellation/floating_point_cancellation.ipynb`

### 14 — Power & inverse iteration  (optional; eigenvalue material cut from M6)
_TBD — retained as enrichment; not in the default lecture sequence._

### 15 — Absolute stability regions & stiffness  (M8 §8.1–8.2, reserve)
- **Goal:** distinguish stability from order; show why explicit methods fail on stiff
  problems and backward Euler does not.
- **Student sees:** the absolute stability regions {|R(z)|≤1} for explicit Euler, RK4,
  and backward Euler; and a stiff decay problem where the explicit solution blows up
  while backward Euler stays bounded.
- **Controls:** λ slider and step-size slider, reporting whether z=hλ lies in the explicit
  stability interval.
- **Theorem confronted:** on y′=λy each method is multiplication by R(z), z=hλ; stability
  is |R(z)|≤1. Explicit Euler is stable for z∈[−2,0] (h≤2/|λ|); backward Euler is A-stable.
- **Verified:** with λ=50, h=0.05 (z=−2.5, outside the region) explicit Euler reaches
  3.3e3 while backward Euler gives 1.3e-11 against the exact 1.9e-22.
- **File:** `15_stability_regions_stiffness/stability_regions_stiffness.ipynb`

## Renumbering map (previous layout → current)

| Previous | Current | Note |
|----------|---------|------|
| 01, 02, 03 | 01, 02, 03 | unchanged (Module 1) |
| 04 least squares | 05 | moved to Module 3 slot |
| 05 Gaussian elimination | 12 | reading-linked, moved after core |
| 06 conditioning | 09 | Module 6 |
| 07 floating point | 13 | reading-linked, moved after core |
| 08 Jacobi / Gauss–Seidel | 10 | Module 6 |
| 09 power / inverse iteration | 14 | eigenvalue material cut, retained optional |
| 10 root-finding | 11 | Module 7 |
| (placeholder) numerical differentiation | 04 | new content, Module 2 |
| (placeholder) quadrature | 06 | new content, Module 4 |
| (placeholder) Gaussian quadrature | 07 | new content, Module 4 |
| (placeholder) Euler / RK | 08 | new content, Module 5 |
| 15 stability & stiffness | 15 | new content, reserve Module 8 |
