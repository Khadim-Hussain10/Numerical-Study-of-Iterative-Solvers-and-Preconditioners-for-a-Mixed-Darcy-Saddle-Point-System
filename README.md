# Numerical Study of Iterative Solvers and Preconditioners for a Mixed Darcy Saddle-Point System

![Status](https://img.shields.io/badge/Project-Completed-2E8B57?style=flat-square)
![Language](https://img.shields.io/badge/Language-Python-3776AB?style=flat-square&logo=python&logoColor=FFD343)
![Notebooks](https://img.shields.io/badge/Notebooks-5_Completed-2E8B57?style=flat-square)
![Research](https://img.shields.io/badge/Research-Numerical_Methods-6A5ACD?style=flat-square)

## About This Project

I started this project to improve my understanding of saddle-point problems, mixed finite element methods, iterative solvers, and preconditioning techniques using Python.

I am using a two-dimensional Darcy flow problem as a starting point. My goal is to understand the mixed formulation, solve the numerical system, and study how different solvers and preconditioners perform.

This project is related to my broader research interest in iterative preconditioners for saddle-point problems.

---

## Research Objectives

- Understand mixed finite element formulations.
- Implement a mixed Darcy saddle-point system.
- Study MINRES and GMRES iterative solvers.
- Implement Schur complement preconditioners.
- Study the artificial compressibility approach.
- Compare numerical convergence and computational costs.

---

## Mathematical Problem

I consider the Darcy flow problem on a two-dimensional unit square with unit permeability (K = 1).

**q = −∇p**

**∇ · q = f**

After discretization using RT0 elements for flux and P0 elements for pressure, the resulting saddle-point system is:

```text
⎡ A   −Dᵀ ⎤ ⎡ q ⎤   ⎡  0 ⎤
⎢         ⎥ ⎢   ⎥ = ⎢    ⎥
⎣ −D   0  ⎦ ⎣ p ⎦   ⎣ −F ⎦
```

I use this system throughout my numerical experiments.

---

## Tools and Libraries

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=FFD343)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white)
![SciPy](https://img.shields.io/badge/SciPy-8CAAE6?style=for-the-badge&logo=scipy&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Matplotlib](https://custom-icon-badges.demolab.com/badge/Matplotlib-11557C?style=for-the-badge&logo=matplotlib&logoColor=white)
![scikit-fem](https://img.shields.io/badge/scikit--fem-287D46?style=for-the-badge)
![Google Colab](https://img.shields.io/badge/Google_Colab-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=black)
![Kaggle](https://img.shields.io/badge/Kaggle-20BEFF?style=for-the-badge&logo=kaggle&logoColor=white)

---

## Research Workflow

```text
Mixed Darcy Formulation [Completed]
    ↓
Finite Element Discretization [Completed]
    ↓
Saddle-Point System [Completed]
    ├── Direct Solver [Completed]
    ├── MINRES and GMRES [Completed]
    ├── Schur Complement Preconditioners [Completed]
    └── Artificial Compressibility Approach [Completed]
    ↓
Final Numerical Comparison [Completed]
```
---

## Current Progress

So far, I have completed five notebooks.

| Notebook | Research Topic | Status |
|---|---|---|
| 01 | Mixed Darcy Formulation | ![Completed](https://img.shields.io/badge/Completed-2E8B57?style=flat-square) |
| 02 | MINRES and GMRES | ![Completed](https://img.shields.io/badge/Completed-2E8B57?style=flat-square) |
| 03 | Schur Complement Preconditioners | ![Completed](https://img.shields.io/badge/Completed-2E8B57?style=flat-square) |
| 04 | Artificial Compressibility | ![Completed](https://img.shields.io/badge/Completed-2E8B57?style=flat-square) |
| 05 | Final Numerical Comparison | ![Completed](https://img.shields.io/badge/Completed-2E8B57?style=flat-square) |
---

## Notebook 1: Mixed Darcy Formulation

**[Open Notebook 1](01_mixed_darcy_formulation.ipynb)**

In my first notebook, I implemented a 2D mixed Darcy problem using RT0 elements for flux and P0 elements for pressure.

I assembled the saddle-point matrix and solved the system using SciPy's direct solver.

### Work Completed

- Mixed finite element discretization.
- Saddle-point matrix assembly.
- Direct solution of the numerical system.
- Pressure and flux error analysis.
- Mesh refinement study.
- Discrete local mass conservation check.

I observed that the pressure and flux errors decreased when I refined the mesh.

These tests gave me a starting point for working with iterative solvers.

---

## Notebook 2: MINRES and GMRES

**[Open Notebook 2](02-minres-gmres-solvers.ipynb)**

In my second notebook, I studied MINRES and GMRES and used them to solve the same mixed Darcy system without preconditioners.

### Work Completed

- Implementation of MINRES and GMRES.
- Comparison with the direct solver.
- Iteration count and residual analysis.
- Mesh refinement study.
- Solver tolerance investigation.
- Residual convergence graphs.
- Computation time comparison.

During the experiments, I noticed that MINRES could report successful completion even when my calculated relative residual was above the target. I tested different tolerances to investigate this.

### Numerical Results

For the 16 × 16 mesh with 1312 unknowns:

| Solver | Iterations | Relative Residual |
|---|---:|---:|
| MINRES | 173 | 5.09 × 10⁻¹⁰ |
| GMRES | 363 | 9.93 × 10⁻⁹ |

Both solvers reached my actual relative residual target of 10⁻⁸.

In my timing experiment, the direct solver was the fastest, followed by MINRES and GMRES.

I used these results as a baseline for testing preconditioners.

---

## Notebook 3: Schur Complement Preconditioners

**[Open Notebook 3](03-schur-complement-preconditioners.ipynb)**

In my third notebook, I studied the Schur complement and implemented different block preconditioning methods.

### Preconditioners Implemented

- Exact block diagonal preconditioner.
- Exact block triangular preconditioner.
- Approximate block diagonal preconditioner.

The exact Schur complement is:

**S = D A⁻¹ Dᵀ**

I also calculated an approximate Schur complement using the diagonal elements of the flux mass matrix:

**S̃ = D diag(A)⁻¹ Dᵀ**

### Work Completed

- Exact and approximate Schur complement calculations.
- Block preconditioner implementation.
- Preconditioned MINRES and GMRES.
- Solver tolerance investigation.
- Mesh refinement study.
- Preconditioner setup cost analysis.
- Computation time comparison.
- Visualization of numerical results.

### Mesh Refinement Study

| Mesh Size | Number of Triangles | Total DOFs |
|---|---:|---:|
| 4 × 4 | 32 | 88 |
| 8 × 8 | 128 | 336 |
| 16 × 16 | 512 | 1312 |

### Numerical Results

Iteration counts for the 16 × 16 mesh:

| Preconditioner | MINRES | GMRES |
|---|---:|---:|
| Without preconditioner | 173 | 363 |
| Exact block diagonal | 2 | 2 |
| Exact block triangular | — | 2 |
| Approximate block diagonal | 34 | 32 |

### Iteration Reduction

| Preconditioner | MINRES | GMRES |
|---|---:|---:|
| Exact block diagonal | 98.84% | 99.45% |
| Exact block triangular | — | 99.45% |
| Approximate block diagonal | 80.35% | 91.18% |

All 21 configurations in my mesh refinement study reached the actual relative residual target of 10⁻⁸.

I observed that the exact preconditioners maintained an iteration count of 2 for all three tested mesh sizes.

The approximate preconditioner also reduced the iteration counts, especially for larger systems.

During my timing experiments, I learned that fewer iterations do not always mean lower total computation time because building and applying preconditioners also requires computational effort.

---


## Notebook 4: Artificial Compressibility

**[Open Notebook 4](04-artificial-compressibility.ipynb)**

In my fourth notebook, I studied the artificial compressibility approach for the mixed Darcy saddle-point system.

I started with a small matrix example to understand how the artificial compressibility parameter changes the system.

I then implemented an iterative correction method using the modified saddle-point matrix to solve the original Darcy system.

### Work Completed

- Studied the artificial compressibility approach.
- Implemented the modified saddle-point matrix.
- Tested iterative corrections against a direct solution.
- Investigated different artificial compressibility parameters.
- Plotted residual convergence histories.
- Tested three different mesh sizes.
- Measured setup, solve, and total computation times.
- Plotted and analyzed the numerical results.

### Numerical Results

I tested four parameter values on three mesh sizes.

The iteration counts were:

| Alpha | 4 × 4 | 8 × 8 | 16 × 16 |
|---|---:|---:|---:|
| 0.01 | 6 | 9 | 15 |
| 0.10 | 12 | 25 | 71 |
| 0.50 | 29 | 86 | 310 |
| 1.00 | 48 | 160 | 609 |

All 12 configurations reached my actual relative residual target of 10⁻¹⁰.

I observed that smaller alpha values required fewer iterations for all three tested meshes.

The number of iterations increased with mesh refinement for each fixed alpha value.

### Computation Time

I repeated each timing configuration five times.

In my final saved timing results, alpha = 0.01 had the lowest measured total computation time on all three meshes.

For the largest mesh with 1312 unknowns:

- Alpha = 0.01 required 15 iterations and approximately 5.10 ms.
- Alpha = 1.0 required 609 iterations and approximately 86.72 ms.

These results are based on my current sparse LU implementation. Matrix assembly time was excluded.

This notebook helped me understand how the artificial compressibility parameter affects convergence and computational cost.

---

## Notebook 5: Final Numerical Comparison

**[Open Notebook 5](05-final-numerical-comparison.ipynb)**

In my fifth notebook, I completed a numerical comparison of the iterative solvers and preconditioning approaches studied in my previous notebooks.

I used the same two-dimensional mixed Darcy saddle-point system with RT0–P0 finite elements.

My goal was to compare iteration counts, convergence behavior, and computational costs under a common actual relative residual target of 10⁻⁸.

### Methods Compared

- Direct sparse LU solver.
- MINRES and GMRES without preconditioning.
- Exact block diagonal Schur complement preconditioning.
- Exact block triangular Schur complement preconditioning with GMRES.
- Approximate block diagonal Schur complement preconditioning.
- Artificial compressibility with four parameter values.

### Work Completed

- Assembled the Darcy system for three mesh sizes.
- Computed direct reference solutions.
- Compared MINRES and GMRES convergence.
- Tested exact and approximate Schur complement preconditioners.
- Compared artificial compressibility parameters.
- Created combined iteration comparison tables and graphs.
- Measured setup, solve, and total computation times.
- Analyzed the numerical results and limitations.

### Numerical Results

I compared 11 iterative configurations across three mesh sizes, giving 33 iterative configurations.

All 33 configurations satisfied my common actual relative residual target of 10⁻⁸.

The exact Schur complement preconditioners reduced the Krylov iteration counts to 2 for every tested mesh.

For artificial compressibility, alpha = 0.01 required the fewest correction iterations among the tested parameter values.

### Computation Time

I measured 12 solver configurations across three mesh sizes, with five timing repetitions per configuration.

All 180 timed runs satisfied the residual target.

For the largest mesh with 1312 unknowns:

| Method | Average Total Time |
|---|---:|
| Direct sparse LU | 4.57 ms |
| MINRES without preconditioning | 17.84 ms |
| GMRES without preconditioning | 216.79 ms |
| MINRES + Exact diagonal | 213.60 ms |
| Artificial compressibility, alpha = 0.01 | 11.29 ms |

I observed that fewer iterations did not always result in lower total computation time.

The direct sparse LU solver had the lowest measured total time on all three tested meshes, although its time was almost identical to that of preconditioned MINRES on the smallest mesh.

These results are specific to my implementations and tested problem sizes. Matrix assembly time was excluded, and the methods used different factorization techniques.

This final notebook helped me understand why both convergence and computational cost are important when comparing numerical methods.

---

## Current Limitations

- The study is limited to a two-dimensional Darcy flow problem.
- I used constant permeability and RT0–P0 finite elements.
- The largest tested system contains 1312 degrees of freedom.
- I used dense Cholesky factorization for the Schur complement preconditioners and sparse LU factorization for the artificial compressibility method.
- Computation times depend on the implementation and computational environment.

My current results are specific to the tested problem and solver settings.

---

## Next Steps

- [x] Implement the mixed Darcy formulation.
- [x] Study MINRES and GMRES.
- [x] Implement Schur complement preconditioners.
- [x] Study and implement artificial compressibility.
- [x] Compare the different preconditioning approaches.
- [x] Complete the final numerical analysis.

---

## Project Status
![Status](https://img.shields.io/badge/Status-Completed-2E8B57?style=for-the-badge)

I have completed the five planned notebooks in this numerical study, including the final comparison of iterative solvers and preconditioning approaches.
The results, code, and numerical experiments are available in this repository. The conclusions are specific to the tested Darcy problem and implementations.
