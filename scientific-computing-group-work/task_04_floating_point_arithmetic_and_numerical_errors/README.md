# Task 4: Floating-Point Arithmetic and Numerical Errors

## Mathematical concept

Floating-point numbers are stored with finite binary precision, so some decimal values are represented approximately. Absolute and relative error can be used to measure the difference between an exact or reference value and an approximation.

## Input values / parameters

- Calculated value: 0.1 + 0.2.
- Expected value: 0.3.
- True value √2 and approximation 1.414.
- Small x values: 10⁻⁴, 10⁻⁸ and 10⁻¹².

## Mathematical operation

Compare floating-point values directly and with np.isclose(). Calculate absolute error = |true − approximate| and relative error = absolute error / |true|. Also compare a direct expression with a numerically stable equivalent.

## Parameter change and effect

If the approximation of √2 is changed from 1.414 to 1.4142, the absolute and relative errors become smaller because the approximation is closer to the true value.

## Output and interpretation

The direct equality comparison can fail because of floating-point representation, while tolerance-based comparison is more appropriate for numerical work. The stable expression avoids loss of significant digits for very small x.

## Python implementation

Source code: [`task_04.py`](task_04.py)

```python
import numpy as np

calculated = 0.1 + 0.2
expected = 0.3

print("0.1 + 0.2 =", calculated)
print("Exact comparison:", calculated == expected)
print("Tolerance-based comparison:", np.isclose(calculated, expected))

true_value = np.sqrt(2)
approx_value = 1.414
absolute_error = abs(true_value - approx_value)
relative_error = absolute_error / abs(true_value)

print(f"Absolute error: {absolute_error:.8f}")
print(f"Relative error: {relative_error:.8%}")

for x in [1e-4, 1e-8, 1e-12]:
    direct = (np.sqrt(1 + x) - 1) / x
    stable = 1 / (np.sqrt(1 + x) + 1)
    print(f"x={x:.0e}: direct={direct:.12f}, stable={stable:.12f}")
```

Run it with:

```bash
python task_04.py
```
