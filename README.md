# Numerical Study of Iterative Solvers and Preconditioners for a Mixed Darcy Saddle-Point System

## About This Project

I started this project to improve my understanding of saddle-point problems, mixed finite element methods, and iterative solvers using Python.

I am using a 2D Darcy flow problem as a starting point. My goal is to understand the mixed formulation, implement the numerical system, and then study iterative solvers such as MINRES and GMRES.

I also plan to explore preconditioning approaches based on Schur complements and artificial compressibility.

This project is related to my broader research interest in iterative preconditioners for saddle-point problems.

## Current Progress

I have completed my first Google Colab notebook:

**[01_mixed_darcy_formulation.ipynb](01_mixed_darcy_formulation.ipynb)**

In this notebook, I have:

- Set up the Python environment and defined an exact solution for a 2D Darcy problem.
- Created a triangular mesh and used RT0 elements for flux and P0 elements for pressure.
- Assembled the mixed Darcy saddle-point matrix and right-hand-side vector.
- Solved the system using SciPy's direct solver.
- Compared the numerical pressure and flux with the exact solution.
- Studied how the pressure and flux errors change with mesh refinement.
- Checked discrete local mass conservation.

For the initial mesh with 32 triangles, the system had 56 flux unknowns and 32 pressure unknowns.

The direct solver gave a relative residual of approximately 7.44 × 10⁻¹⁶.

The pressure RMSE measured at triangle centers was approximately 0.02696, and the flux L² error was approximately 0.49982.

I also tested finer meshes with 128 and 512 triangles. Both errors decreased as the mesh was refined.

The discrete mass balance error was close to machine precision.

These results give me a starting point for testing iterative solvers and preconditioners. More numerical verification may be needed as the project develops.

## Next Steps

My next goal is to study and implement iterative solvers for the same mixed Darcy system.

I plan to start with MINRES and GMRES, compare them with the direct solver, and then investigate suitable preconditioners.

Later, I want to study Schur complement and artificial compressibility approaches.

## Tools

Python, NumPy, SciPy, Matplotlib, scikit-fem, and Google Colab.

## Project Status

**In Progress**

I will continue updating this repository as I learn, implement, and verify each part of the project.
