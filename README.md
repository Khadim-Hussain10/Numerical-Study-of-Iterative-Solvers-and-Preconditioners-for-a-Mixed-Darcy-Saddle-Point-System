# Numerical Study of Iterative Solvers and Preconditioners for a Mixed Darcy Saddle-Point System

## About This Project

I started this project to improve my understanding of saddle-point problems, mixed finite element methods, and iterative solvers using Python.

I am using a 2D Darcy flow problem as a starting point. My plan is to learn how the mixed formulation works, implement the numerical system, and then study iterative methods such as MINRES and GMRES, along with Schur complement and artificial compressibility approaches.

This project is related to my broader research interest in iterative preconditioners for saddle-point problems.

## Current Progress

I am working on the mixed Darcy formulation in Google Colab.

So far, I have:

- Set up the Python environment.
- Defined and checked an exact pressure solution.
- Calculated the exact flux and source term.
- Created a 2D triangular mesh.
- Defined RT0 elements for flux and P0 elements for pressure.
- Assembled the saddle-point matrix and checked its dimensions and symmetry.

The right-hand side, numerical solution, and iterative preconditioners have not been implemented yet.

## Tools

Python, NumPy, SciPy, Matplotlib, scikit-fem, and Google Colab.

## Project Status

**In Progress**

I will update this repository as I continue learning, implementing, and checking each part of the project.
