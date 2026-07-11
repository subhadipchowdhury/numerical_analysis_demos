# MATH 21100 — Lecture Demos

Interactive demos for showcasing numerical methods during lecture. One lead demo per
learning standard (Standard 6 is split into a geometry demo and a floating-point demo,
so 15 demos for 14 standards).

## Conventions

- **Runtime:** Google Colab. Single Python kernel, zero setup — open from a link and run.
  All libraries used (numpy, matplotlib, sympy, mpmath, ipywidgets) are preinstalled in
  Colab. No Mathematica / Wolfram kernel anywhere, to keep one uniform runtime.
- **Language:** Python throughout. Symbolic work uses **SymPy** where the mathematics
  calls for it (demos 04, 13); flagged below.
- **Precision:** high-precision arithmetic via `mpmath` wherever precision is part of the
  lesson (conditioning, cancellation, quadrature nodes, optimal step size).
- **Interactivity:** `ipywidgets` (`interact` / `interactive`) for all sliders — NOT
  `matplotlib.widgets.Slider`, which needs an interactive backend Colab lacks. Enable once
  per notebook with `from google.colab import output; output.enable_custom_widget_manager()`.
  Animations via `matplotlib.animation.FuncAnimation` rendered to HTML5 video.
- **Files:** each demo folder holds one `.ipynb` (the Colab demo) plus, where useful, a
  plain `.py` script version.
- **Code level:** beginner-to-intermediate, extensively commented — every function
  documented with what it does, its inputs/outputs, and the idea behind it. Students may
  use Python, MATLAB, or Julia on homework; these demos are the reference implementations.

## Status legend

`[ ]` not started · `[~]` drafted · `[x]` finalized

## Demo list

| # | Demo | Std | Week | Libraries | Symbolic? | Status |
|---|------|-----|------|-----------|-----------|--------|
| 01 | Interpolation: Runge's phenomenon & Chebyshev nodes | 1,2 | 1–2 | numpy, matplotlib, ipywidgets | no | [ ] |
| 02 | Newton form & divided-difference table | 1 | 1 | numpy, sympy (display) | optional | [ ] |
| 03 | Cubic splines & boundary conditions | 3 | 3 | numpy, matplotlib, ipywidgets | no | [ ] |
| 04 | Least squares & orthogonal polynomials | 4 | 3–4 | numpy, matplotlib, sympy | yes (orthogonal polys) | [ ] |
| 05 | Gaussian elimination / LU with partial pivoting | 5 | 4 | numpy | no | [ ] |
| 06 | Conditioning: unit ball → ellipse, κ(A) geometry | 6 | 5 | numpy, matplotlib, ipywidgets | no | [ ] |
| 07 | Floating point & catastrophic cancellation | 6 | 5 | mpmath, numpy | no | [ ] |
| 08 | Jacobi & Gauss–Seidel convergence, spectral radius | 7 | 6 | numpy, matplotlib | no | [ ] |
| 09 | Power & inverse iteration → dominant eigenvector | 8 | 6 | numpy, matplotlib, ipywidgets | no | [ ] |
| 10 | Root-finding: bisection, Newton, secant, cobweb | 9 | 7 | numpy, matplotlib, ipywidgets | no | [ ] |
| 11 | Numerical differentiation: the optimal-h U-curve | 10 | 7 | mpmath, numpy, matplotlib | no | [ ] |
| 12 | Quadrature: Newton–Cotes, composite, adaptive | 11 | 8 | numpy, matplotlib, ipywidgets | no | [ ] |
| 13 | Gaussian quadrature from orthogonal polynomials | 12 | 8 | sympy, mpmath, numpy | yes (poly construction) | [ ] |
| 14 | Euler & Runge–Kutta: convergence order | 13 | 8–9 | numpy, matplotlib | no | [ ] |
| 15 | Absolute stability regions & stiffness | 14 | 9 | numpy, matplotlib | no | [ ] |

## Per-demo detail

Filled in as we discuss each. Template: learning goal · what the student sees ·
interactive controls · the theorem it confronts · key parameters/functions.

### 01 — Interpolation: Runge's phenomenon & Chebyshev nodes
_TBD_

### 02 — Newton form & divided-difference table
_TBD_

### 03 — Cubic splines & boundary conditions
_TBD_

### 04 — Least squares & orthogonal polynomials
_TBD_

### 05 — Gaussian elimination / LU with partial pivoting
_TBD_

### 06 — Conditioning: unit ball → ellipse
_TBD_

### 07 — Floating point & catastrophic cancellation
_TBD_

### 08 — Jacobi & Gauss–Seidel convergence
_TBD_

### 09 — Power & inverse iteration
_TBD_

### 10 — Root-finding & cobweb diagrams
_TBD_

### 11 — Numerical differentiation: optimal h
_TBD_

### 12 — Quadrature: Newton–Cotes to adaptive
_TBD_

### 13 — Gaussian quadrature from orthogonal polynomials
_TBD_

### 14 — Euler & Runge–Kutta convergence order
_TBD_

### 15 — Absolute stability regions & stiffness
_TBD_
