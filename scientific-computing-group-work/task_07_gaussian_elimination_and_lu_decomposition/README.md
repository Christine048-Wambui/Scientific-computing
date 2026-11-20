# Task 7: Gaussian Elimination and LU Decomposition

## Mathematical concept

Gaussian elimination reduces a system to an upper-triangular form. LU decomposition factors a matrix into lower and upper triangular components, allowing the same coefficient matrix to be reused efficiently for different right-hand sides.

## Input values / parameters

- Coefficient matrix A = [[4,-1,0],[-1,4,-1],[0,-1,3]].
- Three measurement vectors.
- The same A is used for every measurement set.

## Mathematical operation

Factor A once with scipy.linalg.lu_factor(), then use lu_solve() for each measurement vector.

## Parameter change and effect

If one measurement vector is changed, only the corresponding solution changes. The LU factorization of A does not need to be repeated because the coefficient matrix is unchanged.

## Output and interpretation

The solution vectors represent the unknown quantities corresponding to each measurement set. A small residual norm indicates that the computed solution satisfies Ax = b.

## Python implementation

Source code: [`task_07.py`](task_07.py)

```python
import numpy as np
from scipy.linalg import lu_factor, lu_solve

A = np.array([
    [4.0, -1.0, 0.0],
    [-1.0, 4.0, -1.0],
    [0.0, -1.0, 3.0]
])

measurement_sets = [
    np.array([15.0, 10.0, 10.0]),
    np.array([16.0, 11.0, 9.0]),
    np.array([14.0, 12.0, 11.0])
]

lu, piv = lu_factor(A)

for i, b in enumerate(measurement_sets, start=1):
    x = lu_solve((lu, piv), b)
    residual = b - A @ x
    print(f"Measurement set {i}")
    print("Solution:", x)
    print("Residual norm:", np.linalg.norm(residual))

print("Direct solution for first set:",
      np.linalg.solve(A, measurement_sets[0]))
```

Run it with:

```bash
python task_07.py
```
