# Task 18: Numerical Solution of ODEs Using SciPy

## Mathematical concept

SciPy's solve_ivp provides a higher-level numerical ODE solver and can automatically use suitable step sizes while returning the solution at requested times.

## Input values / parameters

- Supply voltage Vs = 5 V.
- Resistance R = 1000 ohms.
- Capacitance C = 0.001 F.
- Initial capacitor voltage V0 = 0 V.
- Simulation interval = 0 to 5 seconds.

## Mathematical operation

Solve dV/dt = (Vs−V)/(RC) using solve_ivp and compare the numerical result with the exact RC charging formula.

## Parameter change and effect

If the resistance is increased, the time constant RC increases, so the capacitor charges more slowly and the voltage at 5 seconds can be lower.

## Output and interpretation

The output gives the capacitor voltage at 5 seconds and the maximum difference from the exact solution. A very small error shows that the numerical solution closely matches the analytical curve.

## Graph interpretation

The voltage rises quickly at first and then approaches the supply voltage of 5 V. The numerical and exact curves should almost overlap.

## Python implementation

Source code: [`task_18.py`](task_18.py)

```python
import numpy as np
from scipy.integrate import solve_ivp
import matplotlib.pyplot as plt

Vs = 5.0
R = 1000.0
C = 0.001
V0 = 0.0

def rc_circuit(t, V):
    return [(Vs - V[0]) / (R * C)]

t_eval = np.linspace(0, 5, 200)

solution = solve_ivp(
    rc_circuit, (0, 5), [V0],
    t_eval=t_eval, rtol=1e-9, atol=1e-11
)

exact = Vs * (1 - np.exp(-solution.t / (R * C)))

print("Solver success:", solution.success)
print(f"Capacitor voltage at 5 s: {solution.y[0, -1]:.4f} V")
print(f"Maximum error against exact solution: "
      f"{np.max(np.abs(solution.y[0]-exact)):.3e} V")

plt.plot(solution.t, solution.y[0], label="solve_ivp")
plt.plot(solution.t, exact, linestyle="--", label="Exact")
plt.xlabel("Time (s)")
plt.ylabel("Capacitor voltage (V)")
plt.title("RC circuit charging")
plt.legend()
plt.grid(True)
plt.show()
```

Run it with:

```bash
python task_18.py
```
