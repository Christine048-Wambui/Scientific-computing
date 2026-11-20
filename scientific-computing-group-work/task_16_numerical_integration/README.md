# Task 16: Numerical Integration

## Mathematical concept

Numerical integration estimates an accumulated quantity or area. The trapezoidal rule uses trapezoids, while Simpson's rule uses parabolic approximations and can be more accurate for smooth data.

## Input values / parameters

- Time = [0, 2, 4, 6, 8, 10, 12] hours.
- Power = [0.8, 1.0, 1.4, 1.8, 1.6, 1.2, 0.9] kW.

## Mathematical operation

Integrate power with respect to time using the trapezoidal rule and Simpson's rule to estimate energy consumption.

## Parameter change and effect

If the power at one time is increased, the area under the power-time curve increases, so the estimated energy consumption also increases.

## Output and interpretation

The result is measured in kWh because power in kW is integrated over time in hours. The difference between the two estimates shows the effect of the numerical integration method.

## Python implementation

Source code: [`task_16.py`](task_16.py)

```python
import numpy as np
from scipy.integrate import simpson

time_hours = np.array([0, 2, 4, 6, 8, 10, 12], dtype=float)
power_kw = np.array([0.8, 1.0, 1.4, 1.8, 1.6, 1.2, 0.9])

energy_trapezoid = np.trapezoid(power_kw, time_hours)
energy_simpson = simpson(power_kw, x=time_hours)

print(f"Energy using trapezoidal rule: {energy_trapezoid:.3f} kWh")
print(f"Energy using Simpson's rule:   {energy_simpson:.3f} kWh")
print(f"Difference between estimates: "
      f"{abs(energy_simpson-energy_trapezoid):.3f} kWh")
```

Run it with:

```bash
python task_16.py
```
