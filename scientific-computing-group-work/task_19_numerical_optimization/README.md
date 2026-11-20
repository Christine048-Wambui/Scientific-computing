# Task 19: Numerical Optimization

## Mathematical concept

Optimization finds input values that minimize or maximize an objective function subject to any required constraints.

## Input values / parameters

- Type A cost = 12 per unit and capacity = 100.
- Type B cost = 18 per unit and capacity = 170.
- Required capacity = at least 1000.
- Non-negative bounds for both variables.

## Mathematical operation

Minimize cost = 12x + 18y subject to 100x + 170y ≥ 1000 and x,y ≥ 0 using scipy.optimize.minimize.

## Parameter change and effect

If the required capacity is increased, the optimizer must select a larger allocation, normally increasing the minimum cost. If unit costs change, the preferred allocation can also change.

## Output and interpretation

The solution gives the continuous allocation that minimizes operating cost while meeting the capacity requirement. The integer check gives a practical alternative when only whole servers are allowed.

## Python implementation

Source code: [`task_19.py`](task_19.py)

```python
import numpy as np
from scipy.optimize import minimize

def cost(z):
    x, y = z
    return 12*x + 18*y

def capacity_constraint(z):
    x, y = z
    return 100*x + 170*y - 1000

constraints = {
    "type": "ineq",
    "fun": capacity_constraint
}
bounds = [(0, None), (0, None)]

solution = minimize(
    cost, x0=[5, 3], method="SLSQP",
    bounds=bounds, constraints=constraints
)

x, y = solution.x
print("Optimization success:", solution.success)
print(f"Type A allocation: {x:.3f}")
print(f"Type B allocation: {y:.3f}")
print(f"Total capacity: {100*x + 170*y:.2f}")
print(f"Minimum planning cost: {solution.fun:.2f}")

best_integer = None
for a in range(0, 20):
    for b in range(0, 20):
        capacity = 100*a + 170*b
        if capacity >= 1000:
            total_cost = 12*a + 18*b
            if best_integer is None or total_cost < best_integer[0]:
                best_integer = (total_cost, a, b, capacity)

print("Best nearby integer solution:", best_integer)
```

Run it with:

```bash
python task_19.py
```
