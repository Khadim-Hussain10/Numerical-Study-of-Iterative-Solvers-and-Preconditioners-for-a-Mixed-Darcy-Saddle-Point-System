# Numerical Study of Iterative Solvers and Preconditioners for a Mixed Darcy Saddle-Point System

## About This Project

I started this project to improve my understanding of saddle-point problems, mixed finite element methods, and iterative solvers using Python.

I am using a 2D Darcy flow problem as a starting point. My goal is to understand the mixed formulation, solve the numerical system, and study how different iterative solvers perform.

I have started with MINRES and GMRES. Later, I plan to study preconditioning methods based on Schur complements and artificial compressibility.

This project is related to my broader research interest in iterative preconditioners for saddle-point problems.

## Current Progress

So far, I have completed two notebooks.

### Notebook 1: Mixed Darcy Formulation

**[01_mixed_darcy_formulation.ipynb](01_mixed_darcy_formulation.ipynb)**

In my first notebook, I implemented a 2D mixed Darcy problem using RT0 elements for flux and P0 elements for pressure.

I assembled the saddle-point matrix and solved the system using SciPy's direct solver.

I compared the numerical pressure and flux with the exact solution. I also tested different mesh sizes and checked discrete local mass conservation.

The pressure and flux errors decreased when I refined the mesh.

These tests gave me a starting point for working with iterative solvers.

### Notebook 2: MINRES and GMRES

**[02-minres-gmres-solvers.ipynb](02-minres-gmres-solvers.ipynb)**

In my second notebook, I studied MINRES and GMRES and used them to solve the same mixed Darcy system without preconditioners.

I compared their solutions with the direct solver and checked the residuals and iteration counts.

I also tested three mesh sizes, plotted the residual convergence history, and measured the computation times.

During the experiments, I noticed that MINRES could report successful completion even when my calculated relative residual was above the target. I tested different tolerances to investigate this.

For the 16 × 16 mesh with 1312 unknowns:

- MINRES took 173 iterations and gave a relative residual of approximately 5.09 × 10⁻¹⁰.
- GMRES took 363 iterations and gave a relative residual of approximately 9.93 × 10⁻⁹.
- Both solvers reached my actual relative residual target of 10⁻⁸.

In my timing experiment, the direct solver was the fastest, followed by MINRES and GMRES.

These results are for the current problem and solver settings. I cannot use them to make general conclusions about solver performance.

I will use these results as a baseline when I start testing preconditioners.

## Next Steps

My next goal is to learn about Schur complement preconditioners and test suitable block preconditioning methods for the mixed Darcy system.

I also plan to study the artificial compressibility approach.

I want to compare the preconditioned solvers with the unpreconditioned MINRES and GMRES results.

## Tools

Python, NumPy, SciPy, Matplotlib, scikit-fem, Google Colab, and Kaggle Notebooks.

## Project Status

**In Progress**

The mixed Darcy implementation and the initial MINRES and GMRES experiments are complete.

The preconditioning part of the project has not been implemented yet.

I will continue updating this repository as I learn, implement, and check each part of the project.
