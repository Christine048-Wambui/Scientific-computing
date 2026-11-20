# Task 15: Numerical Differentiation

## Mathematical concept

A derivative measures a rate of change. Numerical differentiation estimates the derivative from nearby data points. Central differences are generally more accurate than one-sided differences for interior points.

## Input values / parameters

- Time samples = 0 to 6 seconds.
- Position measurements in metres = [0.0, 4.8, 10.2, 16.1, 22.7, 30.0, 38.0].

## Mathematical operation

Use a forward difference at the first point, central differences at interior points, and a backward difference at the final point.

## Parameter change and effect

If the sampling interval is reduced and additional position measurements are available, the derivative can be estimated at more closely spaced times. Changing a position reading directly changes the estimated speed around that point.

## Output and interpretation

The output is estimated vehicle speed in metres per second. The graph shows how speed changes with time based on the GPS position measurements.

## Graph interpretation

The speed curve indicates the estimated rate of movement at each sampled time. An upward trend means the position is changing more rapidly.

## Python implementation

Source code: [`task_15.py`](task_15.py)

```python
import numpy as np
import matplotlib.pyplot as plt

time = np.array([0, 1, 2, 3, 4, 5, 6], dtype=float)
position = np.array([0.0, 4.8, 10.2, 16.1, 22.7, 30.0, 38.0])

speed = np.zeros_like(position)
speed[0] = (position[1] - position[0]) / (time[1] - time[0])

for i in range(1, len(time) - 1):
    speed[i] = (
        position[i + 1] - position[i - 1]
    ) / (time[i + 1] - time[i - 1])

speed[-1] = (
    position[-1] - position[-2]
) / (time[-1] - time[-2])

for t, x, v in zip(time, position, speed):
    print(f"t={t:.0f}s, position={x:.1f}m, estimated speed={v:.2f}m/s")

plt.plot(time, speed, marker="o")
plt.xlabel("Time (s)")
plt.ylabel("Estimated speed (m/s)")
plt.title("Speed estimated from GPS position data")
plt.grid(True)
plt.show()
```

Run it with:

```bash
python task_15.py
```
