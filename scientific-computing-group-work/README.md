# BIT 2118: Scientific Computing - Group Work Assignment

## Group members

1. Sumrall Hazo - BSCCS202443637
2. Ian Iregi - BSCCS252617842
3. Lorna Mugecha - BSCCS252617744
4. Claire Kinyanjui - BSCCS252618760
5. Beryl Tele - BSCCS252613992
6. Francis Kasalu - BSCCS252614095
7. Page Mawira - BSCCS/2025/60438
8. Christine Wambui - BSCCS252615757
9. Lucy Mwende - BSCCS262717862
10. Trina Viddy – BSCCS252607978

## Introduction

Scientific computing uses numerical methods and computer programs to solve mathematical problems that are difficult or repetitive to handle manually. In this work I used Python libraries such as NumPy, SciPy and Matplotlib to demonstrate numerical computation, linear algebra, root finding, interpolation, differential equations, optimization and Monte Carlo simulation.

The assignment instructions require all groups to complete all tasks, identify input values and mathematical operations, change at least one input or parameter and explain the effect, interpret outputs and graphs, and modify the program for a related real-world case. The GitHub submission is individual, even though discussion is done as group work.

## Software and libraries

- Python 3.x – programming language used for the numerical solutions.
- NumPy – arrays, vectorized calculations, matrix operations and linear algebra.
- SciPy – scientific algorithms including root finding, interpolation, integration, ODEs, curve fitting and optimization.
- Matplotlib – graphs used to interpret numerical behaviour, convergence and simulation results.
- timeit – timing comparison between ordinary Python loops and vectorized NumPy operations.

## Contents

Each task has its own folder with the Python code and a README that documents the mathematical concept, inputs, operation, parameter change and interpretation.

| Task | Topic | Folder |
|---|---|---|
| Task 2 | NumPy Arrays and Numerical Computation | [task_02_numpy_arrays_and_numerical_computation](task_02_numpy_arrays_and_numerical_computation/) |
| Task 3 | Mathematical Functions and Vectorization | [task_03_mathematical_functions_and_vectorization](task_03_mathematical_functions_and_vectorization/) |
| Task 4 | Floating-Point Arithmetic and Numerical Errors | [task_04_floating_point_arithmetic_and_numerical_errors](task_04_floating_point_arithmetic_and_numerical_errors/) |
| Task 5 | Matrix Algebra and Matrix Operations | [task_05_matrix_algebra_and_matrix_operations](task_05_matrix_algebra_and_matrix_operations/) |
| Task 6 | Solution of Systems of Linear Equations | [task_06_solution_of_systems_of_linear_equations](task_06_solution_of_systems_of_linear_equations/) |
| Task 7 | Gaussian Elimination and LU Decomposition | [task_07_gaussian_elimination_and_lu_decomposition](task_07_gaussian_elimination_and_lu_decomposition/) |
| Task 8 | Iterative Methods for Linear Systems | [task_08_iterative_methods_for_linear_systems](task_08_iterative_methods_for_linear_systems/) |
| Task 9 | Eigenvalues and Eigenvectors | [task_09_eigenvalues_and_eigenvectors](task_09_eigenvalues_and_eigenvectors/) |
| Task 10 | Root Finding – Bisection and Fixed-Point Methods | [task_10_root_finding_bisection_and_fixed_point_methods](task_10_root_finding_bisection_and_fixed_point_methods/) |
| Task 11 | Root Finding – Newton-Raphson and Secant Methods | [task_11_root_finding_newton_raphson_and_secant_methods](task_11_root_finding_newton_raphson_and_secant_methods/) |
| Task 12 | Polynomial and Nonlinear Equation Solving | [task_12_polynomial_and_nonlinear_equation_solving](task_12_polynomial_and_nonlinear_equation_solving/) |
| Task 13 | Interpolation | [task_13_interpolation](task_13_interpolation/) |
| Task 14 | Curve Fitting and Approximation | [task_14_curve_fitting_and_approximation](task_14_curve_fitting_and_approximation/) |
| Task 15 | Numerical Differentiation | [task_15_numerical_differentiation](task_15_numerical_differentiation/) |
| Task 16 | Numerical Integration | [task_16_numerical_integration](task_16_numerical_integration/) |
| Task 17 | Ordinary Differential Equations – Euler Method | [task_17_ordinary_differential_equations_euler_method](task_17_ordinary_differential_equations_euler_method/) |
| Task 18 | Numerical Solution of ODEs Using SciPy | [task_18_numerical_solution_of_odes_using_scipy](task_18_numerical_solution_of_odes_using_scipy/) |
| Task 19 | Numerical Optimization | [task_19_numerical_optimization](task_19_numerical_optimization/) |
| Task 20 | Random Numbers and Monte Carlo Methods | [task_20_random_numbers_and_monte_carlo_methods](task_20_random_numbers_and_monte_carlo_methods/) |
| Related case | Related Real-World Case: IT Support Response Times | [related_case_it_support_response_times](related_case_it_support_response_times/) |

## Running the code

```bash
pip install -r requirements.txt
python task_02_numpy_arrays_and_numerical_computation/task_02.py
```

## General observations

- NumPy is useful for storing and processing numerical data efficiently, especially when the same operation is repeated many times.
- Numerical methods are approximations, so error, tolerance and validation are important when interpreting results.
- SciPy provides ready-to-use numerical algorithms for problems such as roots, interpolation, integration, ODEs and optimization.
- Graphs make convergence, fitted relationships, interpolation and simulation behaviour easier to interpret.
- Changing an input parameter is useful for sensitivity analysis because it shows how the mathematical output responds to different conditions.

## Conclusion

This assignment demonstrates how mathematical concepts can be implemented as practical Python programs. The tasks cover arrays, vectorization, numerical errors, matrix algebra, linear systems, iterative methods, eigenvalues, root finding, nonlinear equations, interpolation, curve fitting, differentiation, integration, ODEs, optimization and Monte Carlo simulation. I also included a related IT support case to demonstrate how the same numerical techniques can be adapted to a different real-world situation.
