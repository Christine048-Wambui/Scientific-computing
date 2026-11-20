# Task 10: Root Finding – Bisection and Fixed-Point Methods

## Mathematical concept

A root is a value r for which f(r)=0. Bisection repeatedly halves a bracket containing a sign change. Fixed-point iteration rewrites the equation as T=g(T) and repeatedly evaluates g.

## Input values / parameters

- Heat-balance function f(T) = T − 25 − 10e^(−T/20).
- Bisection interval [20, 40]°C.
- Fixed-point initial value T = 30°C.
- Stopping tolerance = 10⁻¹⁰.

## Mathematical operation

The bisection method searches for a sign-changing interval while fixed-point iteration repeatedly evaluates g(T)=25+10e^(−T/20).

## Parameter change and effect

If the initial fixed-point value is changed, the number of iterations can change even though the converged solution may remain the same. Changing the bracket also affects the bisection process, provided it still contains a root.

## Output and interpretation

The root is the equilibrium temperature where the heat-balance function equals zero. On the graph, the root is where the curve crosses the horizontal zero line.

## Graph interpretation

The curve crosses y=0 at the equilibrium temperature. The vertical marker identifies the numerical root.

## Python implementation

Source code: [`task_10.py`](task_10.py)

```python
import numpy as np
from scipy.optimize import root_scalar
import matplotlib.pyplot as plt

def heat_balance(T):
    return T - 25 - 10*np.exp(-T/20)

solution = root_scalar(
    heat_balance, bracket=[20, 40],
    method="bisect", xtol=1e-10
)

def g(T):
    return 25 + 10*np.exp(-T/20)

T = 30.0
history = [T]
for _ in range(100):
    T_new = g(T)
    history.append(T_new)
    if abs(T_new - T) < 1e-10:
        break
    T = T_new

print(f"Bisection equilibrium temperature: {solution.root:.6f} C")
print(f"Fixed-point equilibrium temperature: {history[-1]:.6f} C")
print("Fixed-point iterations:", len(history) - 1)

temps = np.linspace(20, 40, 300)
plt.plot(temps, heat_balance(temps))
plt.axhline(0, linewidth=0.8)
plt.axvline(solution.root, linestyle="--")
plt.xlabel("Temperature (C)")
plt.ylabel("Heat-balance function")
plt.title("Equilibrium temperature")
plt.grid(True)
plt.show()
```

Run it with:

```bash
python task_10.py
```
