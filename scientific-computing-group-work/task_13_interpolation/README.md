# Task 13: Interpolation

## Mathematical concept

Interpolation estimates values between known data points. Linear interpolation joins neighbouring points with straight lines, while a cubic spline uses smooth cubic curves between the measurements.

## Input values / parameters

- Hourly times from 08:00 to 14:00.
- Temperature measurements [18.0, 20.0, 22.5, 24.0, 25.0, 25.5, 25.0]°C.
- Target time = 10:30.
- Estimates requested every 10 minutes.

## Mathematical operation

Build linear and cubic interpolation functions and evaluate them at intermediate times.

## Parameter change and effect

If the temperature at 11:00 is changed, the interpolation values around 11:00 also change because the surrounding data points define the interpolated curve.

## Output and interpretation

The output estimates the temperature at times where there was no direct measurement. The graph shows measured points and the two interpolation curves, making the difference between straight-line and smooth interpolation visible.

## Graph interpretation

The measured temperatures appear as points. The linear curve connects them with straight segments, while the cubic spline produces a smoother curve through the same data.

## Python implementation

Source code: [`task_13.py`](task_13.py)

```python
import numpy as np
from scipy.interpolate import interp1d, CubicSpline
import matplotlib.pyplot as plt

hours = np.array([8, 9, 10, 11, 12, 13, 14], dtype=float)
temperature = np.array(
    [18.0, 20.0, 22.5, 24.0, 25.0, 25.5, 25.0]
)

linear = interp1d(hours, temperature, kind="linear")
cubic = CubicSpline(hours, temperature)

ten_minute_times = np.arange(8, 14 + 1/6, 1/6)
linear_estimates = linear(ten_minute_times)
cubic_estimates = cubic(ten_minute_times)

target_time = 10.5
print(f"Linear estimate at 10:30: {float(linear(target_time)):.2f} C")
print(f"Cubic estimate at 10:30: {float(cubic(target_time)):.2f} C")

plt.scatter(hours, temperature, label="Hourly measurements")
plt.plot(ten_minute_times, linear_estimates, label="Linear")
plt.plot(ten_minute_times, cubic_estimates, label="Cubic spline")
plt.xlabel("Hour of day")
plt.ylabel("Temperature (C)")
plt.title("Temperature interpolation")
plt.legend()
plt.grid(True)
plt.show()
```

Run it with:

```bash
python task_13.py
```
