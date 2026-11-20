# Task 6: Solution of Systems of Linear Equations

## Mathematical concept

A system of linear equations can be written as Ax = b, where A contains coefficients, x contains unknowns and b contains known results.

## Input values / parameters

- Type A server uses 4 CPU units and 8 GB memory.
- Type B server uses 2 CPU units and 12 GB memory.
- Total observed usage = 20 CPU units and 72 GB memory.

## Mathematical operation

Solve the matrix equation Ax = b using np.linalg.solve(), then verify the result using A @ solution.

## Parameter change and effect

If total CPU usage is changed from 20 to 24 units while memory remains 72 GB, the solution for the number of server types changes because the right-hand side vector b has changed.

## Output and interpretation

The solution gives the quantities of the two server types that satisfy both resource equations. The residual and its norm should be close to zero, showing that the solution satisfies the original equations.

## Python implementation

Source code: [`task_06.py`](task_06.py)

```python
import numpy as np

A = np.array([
    [4.0, 2.0],
    [8.0, 12.0]
])
b = np.array([20.0, 72.0])

solution = np.linalg.solve(A, b)
residual = b - A @ solution

print(f"Type A servers: {solution[0]:.0f}")
print(f"Type B servers: {solution[1]:.0f}")
print("Verification A @ solution:", A @ solution)
print("Residual:", residual)
print("Residual norm:", np.linalg.norm(residual))
```

Run it with:

```bash
python task_06.py
```
