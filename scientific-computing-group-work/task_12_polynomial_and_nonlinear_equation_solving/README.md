# Task 12: Polynomial and Nonlinear Equation Solving

## Mathematical concept

A nonlinear system contains equations that are not all linear in the unknowns. Numerical solvers search for values that make all residuals close to zero.

## Input values / parameters

- Circle: x² + y² = 4.
- Parabola: y = x² − 1.
- Initial guesses [1,1] and [-1,1].

## Mathematical operation

Define two residual equations and use scipy.optimize.root() from more than one initial guess to find the intersection points.

## Parameter change and effect

If a different initial guess is used, the solver may converge to a different intersection when multiple solutions exist. This demonstrates the importance of starting values in nonlinear solving.

## Output and interpretation

The returned x and y coordinates are the intersection points of the circle and parabola. Residuals close to zero indicate that both equations are satisfied.

## Python implementation

Source code: [`task_12.py`](task_12.py)

```python
import numpy as np
from scipy.optimize import root

def equations(z):
    x, y = z
    return [
        x**2 + y**2 - 4,
        y - (x**2 - 1)
    ]

for guess in ([1.0, 1.0], [-1.0, 1.0]):
    solution = root(equations, guess)
    print("Initial guess:", guess)
    print("Intersection:", solution.x)
    print("Residuals:", equations(solution.x))
    print("Converged:", solution.success)
    print()
```

Run it with:

```bash
python task_12.py
```
