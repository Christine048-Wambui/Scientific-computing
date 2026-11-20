# Task 17: Ordinary Differential Equations – Euler Method

## Mathematical concept

An ordinary differential equation describes how a quantity changes over time. Euler's method advances the solution using yₙ₊₁ = yₙ + h f(tₙ,yₙ). A smaller step size normally improves accuracy but increases computation.

## Input values / parameters

- Ambient temperature = 25°C.
- Initial temperature = 90°C.
- Cooling constant k = 0.12 per minute.
- Step size h = 1 minute.
- Simulation time = 30 minutes.

## Mathematical operation

The cooling model is dT/dt = −k(T−T_ambient). Euler's method is applied repeatedly to calculate the temperature.

## Parameter change and effect

If h is reduced from 1 minute to 0.5 minutes, the calculation uses more steps and should generally produce a closer approximation to the exact solution.

## Output and interpretation

The output gives the predicted temperature after 30 minutes and the final absolute error. The graph compares Euler's numerical curve with the exact cooling solution.

## Graph interpretation

Both curves should move toward the ambient temperature. The numerical Euler curve is an approximation of the exact exponential cooling curve.

## Python implementation

Source code: [`task_17.py`](task_17.py)

```python
import numpy as np
import matplotlib.pyplot as plt

T_ambient = 25.0
T_initial = 90.0
k = 0.12
h = 1.0
end_time = 30.0

def cooling_rate(T):
    return -k * (T - T_ambient)

time = np.arange(0, end_time + h, h)
temperature = np.zeros_like(time)
temperature[0] = T_initial

for i in range(len(time) - 1):
    temperature[i + 1] = (
        temperature[i] + h * cooling_rate(temperature[i])
    )

exact = T_ambient + (T_initial - T_ambient) * np.exp(-k * time)

print(f"Euler temperature after 30 min: {temperature[-1]:.2f} C")
print(f"Exact temperature after 30 min: {exact[-1]:.2f} C")
print(f"Final absolute error: "
      f"{abs(temperature[-1]-exact[-1]):.4f} C")

plt.plot(time, temperature, marker="o", label="Euler")
plt.plot(time, exact, label="Exact solution")
plt.xlabel("Time (minutes)")
plt.ylabel("Temperature (C)")
plt.title("Cooling of a hot object")
plt.legend()
plt.grid(True)
plt.show()
```

Run it with:

```bash
python task_17.py
```
