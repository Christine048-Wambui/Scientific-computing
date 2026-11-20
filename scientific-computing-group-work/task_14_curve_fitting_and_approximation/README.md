# Task 14: Curve Fitting and Approximation

## Mathematical concept

Curve fitting chooses model parameters so that a mathematical function follows observed data as closely as possible. Least-squares fitting minimizes the sum of squared residuals.

## Input values / parameters

- Concurrent users = [50, 100, 150, 200, 250, 300, 350].
- Measured response times = [82, 95, 115, 145, 185, 238, 305] ms.
- Quadratic model y = ax² + bx + c.
- Prediction required at 400 users.

## Mathematical operation

Use scipy.optimize.curve_fit() to estimate a, b and c, calculate RMSE, and use the fitted model to predict response time.

## Parameter change and effect

If the response time for a particular load is increased, the fitted coefficients change to reflect the new observations, and the prediction at 400 users can also change.

## Output and interpretation

The fitted curve summarizes the relationship between user load and response time. RMSE measures average fitting error; a smaller RMSE means the fitted curve is closer to the measured values.

## Graph interpretation

The fitted curve should follow the upward trend of response time as the number of concurrent users increases.

## Python implementation

Source code: [`task_14.py`](task_14.py)

```python
import numpy as np
from scipy.optimize import curve_fit
import matplotlib.pyplot as plt

users = np.array([50, 100, 150, 200, 250, 300, 350], dtype=float)
response_ms = np.array([82, 95, 115, 145, 185, 238, 305], dtype=float)

def model(x, a, b, c):
    return a*x**2 + b*x + c

parameters, covariance = curve_fit(model, users, response_ms)
a, b, c = parameters
predicted = model(users, a, b, c)
rmse = np.sqrt(np.mean((response_ms - predicted)**2))

print(f"Fitted model: y = {a:.6f}x^2 + {b:.4f}x + {c:.2f}")
print(f"RMSE: {rmse:.2f} ms")
print(f"Predicted response at 400 users: {model(400, a, b, c):.2f} ms")

x_plot = np.linspace(users.min(), 400, 300)
plt.scatter(users, response_ms, label="Measurements")
plt.plot(x_plot, model(x_plot, a, b, c), label="Fitted curve")
plt.xlabel("Concurrent users")
plt.ylabel("Response time (ms)")
plt.title("Server response-time curve fitting")
plt.legend()
plt.grid(True)
plt.show()
```

Run it with:

```bash
python task_14.py
```
